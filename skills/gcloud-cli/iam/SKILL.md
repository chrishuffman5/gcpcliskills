---
name: gcloud-iam
description: >-
  Identity and Access Management via gcloud (`gcloud iam`). Manage IAM service accounts and keys — oauth-clients, policies, policy-bindings, principal-access-boundary-policies, roles, service-accounts, simulator, workforce-pools.
---

# gcloud iam — Identity and Access Management

## Overview

`gcloud iam` manages the building blocks of Google Cloud access control: **service accounts** (and their keys), **custom roles**, and **identity federation** (workload and workforce pools/providers). Reach for it when you need to create the identities and role definitions that get granted access — not to grant access on a specific resource.

> **Where IAM bindings live.** Granting a principal a role *on a resource* (a project, bucket, etc.) is done on that resource's own command group — e.g. `gcloud projects add-iam-policy-binding`, `gcloud storage buckets add-iam-policy-binding`. `gcloud iam` only manages bindings on IAM's *own* resources (a service account, a workload identity pool), plus the service accounts, custom roles, and federation pools themselves.

## Quick reference — common workflows

### Enable the APIs
```bash
gcloud services enable iam.googleapis.com
# Workload Identity Federation also needs the Security Token Service API:
gcloud services enable sts.googleapis.com
```
Enabling `iam.googleapis.com` also enables the IAM Service Account Credentials API automatically.

### 1. Create and manage a service account
```bash
# Create
gcloud iam service-accounts create my-app-sa \
    --display-name="My Application SA" \
    --description="Runs the my-app workload"

# Describe / list
gcloud iam service-accounts describe my-app-sa@PROJECT_ID.iam.gserviceaccount.com
gcloud iam service-accounts list

# Update, then disable / re-enable
gcloud iam service-accounts update my-app-sa@PROJECT_ID.iam.gserviceaccount.com \
    --display-name="My App SA (updated)"
gcloud iam service-accounts disable my-app-sa@PROJECT_ID.iam.gserviceaccount.com
gcloud iam service-accounts enable  my-app-sa@PROJECT_ID.iam.gserviceaccount.com

# Let a user impersonate/attach the SA (binding ON the SA resource)
gcloud iam service-accounts add-iam-policy-binding \
    my-app-sa@PROJECT_ID.iam.gserviceaccount.com \
    --member="user:alice@example.com" \
    --role="roles/iam.serviceAccountUser"
```

### 2. Manage service account keys
```bash
# Create a JSON key (download a private key — use sparingly)
gcloud iam service-accounts keys create key.json \
    --iam-account=my-app-sa@PROJECT_ID.iam.gserviceaccount.com

# List user-managed keys (key rotation)
gcloud iam service-accounts keys list \
    --iam-account=my-app-sa@PROJECT_ID.iam.gserviceaccount.com \
    --managed-by=user

# Disable before deleting (recommended), then delete
gcloud iam service-accounts keys disable KEY_ID \
    --iam-account=my-app-sa@PROJECT_ID.iam.gserviceaccount.com
gcloud iam service-accounts keys delete KEY_ID \
    --iam-account=my-app-sa@PROJECT_ID.iam.gserviceaccount.com
```
> Prefer Workload Identity Federation over long-lived keys for external workloads.

### 3. Create and update a custom role
```bash
# Discover permissions you can include for a resource
gcloud iam list-testable-permissions \
    //cloudresourcemanager.googleapis.com/projects/PROJECT_ID

# Create from flags
gcloud iam roles create MyCustomRole --project=PROJECT_ID \
    --title="My Custom Role" \
    --description="Read-only access to Pub/Sub topics" \
    --permissions=pubsub.topics.get,pubsub.topics.list \
    --stage=GA

# ...or from a YAML file
gcloud iam roles create MyCustomRole --project=PROJECT_ID --file=role.yaml

# Add/remove permissions later; copy a predefined role as a starting point
gcloud iam roles update MyCustomRole --project=PROJECT_ID \
    --add-permissions=pubsub.subscriptions.get \
    --remove-permissions=pubsub.topics.list
gcloud iam roles copy --source="roles/storage.objectViewer" \
    --destination=MyStorageViewer --dest-project=PROJECT_ID
```

### 4. Set up Workload Identity Federation (OIDC, e.g. GitHub Actions)
```bash
# Create a pool, then an OIDC provider
gcloud iam workload-identity-pools create my-wif-pool \
    --location="global" --display-name="My WIF Pool"

gcloud iam workload-identity-pools providers create-oidc my-github-provider \
    --location="global" \
    --workload-identity-pool=my-wif-pool \
    --issuer-uri="https://token.actions.githubusercontent.com" \
    --attribute-mapping="google.subject=assertion.sub,attribute.repository=assertion.repository"

# Let an external identity impersonate a service account (binding ON the SA)
gcloud iam service-accounts add-iam-policy-binding \
    my-app-sa@PROJECT_ID.iam.gserviceaccount.com \
    --member="principalSet://iam.googleapis.com/projects/PROJECT_NUMBER/locations/global/workloadIdentityPools/my-wif-pool/attribute.repository/my-org/my-repo" \
    --role="roles/iam.workloadIdentityUser"

# Generate a credential config file for the external workload
gcloud iam workload-identity-pools create-cred-config \
    projects/PROJECT_NUMBER/locations/global/workloadIdentityPools/my-wif-pool/providers/my-github-provider \
    --service-account=my-app-sa@PROJECT_ID.iam.gserviceaccount.com \
    --credential-source-file=/path/to/oidc/token \
    --output-file=credentials.json
```

### 5. Discover roles & permissions for a resource
```bash
gcloud iam list-grantable-roles //cloudresourcemanager.googleapis.com/projects/PROJECT_ID
gcloud iam roles list                       # all predefined roles
gcloud iam roles list --project=PROJECT_ID  # this project's custom roles
gcloud iam roles describe roles/storage.objectViewer
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `iam service-accounts` | [`service-accounts.md`](service-accounts.md) | 20 | Create/manage service accounts, their keys, and per-SA IAM bindings |
| `iam roles` | [`roles.md`](roles.md) | 7 | Create, copy, update, delete/undelete custom roles; describe/list roles |
| `iam workload-identity-pools` | [`workload-identity-pools.md`](workload-identity-pools.md) | 49 | Workload identity pools, providers, and credential-config files |
| `iam workforce-pools` | [`workforce-pools.md`](workforce-pools.md) | 41 | Workforce pools and providers for human SSO via an external IdP |
| `iam policies` | [`policies.md`](policies.md) | 5 | IAM deny policies |
| `iam policy-bindings` | [`policy-bindings.md`](policy-bindings.md) | 6 | Principal access boundary policy bindings |
| `iam principal-access-boundary-policies` | [`principal-access-boundary-policies.md`](principal-access-boundary-policies.md) | 6 | Principal access boundary (PAB) policies |
| `iam oauth-clients` | [`oauth-clients.md`](oauth-clients.md) | 11 | Manage OAuth clients |
| `iam simulator` | [`simulator.md`](simulator.md) | 1 | Replay recent access to preview the impact of a policy change |
| `iam` (top-level) | [`_commands.md`](_commands.md) | 2 | `list-grantable-roles`, `list-testable-permissions` |

See [`index.md`](index.md) for a one-line index of all 148 GA commands.

## Common flags & tips

- **Service account naming.** A SA's email is `NAME@PROJECT_ID.iam.gserviceaccount.com`. `create` takes the short `NAME`; nearly every other command takes the full email (or 21-digit numeric ID).
- **`--iam-account` vs. positional SA.** Key commands (`keys create/list/delete/disable/enable/upload`, `sign-blob`, `sign-jwt`) require `--iam-account=EMAIL`. Account-level commands (`describe`, `update`, `disable`, bindings) take the SA email as a positional arg.
- **`undelete` needs the numeric ID.** `gcloud iam service-accounts undelete` takes the 21-digit unique ID, not the email.
- **Custom role scope.** `roles create/update/delete/undelete` require exactly one of `--project=PROJECT_ID` or `--organization=ORG_ID`. Use `--stage` (e.g. `GA`, `BETA`, `DISABLED`) and `--add-permissions`/`--remove-permissions` on `update`.
- **Federation requires `--location`.** All `workload-identity-pools` / `workforce-pools` commands take `--location` (typically `global`). List soft-deleted pools with `--show-deleted`; `delete` is a recoverable soft-delete (`undelete` restores it).
- **Resource references for discovery.** `list-grantable-roles` / `list-testable-permissions` take a full resource name (`//service.googleapis.com/...`) or URI; get a URI from most list commands with `--uri`.
- **Conditions.** `add-iam-policy-binding` on a SA or pool accepts `--condition=expression=...,title=...` (or `--condition-from-file`). Use `--condition=None` for an unconditional binding.
- **Useful format/filter examples:**
  ```bash
  gcloud iam service-accounts list --filter="disabled=false" --format="table(email,displayName)"
  gcloud iam roles list --filter="title:Storage" --format="value(name)"
  gcloud iam service-accounts keys list --iam-account=SA_EMAIL \
      --managed-by=user --created-before=2024-01-01T00:00:00Z
  ```

## Official documentation

- [IAM documentation home](https://cloud.google.com/iam/docs) — product overview, concepts, and how-to guides.
- [Service account overview](https://cloud.google.com/iam/docs/service-account-overview) — how SAs work as both principals and resources.
- [Create & manage service accounts](https://cloud.google.com/iam/docs/creating-managing-service-accounts) — gcloud how-to for the SA lifecycle.
- [Create & delete service account keys](https://cloud.google.com/iam/docs/keys-create-delete) — key creation, rotation, and best practices.
- [Create & manage custom roles](https://cloud.google.com/iam/docs/creating-custom-roles) — authoring custom roles at project/org scope.
- [Workload Identity Federation](https://cloud.google.com/iam/docs/workload-identity-federation) — keyless auth for AWS, Azure, GitHub, and other OIDC/SAML workloads.
- [Manage WIF pools & providers](https://cloud.google.com/iam/docs/manage-workload-identity-pools-providers) — gcloud how-to for pools and providers.
- [Workforce Identity Federation](https://cloud.google.com/iam/docs/workforce-identity-federation) — SSO for employees/partners via an external IdP.
- [gcloud iam reference](https://cloud.google.com/sdk/gcloud/reference/iam) — full command reference for all subgroups.
</content>
</invoke>

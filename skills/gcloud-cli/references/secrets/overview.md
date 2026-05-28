# gcloud secrets — Secret Manager

## Overview
`gcloud secrets` manages Google Cloud **Secret Manager** — a fully managed service for storing API keys, passwords, certificates, and other sensitive data. A *secret* is a versioned container; the actual payload lives in a *secret version*, so rotating a value means adding a new version rather than overwriting. Replication can be **automatic** (Google-managed) or **user-managed** (an explicit region list), access is controlled with Cloud IAM per secret, and every access is recorded in Cloud Audit Logs. Reach for it whenever an application or pipeline needs to fetch a credential at runtime instead of baking it into code or config.

## Quick reference — common workflows

### 1. Enable the API
```bash
gcloud services enable secretmanager.googleapis.com
```

### 2. Create a secret and store its first value
```bash
# Create the secret container only (no version yet)
gcloud secrets create my-secret

# Create with an automatic replication policy and a value piped from stdin
printf "s3cr3t" | gcloud secrets create my-secret --data-file=-

# Create with user-managed replication pinned to specific regions
printf "s3cr3t" | gcloud secrets create my-secret --data-file=- \
    --replication-policy=user-managed \
    --locations=us-central1,us-east1
```

### 3. Access (read) a secret value
```bash
# Access the latest version ('latest' is a built-in alias)
gcloud secrets versions access latest --secret=my-secret

# Access a specific version number
gcloud secrets versions access 123 --secret=my-secret

# Write raw bytes to a file to avoid UTF-8 corruption of binary secrets
gcloud secrets versions access latest --secret=my-secret \
    --out-file=/tmp/secret
```

### 4. Rotate a secret (add a new version, retire the old one)
```bash
# Add a new version from stdin
printf "new-s3cr3t" | gcloud secrets versions add my-secret --data-file=-

# Add a new version from a file
gcloud secrets versions add my-secret --data-file=/tmp/secret

# List versions and their status, then disable / destroy an old one
gcloud secrets versions list my-secret
gcloud secrets versions disable 1 --secret=my-secret
gcloud secrets versions destroy 1 --secret=my-secret
```

### 5. Configure a rotation schedule (Pub/Sub notification)
```bash
# Set a next rotation time and period at creation
gcloud secrets create my-secret \
    --next-rotation-time="2030-01-01T15:30:00-05:00" \
    --rotation-period="7200s" \
    --topics=projects/MY_PROJECT/topics/MY_TOPIC

# Update the schedule on an existing secret
gcloud secrets update my-secret \
    --next-rotation-time="2030-01-01T15:30:00-05:00" \
    --rotation-period="7200s"

# Clear the rotation policy entirely
gcloud secrets update my-secret --remove-rotation-schedule
```

### 6. Manage IAM access per secret
```bash
# Grant the accessor role to a service account
gcloud secrets add-iam-policy-binding my-secret \
    --member='serviceAccount:sa@project.iam.gserviceaccount.com' \
    --role='roles/secretmanager.secretAccessor'

# View the current IAM policy
gcloud secrets get-iam-policy my-secret

# Remove a binding
gcloud secrets remove-iam-policy-binding my-secret \
    --member='user:test-user@gmail.com' \
    --role='roles/secretmanager.secretAccessor'
```

### 7. Inspect and tidy up secret metadata
```bash
gcloud secrets list                                   # all secret names
gcloud secrets describe my-secret                     # metadata (replication, labels, rotation)
gcloud secrets update my-secret --update-labels=env=prod
gcloud secrets update my-secret --version-destroy-ttl="86400s"   # delayed destroy
gcloud secrets delete my-secret                       # delete secret + all versions
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `secrets` (top level) | [`_commands.md`](_commands.md) | 9 | Create/delete/describe/list/update secrets and manage their IAM policy |
| `secrets locations` | [`locations.md`](locations.md) | 2 | Describe and list locations available for storing secrets |
| `secrets replication` | [`replication.md`](replication.md) | 3 | Get, set, and update a secret's replication and CMEK |
| `secrets versions` | [`versions.md`](versions.md) | 7 | Add, access, list, describe, enable, disable, destroy secret versions |

See [`index.md`](index.md) for the one-line index of all 21 commands.

## Common flags & tips
- **Writing secret data:** `--data-file=PATH` reads the payload from a file; use `--data-file=-` to read from stdin (e.g. `printf "s3cr3t" | gcloud secrets create ...`). Prefer `printf` over `echo` to avoid a trailing newline; on Windows PowerShell, `Write-Output` appends a newline to the secret.
- **Reading secret data:** `gcloud secrets versions access` prints to stdout as UTF-8, which can corrupt binary payloads — use `--out-file=PATH` for raw bytes. The version `latest` is a built-in alias; you can also reference numeric version IDs.
- **Replication:** `--replication-policy=automatic` (Google-managed) or `--replication-policy=user-managed` with `--locations=LOCATION,...`. Replication locations are fixed once the secret is created.
- **Rotation:** pair `--next-rotation-time` (RFC 3339 timestamp) with `--rotation-period` (a duration such as `604800s`) and one or more `--topics`. Run `gcloud topic datetimes` for accepted date/time and duration formats.
- **Optimistic concurrency:** `--etag=ETAG` on `delete`, `update`, and the version `destroy`/`disable`/`enable` commands applies the change only if the current ETag matches.
- **CMEK:** set a key at creation with `--kms-key-name` (automatic) or `--regional-kms-key-name` (regional secret), and manage it later with `gcloud secrets replication update --set-kms-key=... [--location=...]` or `--remove-cmek`.
- **Regional secrets:** add `--location=LOCATION` to most commands to target a regional secret instead of a global one.
- **Useful `--format` / `--filter`:**
  - Get just the version names: `gcloud secrets list --format='value(name)'`
  - Show only enabled versions: `gcloud secrets versions list my-secret --filter='state:ENABLED'`
  - Decode the raw payload: `gcloud secrets versions access latest --secret=my-secret --format='get(payload.data)' | tr '_-' '/+' | base64 -d`

## beta / alpha
`gcloud beta secrets` and `gcloud alpha secrets` exist but expose the same command surface as GA — no beta- or alpha-exclusive commands or flags were found as of the research date. Stay on GA unless a future preview feature requires the surface.

## Official documentation
- [Secret Manager documentation home](https://cloud.google.com/secret-manager/docs) — product overview, guides, and API reference.
- [Secret Manager overview](https://cloud.google.com/secret-manager/docs/overview) — core concepts: secrets, versions, replication, IAM.
- [Quickstart](https://cloud.google.com/secret-manager/docs/quickstart) — create a secret and access its value with gcloud.
- [Create and access secrets](https://cloud.google.com/secret-manager/docs/creating-and-accessing-secrets) — how-to for creating secrets and accessing versions.
- [Manage secrets](https://cloud.google.com/secret-manager/docs/managing-secrets) — list and describe secret metadata.
- [Access control with IAM](https://cloud.google.com/secret-manager/docs/access-control) — roles and least-privilege patterns.
- [Secret rotation](https://cloud.google.com/secret-manager/docs/secret-rotation) — configure automatic rotation via Pub/Sub notifications.
- [Customer-managed encryption keys (CMEK)](https://cloud.google.com/secret-manager/docs/cmek) — encrypt secrets with Cloud KMS keys.
- [gcloud secrets CLI reference](https://cloud.google.com/sdk/gcloud/reference/secrets) — full command and flag reference.

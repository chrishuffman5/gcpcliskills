---
name: gcloud-kms
description: >-
  Cloud Key Management Service via gcloud (`gcloud kms`). Manage cryptographic keys in the cloud — autokey-config, ekm-config, ekm-connections, import-jobs, inventory, key-handles, keyrings, keys.
---

# gcloud kms — Cloud Key Management Service

## Overview

`gcloud kms` manages Cloud KMS key rings, keys, versions, and encrypt/decrypt operations. Use it to create and organize cryptographic keys (symmetric, asymmetric, MAC, raw, key-encapsulation), perform cryptographic operations (encrypt/decrypt, sign/verify, get public keys), control rotation and destruction of key versions, and grant IAM access — while retaining customer custodianship of key material. Keys live in a location, are grouped into a key ring, and progress through numbered versions. Reach for it whenever you need customer-managed encryption keys (CMEK) for other Google Cloud services or application-level cryptography.

## Quick reference — common workflows

### 1. Enable the API and create a key ring + symmetric key

```bash
# Prerequisite: enable the Cloud KMS API
gcloud services enable cloudkms.googleapis.com

# Create a key ring in a region (location is immutable once set)
gcloud kms keyrings create my-keyring --location=us-central1

# Create a symmetric encryption key (defaults to software protection)
gcloud kms keys create my-key \
    --location=us-central1 \
    --keyring=my-keyring \
    --purpose=encryption

# Inspect and list
gcloud kms keys describe my-key --location=us-central1 --keyring=my-keyring
gcloud kms keys list --location=us-central1 --keyring=my-keyring
```

### 2. Encrypt and decrypt a file (symmetric)

```bash
# Encrypt with the primary key version (selected automatically)
gcloud kms encrypt \
    --key=my-key --keyring=my-keyring --location=us-central1 \
    --plaintext-file=secret.txt \
    --ciphertext-file=secret.txt.enc

# Decrypt (Cloud KMS detects the correct version from the ciphertext)
gcloud kms decrypt \
    --key=my-key --keyring=my-keyring --location=us-central1 \
    --ciphertext-file=secret.txt.enc \
    --plaintext-file=secret.txt.dec
```

Files must be ≤ 64 KiB. Pass `--plaintext-file=-` or `--ciphertext-file=-` to use stdin/stdout, and `--additional-authenticated-data-file` to bind AAD (must match on encrypt and decrypt).

### 3. Create an HSM-backed key with automatic rotation

```bash
gcloud kms keys create my-hsm-key \
    --location=us-central1 \
    --keyring=my-keyring \
    --purpose=encryption \
    --protection-level=hsm \
    --rotation-period=90d \
    --next-rotation-time=2026-09-01T00:00:00Z
```

### 4. Rotate a key (schedule update + manual version promotion)

```bash
# Update the automatic rotation schedule
gcloud kms keys update my-key \
    --location=us-central1 --keyring=my-keyring \
    --rotation-period=30d \
    --next-rotation-time=2026-06-01T00:00:00Z

# Manually create a new version and make it primary
gcloud kms keys versions create \
    --key=my-key --keyring=my-keyring --location=us-central1 --primary

# Or promote an existing version by number
gcloud kms keys set-primary-version my-key \
    --version=3 --keyring=my-keyring --location=us-central1

# Remove the automatic rotation schedule entirely
gcloud kms keys update my-key \
    --location=us-central1 --keyring=my-keyring --remove-rotation-schedule
```

### 5. Grant and revoke access to a key

```bash
# Grant encrypt+decrypt to a service account on one key
gcloud kms keys add-iam-policy-binding my-key \
    --location=us-central1 --keyring=my-keyring \
    --member="serviceAccount:my-sa@my-project.iam.gserviceaccount.com" \
    --role="roles/cloudkms.cryptoKeyEncrypterDecrypter"

# View the current policy
gcloud kms keys get-iam-policy my-key --location=us-central1 --keyring=my-keyring

# Revoke access
gcloud kms keys remove-iam-policy-binding my-key \
    --location=us-central1 --keyring=my-keyring \
    --member="serviceAccount:my-sa@my-project.iam.gserviceaccount.com" \
    --role="roles/cloudkms.cryptoKeyEncrypterDecrypter"
```

### 6. Disable, schedule destruction, and restore a key version

```bash
gcloud kms keys versions list --key=my-key --keyring=my-keyring --location=us-central1

# Disable a version (blocks use without destroying material)
gcloud kms keys versions disable 2 --key=my-key --keyring=my-keyring --location=us-central1

# Schedule destruction (24-hour grace period)
gcloud kms keys versions destroy 2 --key=my-key --keyring=my-keyring --location=us-central1

# Restore before the grace period elapses (moves back to Disabled)
gcloud kms keys versions restore 2 --key=my-key --keyring=my-keyring --location=us-central1
```

### 7. Asymmetric signing and public key retrieval

```bash
# Create an asymmetric signing key (algorithm required for asymmetric keys)
gcloud kms keys create my-sign-key \
    --location=us-central1 --keyring=my-keyring \
    --purpose=asymmetric-signing \
    --default-algorithm=ec-sign-p256-sha256

# Retrieve the public key for a version
gcloud kms keys versions get-public-key 1 \
    --key=my-sign-key --keyring=my-keyring --location=us-central1 \
    --output-file=pub.pem

# Sign a file with that version
gcloud kms asymmetric-sign \
    --key=my-sign-key --keyring=my-keyring --location=us-central1 --version=1 \
    --digest-algorithm=sha256 \
    --input-file=data.txt --signature-file=data.sig
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `kms` (top-level) | [`_commands.md`](_commands.md) | 9 | encrypt/decrypt, asymmetric/MAC sign & verify, raw encrypt/decrypt, decapsulate |
| `kms autokey-config` | [`autokey-config.md`](autokey-config.md) | 3 | update and retrieve the AutokeyConfig |
| `kms ekm-config` | [`ekm-config.md`](ekm-config.md) | 6 | update and retrieve the EkmConfig |
| `kms ekm-connections` | [`ekm-connections.md`](ekm-connections.md) | 8 | create and manage EKM connections |
| `kms import-jobs` | [`import-jobs.md`](import-jobs.md) | 7 | create and manage import jobs for bringing your own key |
| `kms inventory` | [`inventory.md`](inventory.md) | 3 | KMS Inventory and key-tracking / protected-resource queries |
| `kms key-handles` | [`key-handles.md`](key-handles.md) | 3 | create and manage Autokey KeyHandle resources |
| `kms keyrings` | [`keyrings.md`](keyrings.md) | 7 | create and manage key rings (and their IAM policies) |
| `kms keys` | [`keys.md`](keys.md) | 22 | create and manage keys, versions, rotation, and IAM |
| `kms locations` | [`locations.md`](locations.md) | 1 | view locations available for a project |
| `kms operations` | [`operations.md`](operations.md) | 1 | view long-running operation details |
| `kms single-tenant-hsm` | [`single-tenant-hsm.md`](single-tenant-hsm.md) | 9 | manage single-tenant HSM instances and proposals |

See [`index.md`](index.md) for a one-line index of all 79 GA commands.

## Common flags & tips

- **Resource identity**: nearly every command needs `--location` plus `--keyring`, and keys/versions need `--key`. A key is identified by name within a key ring; versions are referenced by their integer number.
- **`--purpose` (on `keys create`)** is always required: `encryption`, `asymmetric-encryption`, `asymmetric-signing`, `mac`, `raw-encryption`, or `key-encapsulation`. `--default-algorithm` is required for asymmetric, MAC-signing, raw, and external keys; symmetric `encryption` keys default to `google-symmetric-encryption`.
- **`--protection-level`**: `software` (default), `hsm`, `hsm-single-tenant`, `external`, or `external-vpc`. External and external-vpc keys require `--skip-initial-version-creation`.
- **Rotation**: `--rotation-period` (e.g. `30d`, `2160h`) and `--next-rotation-time` (ISO 8601 / RFC 3339). Manual rotation via `keys versions create --primary` or `keys set-primary-version` does not change `--next-rotation-time`.
- **Locations**: `global` plus regional/multi-regional values; list them with `gcloud kms locations list`. A key ring's location is fixed at creation.
- **Filtering / formatting** (standard gcloud flags on list commands):
  - `gcloud kms keys list --location=global --keyring=my-keyring --filter="purpose:ENCRYPTION"`
  - `gcloud kms keys versions list --key=my-key --keyring=my-keyring --location=global --filter="state=ENABLED" --format="value(name)"`
  - `gcloud kms keyrings list --location=global --limit=5`
- **Integrity**: encrypt/decrypt/sign/verify perform request/response integrity verification by default; `--skip-integrity-verification` disables it.
- **Inventory/tracking**: `gcloud kms inventory list-keys` and `gcloud kms inventory search-protected-resources --scope=ORG_ID --keyname=...` find keys and the resources they protect across a project/organization.

## beta / alpha

Both `gcloud beta kms` and `gcloud alpha kms` exist. Notable surface not in the GA `gcloud kms` group:

- `gcloud beta kms kaj-config` — manage Key Access Justifications (KAJ) configs.
- `gcloud beta kms kaj-enrollment` — retrieve KAJ enrollment configs.

Features such as `mac-sign`/`mac-verify`, `raw-encrypt`/`raw-decrypt`, `decapsulate`, `key-handles`, and `single-tenant-hsm` are now GA (present in this reference). Check `gcloud beta kms --help` before relying on a newer capability in production scripts.

## Official documentation

- [Cloud KMS documentation home](https://cloud.google.com/kms/docs) — product overview, concepts, and how-tos.
- [Create key rings and keys](https://cloud.google.com/kms/docs/create-encryption-keys) — create key rings and encryption keys with gcloud.
- [Encrypt and decrypt data](https://cloud.google.com/kms/docs/encrypt-decrypt) — symmetric encrypt/decrypt of a file with gcloud.
- [Rotate a key](https://cloud.google.com/kms/docs/rotate-key) — automatic schedules and manual version creation.
- [Key rotation concepts](https://cloud.google.com/kms/docs/key-rotation) — why and what rotation does (and does not) do.
- [Algorithms and protection levels](https://cloud.google.com/kms/docs/algorithms) — purposes, algorithms, and protection levels reference.
- [Control access with IAM](https://cloud.google.com/kms/docs/iam) — predefined Cloud KMS roles and permissions.
- [gcloud kms CLI reference](https://cloud.google.com/sdk/gcloud/reference/kms) — full command/flag reference (GA, with beta/alpha variants).

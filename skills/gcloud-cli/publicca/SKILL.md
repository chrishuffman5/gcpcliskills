---
name: gcloud-publicca
description: >-
  Public Certificate Authority via gcloud (`gcloud publicca`). Manage accounts for Google Trust Services' Certificate Authority — external-account-keys.
---

# gcloud publicca — Public Certificate Authority

## Overview

Public Certificate Authority (Public CA) lets you programmatically obtain publicly trusted TLS/SSL certificates from Google Trust Services using the ACME (Automatic Certificate Management Environment) protocol. The `gcloud publicca` surface is intentionally narrow: it mints the ACME External Account Binding (EAB) credentials — a key ID and an HMAC secret — that you then hand to a standard ACME client (such as Certbot) to register and request certificates. Reach for it when you want automated, standards-based issuance of public certificates rather than the Google-managed certificate workflow in Certificate Manager.

## Quick reference — common workflows

Enable the API once per project before using any command:

```bash
gcloud services enable publicca.googleapis.com
```

You also need `roles/publicca.externalAccountKeyCreator` on the project to mint EAB keys:

```bash
gcloud projects add-iam-policy-binding PROJECT_ID \
    --member="user:USER_EMAIL" \
    --role="roles/publicca.externalAccountKeyCreator"
```

### 1. Create an external account key (print to stdout)

```bash
# Mints an EAB key pair; output includes the key ID and HMAC secret
gcloud publicca external-account-keys create
```

### 2. Create an external account key and save it to a file

```bash
gcloud publicca external-account-keys create \
    --key-output-file=./external_account_key.txt
```

The generated key is written to the given path for later use with your ACME client.

### 3. Create an EAB key for a specific (non-default) project

```bash
gcloud publicca external-account-keys create \
    --project=MY_PROJECT_ID \
    --key-output-file=./eab_key.txt
```

Use the gcloud-wide `--project` flag when your active `gcloud config` project differs from the target.

### 4. End-to-end: enable API, mint EAB key, register with an ACME client

```bash
# Step 1: enable the API
gcloud services enable publicca.googleapis.com --project=PROJECT_ID

# Step 2: create the EAB key and save it to a file
gcloud publicca external-account-keys create \
    --key-output-file=./eab_key.txt

# Step 3+: hand the key ID and HMAC secret from the file to your ACME
# client (e.g. Certbot) to register against the Public CA ACME directory
# and request certificates. See the Public CA tutorial for the exact
# client invocation.
```

> Only the `gcloud` commands originate from this CLI surface; the ACME client steps (registration, certificate issuance) run in your chosen ACME client and are documented in the Public CA tutorial.

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `publicca external-account-keys` | [`external-account-keys.md`](external-account-keys.md) | 1 | Create ACME external account binding (EAB) keys |

See [`index.md`](index.md) for a one-line index of all 1 GA command.

## Common flags & tips

- **`--key-output-file`** is the only command-specific flag. Without it, the key ID and HMAC secret are printed to stdout; with it, the generated key is written to the specified path. Treat the output as a secret — it grants the ability to request certificates under your project.
- **Scope.** EAB keys are project-scoped. Use the gcloud-wide `--project=PROJECT_ID` flag to mint a key for a project other than your active configuration.
- **No regional flag.** The command takes no `--location`/`--region`; Public CA is a global service.
- **Output formatting.** Standard gcloud-wide flags apply, e.g. `gcloud publicca external-account-keys create --format=json` to capture the `keyId` and `b64MacKey` fields programmatically.
- **One-shot resource.** There is no `list`, `describe`, or `delete` for external account keys — `create` is the sole command. Re-run `create` to mint additional key pairs.

## beta / alpha

`gcloud beta publicca` and `gcloud alpha publicca` mirror the GA surface exactly: the same single subgroup (`external-account-keys`) and command (`create`) with the same `--key-output-file` flag. There are no track-exclusive subcommands or flags. Use the GA track (`gcloud publicca`) in production; beta/alpha offer no documented advantage for this service.

## Official documentation

- [Public CA documentation](https://cloud.google.com/certificate-manager/docs/public-ca) — product docs home; what Public CA does and supported ACME challenge types (HTTP-01, TLS-ALPN-01, DNS-01).
- [Public CA tutorial](https://cloud.google.com/certificate-manager/docs/public-ca-tutorial) — request a certificate using Public CA and Certbot; full EAB → ACME → certificate flow.
- [Certificate Manager overview](https://cloud.google.com/certificate-manager/docs/overview) — where Public CA sits within the broader certificate management service.
- [Domain authorization](https://cloud.google.com/certificate-manager/docs/domain-authorization) — DNS vs. load-balancer authorization methods.
- [IAM permissions](https://cloud.google.com/certificate-manager/docs/permissions) — roles for Certificate Manager and Public CA, including `roles/publicca.externalAccountKeyCreator`.
- [gcloud CLI reference](https://cloud.google.com/sdk/gcloud/reference/publicca) — the `gcloud publicca` command group.
- [external-account-keys create reference](https://cloud.google.com/sdk/gcloud/reference/publicca/external-account-keys/create) — flags, synopsis, and examples for the single GA command.

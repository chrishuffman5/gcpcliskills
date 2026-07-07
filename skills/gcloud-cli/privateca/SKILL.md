---
name: gcloud-privateca
description: >-
  Certificate Authority Service via gcloud (`gcloud privateca`). Manage private Certificate Authorities on Google Cloud — certificates, locations, pools, roots, subordinates, templates.
---

# gcloud privateca — Certificate Authority Service

## Overview

Certificate Authority Service (CAS) is a highly available, scalable Google Cloud service for
deploying, managing, and securing your own private certificate authorities (CAs) without running
CA infrastructure yourself. Reach for `gcloud privateca` when you need to issue and manage private
X.509 certificates for internal TLS, service mesh / mTLS, device or workload identity, and similar
PKI use cases. Resources are organized hierarchically: **CA pools** contain **certificate
authorities** (roots or subordinates), which issue **certificates**; **certificate templates**
define reusable, policy-constrained issuance profiles.

## Quick reference — common workflows

### Enable the API

```bash
gcloud services enable privateca.googleapis.com
```

### 1. Create a CA pool and root CA, then enable it

```bash
# Create a CA pool (Enterprise tier is the default; publishes CA certs and CRLs by default)
gcloud privateca pools create my-pool \
  --location=us-west1 \
  --tier=enterprise

# Create a root CA inside the pool (created in STAGED state)
gcloud privateca roots create prod-root \
  --location=us-west1 \
  --pool=my-pool \
  --subject="CN=Example Production Root CA, O=Example" \
  --key-algorithm=rsa-pkcs1-4096-sha256 \
  --validity=P10Y \
  --max-chain-length=1

# Enable the root CA so it can issue certificates
gcloud privateca roots enable prod-root \
  --location=us-west1 \
  --pool=my-pool
```

### 2. Create a subordinate CA signed by a Private CA root

```bash
gcloud privateca pools create sub-pool \
  --location=us-west1 \
  --tier=enterprise

# Issuer is in another CA pool on this same Private CA instance
gcloud privateca subordinates create server-tls-1 \
  --location=us-west1 \
  --pool=sub-pool \
  --subject="CN=Example TLS CA, O=Example" \
  --issuer-pool=my-pool \
  --issuer-location=us-west1 \
  --key-algorithm=rsa-pkcs1-2048-sha256 \
  --validity=P3Y \
  --auto-enable
```

### 3. Subordinate CA with an external issuer (CSR workflow)

```bash
# Generate a CSR for signing by an external CA
gcloud privateca subordinates create ext-sub-ca \
  --location=us-west1 \
  --pool=sub-pool \
  --subject="CN=External Sub CA, O=Example" \
  --create-csr \
  --csr-output-file=./ext-sub-ca.csr

# (Sign the CSR with your external CA to produce chain.crt, then activate.)
gcloud privateca subordinates activate ext-sub-ca \
  --location=us-west1 \
  --pool=sub-pool \
  --pem-chain=./chain.crt \
  --auto-enable
```

### 4. Issue a certificate (client-generated key, preset profile)

```bash
gcloud privateca certificates create frontend-server-tls \
  --issuer-pool=sub-pool \
  --issuer-location=us-west1 \
  --generate-key \
  --key-output-file=./server.key \
  --cert-output-file=./server.crt \
  --dns-san=www.example.com \
  --use-preset-profile=leaf_server_tls \
  --validity=P90D
```

### 5. Issue a certificate from a CSR, then revoke it

```bash
gcloud privateca certificates create my-cert \
  --issuer-pool=sub-pool \
  --issuer-location=us-west1 \
  --csr=./server.csr \
  --cert-output-file=./server.crt \
  --validity=P30D

# Revoke if the key is compromised
gcloud privateca certificates revoke \
  --certificate=my-cert \
  --issuer-pool=sub-pool \
  --issuer-location=us-west1 \
  --reason=key-compromise
```

### 6. Create a policy-constrained template and use it

```bash
# Restrict issued certs to DNS SANs only
gcloud privateca templates create dns-only-template \
  --location=us-west1 \
  --description="Restricts certificates to DNS SANs." \
  --no-copy-subject \
  --copy-sans \
  --identity-cel-expression="subject_alt_names.all(san, san.type == DNS)"

# Grant a service account permission to use the template
gcloud privateca templates add-iam-policy-binding dns-only-template \
  --location=us-west1 \
  --member="serviceAccount:my-sa@my-project.iam.gserviceaccount.com" \
  --role="roles/privateca.templateUser"

# Issue a certificate that uses the template
gcloud privateca certificates create dns-cert \
  --issuer-pool=sub-pool \
  --issuer-location=us-west1 \
  --template=dns-only-template \
  --template-location=us-west1 \
  --generate-key \
  --key-output-file=./dns.key \
  --cert-output-file=./dns.crt \
  --dns-san=api.example.com
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `privateca certificates` | [`certificates.md`](certificates.md) | 6 | Issue, describe, export, list, revoke, and update certificates |
| `privateca locations` | [`locations.md`](locations.md) | 1 | List locations supported by the Private CA GA API |
| `privateca pools` | [`pools.md`](pools.md) | 10 | Create/manage CA pools and their IAM policies |
| `privateca roots` | [`roots.md`](roots.md) | 8 | Create and manage root certificate authorities |
| `privateca subordinates` | [`subordinates.md`](subordinates.md) | 10 | Create, activate, and manage subordinate certificate authorities |
| `privateca templates` | [`templates.md`](templates.md) | 10 | Create/manage certificate templates and their IAM policies |

See [`index.md`](index.md) for a one-line index of all 45 commands.

## Common flags & tips

- **Location is mandatory and regional.** Almost every command needs `--location` (and most CA
  commands also need `--pool` / `--issuer-pool`). Set a default once with
  `gcloud config set privateca/location us-west1` to omit it from individual commands.
- **CA pool tiers.** `pools create --tier` is one of `enterprise` (default) or `devops`. CRL
  publication is not supported for the DevOps tier, and certificate IDs are optional when issuing
  from a DevOps-tier pool.
- **CA lifecycle.** Roots and subordinates are created STAGED by default; they cannot issue until
  enabled. Use `--auto-enable` on create/activate to enable immediately, or run the explicit
  `roots enable` / `subordinates enable` command.
- **Key options.** `roots create` defaults to `--key-algorithm=rsa-pkcs1-4096-sha256`;
  `subordinates create` defaults to `rsa-pkcs1-2048-sha256`. Provide a Cloud KMS key version with
  `--kms-key-version=...` to use your own key instead of a Google-managed key.
- **Certificate issuance modes** on `certificates create` (mutually exclusive): from a `--csr`,
  or from generated SANs plus either `--generate-key --key-output-file` or a KMS key version,
  combined with either `--use-preset-profile` or explicit key-usage/CA-cert flags.
- **Validity** is an ISO-8601 duration: `--validity=P30D` (default for certs), `P90D`, `P3Y`
  (default for subordinates), `P10Y` (default for roots).
- **Deletion has a grace period.** `roots delete` / `subordinates delete` allow undelete within
  30 days; use `--skip-grace-period` to delete immediately and `--ignore-active-certificates`
  to bypass the active-certificate check.
- **Useful describe/export patterns:**
  ```bash
  # Download a leaf cert's PEM via describe
  gcloud privateca certificates describe frontend-server-tls \
    --issuer-pool=my-pool --issuer-location=us-west1 \
    --format="value(pemCertificate)" > frontend-server-tls.crt

  # Export a cert with its full issuing chain
  gcloud privateca certificates export my-cert \
    --issuer-pool=my-pool --issuer-location=us-west1 \
    --include-chain --output-file=chain.pem

  # Fetch all active root CA certs for a pool
  gcloud privateca pools get-ca-certs my-pool \
    --location=us-west1 --output-file=ca-certificates.pem
  ```
- **Filtering lists:** `certificates list` requires staying within a single location; filter by
  issuing CA, e.g.
  `--filter="issuer_certificate_authority='projects/.../certificateAuthorities/my-ca'"`.
- **Templates are regional but replicable.** Use `templates replicate ... --all-locations` (or
  `--target-locations`) to copy a template across regions.

## beta / alpha

A `gcloud beta privateca` surface exists, but at the time of research no beta-only capabilities
were documented as distinct from GA — the GA surface covers all 45 commands across the 6 command
groups above. Check `gcloud beta privateca --help` (and `gcloud alpha privateca --help`) for any
pre-GA features before relying on them.

## Official documentation

- [Certificate Authority Service docs (product home)](https://cloud.google.com/certificate-authority-service/docs) — overview, concepts, and how-to guides.
- [Quickstart](https://cloud.google.com/certificate-authority-service/docs/quickstart) — create a CA pool and root CA, request a certificate, and clean up.
- [Create a CA pool](https://cloud.google.com/certificate-authority-service/docs/creating-ca-pool) — via Console, gcloud, Terraform, or REST.
- [Create certificate authorities](https://cloud.google.com/certificate-authority-service/docs/creating-certificate-authorities) — create a root CA (STAGED by default, then enable).
- [Create a certificate template](https://cloud.google.com/certificate-authority-service/docs/creating-certificate-template) — X.509 constraints and CEL identity expressions.
- [Access control (IAM roles)](https://cloud.google.com/certificate-authority-service/docs/access-control) — the predefined CA Service roles and their permissions.
- [gcloud privateca CLI reference](https://cloud.google.com/sdk/gcloud/reference/privateca) — full reference for all command groups.
- [REST API reference](https://cloud.google.com/certificate-authority-service/docs/reference/rest) — underlying privateca.googleapis.com API.

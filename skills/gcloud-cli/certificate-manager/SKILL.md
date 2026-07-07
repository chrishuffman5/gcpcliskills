---
name: gcloud-certificate-manager
description: >-
  Certificate Manager via gcloud (`gcloud certificate-manager`). Manage SSL certificates for your Google Cloud projects — certificates, dns-authorizations, issuance-configs, maps, operations, trust-configs.
---

# gcloud certificate-manager — Certificate Manager

## Overview

Certificate Manager acquires, deploys, and manages TLS/SSL certificates for use with Cloud Load Balancing and proxy Network Load Balancers. It handles both Google-managed certificates (auto-renewed, validated via DNS authorization or the serving endpoint) and self-managed certificates you upload as PEM files. Reach for it when you need to provision certificates at scale, organize them into certificate maps for SNI-based selection, or configure mTLS trust anchors via trust configs.

## Quick reference — common workflows

Enable the API once per project before using any command:

```bash
gcloud services enable certificatemanager.googleapis.com
# For CA Service-backed issuance also enable: privateca.googleapis.com
# For load balancer attachment also enable: compute.googleapis.com
```

### 1. Google-managed certificate with DNS authorization

```bash
# Create a DNS authorization for the domain
gcloud certificate-manager dns-authorizations create my-auth \
    --domain=api.example.com

# Inspect it to get the CNAME record you must add to your DNS zone
gcloud certificate-manager dns-authorizations describe my-auth

# Create the managed certificate, referencing the DNS authorization
gcloud certificate-manager certificates create api-example-com \
    --domains="api.example.com" \
    --dns-authorizations=my-auth

# Verify status (wait for ACTIVE)
gcloud certificate-manager certificates describe api-example-com
```

### 2. Upload a self-managed certificate

```bash
gcloud certificate-manager certificates create www-example-com \
    --certificate-file=cert.pem \
    --private-key-file=key.pem

gcloud certificate-manager certificates list
```

### 3. Build a certificate map for SNI-based selection

```bash
# Create the map
gcloud certificate-manager maps create my-map

# Per-hostname entry
gcloud certificate-manager maps entries create my-entry \
    --map=my-map \
    --hostname=api.example.com \
    --certificates=api-example-com

# Default (catch-all) entry used when no hostname matches on SNI
gcloud certificate-manager maps entries create my-default-entry \
    --map=my-map \
    --set-primary \
    --certificates=api-example-com

gcloud certificate-manager maps entries list --map=my-map
```

### 4. Issue a certificate via CA Service (private / internal PKI)

```bash
# Create a Certificate Issuance Config pointing at a CA pool
gcloud certificate-manager issuance-configs create my-cic \
    --ca-pool=projects/my-project/locations/us-west1/caPools/my-ca-pool \
    --key-algorithm=rsa-2048 \
    --lifetime=P90D \
    --rotation-window-percentage=66

# Create a managed certificate that uses the issuance config
gcloud certificate-manager certificates create internal-cert \
    --domains="internal.example.com" \
    --issuance-config=my-cic

gcloud certificate-manager certificates describe internal-cert
```

### 5. Manage a TrustConfig for mTLS / client authentication

```bash
# Create a TrustConfig from PEM trust anchors and intermediate CAs
gcloud certificate-manager trust-configs create my-trust-config \
    --description="My mTLS trust config" \
    --trust-store=trust-anchors=ta.pem,intermediate-cas="ica1.pem;ica2.pem"

# Export to YAML for backup or review
gcloud certificate-manager trust-configs export my-trust-config \
    --destination=my-trust-config.yaml \
    --location=global

# Re-import from YAML
gcloud certificate-manager trust-configs import my-trust-config \
    --source=my-trust-config.yaml \
    --location=global
```

### 6. Inventory and monitor resources

```bash
gcloud certificate-manager certificates list
gcloud certificate-manager dns-authorizations list
gcloud certificate-manager maps list
gcloud certificate-manager issuance-configs list

# Track long-running operations
gcloud certificate-manager operations list
gcloud certificate-manager operations describe OPERATION_ID
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `certificate-manager certificates` | [`certificates.md`](certificates.md) | 5 | Manage Google-managed and self-managed certificates |
| `certificate-manager dns-authorizations` | [`dns-authorizations.md`](dns-authorizations.md) | 5 | Manage DNS authorizations for domain-ownership validation |
| `certificate-manager issuance-configs` | [`issuance-configs.md`](issuance-configs.md) | 5 | Manage Certificate Issuance Configs (CA Service integration) |
| `certificate-manager maps` | [`maps.md`](maps.md) | 10 | Manage certificate maps and map entries for SNI selection |
| `certificate-manager operations` | [`operations.md`](operations.md) | 2 | Inspect long-running operations |
| `certificate-manager trust-configs` | [`trust-configs.md`](trust-configs.md) | 7 | Manage trust configs (trust anchors / intermediate CAs for mTLS) |

See [`index.md`](index.md) for a one-line index of all 34 GA commands.

## Common flags & tips

- **Location is global by default.** Every resource accepts `--location` (defaults to `global`). For regional resources, set `--location=REGION` explicitly. `list` commands accept `--location` and several default to the `-` wildcard so they enumerate all locations.
- **Managed vs. self-managed certificates.** Use `--domains` (optionally with `--dns-authorizations` or `--issuance-config`) for managed certificates; use `--certificate-file` + `--private-key-file` (PEM) for self-managed uploads. These two modes are mutually exclusive.
- **Certificate scope.** `certificates create --scope` accepts `default` (Load Balancing / Cloud CDN — the usual choice), `all-regions` (Cross-region Internal Application Load Balancer), `client-auth` (client authentication), and `edge-cache` (Media Edge).
- **Issuance-config defaults.** `--key-algorithm` defaults to `rsa-2048` (or `ecdsa-p256`), `--lifetime` to `P30D` (ISO 8601 duration), and `--rotation-window-percentage` to `66`.
- **Map entries require exactly one selector.** Provide either `--hostname=FQDN` or `--set-primary` (the catch-all used when no SNI match exists), never both.
- **TrustConfig PEM syntax.** `--trust-store` takes `trust-anchors=` and optional `intermediate-cas=`; separate multiple files within a key with semicolons and quote them, e.g. `--trust-store trust-anchors="ta1.pem;ta2.pem",intermediate-cas="ica1.pem;ica2.pem"`.
- **`--async`** is available on every create/update/delete (and `trust-configs import`) to return immediately; poll progress with `operations describe`.
- **Useful filters/formats:**
  - `gcloud certificate-manager certificates list --filter="domains:example.com"`
  - `gcloud certificate-manager certificates list --format="table(name, managed.state, expireTime)"`
  - `gcloud certificate-manager operations list --filter="done=false"`

## beta / alpha

Both `gcloud beta certificate-manager` and `gcloud alpha certificate-manager` expose the same six command groups (certificates, dns-authorizations, issuance-configs, maps, operations, trust-configs) as GA, with no track-exclusive subcommands. Some alpha features may be gated behind an invitation-only early-access allowlist. In the CA Service deployment workflow, the related `gcloud beta services identity create` command is used to provision the Certificate Manager service account needed for CA Service integration.

## Official documentation

- [Certificate Manager documentation](https://cloud.google.com/certificate-manager/docs) — product docs home.
- [Product overview](https://cloud.google.com/certificate-manager/docs/overview) — certificate types, certificate maps, DNS authorizations, trust configs.
- [Deployment overview](https://cloud.google.com/certificate-manager/docs/deploy) — provisioning certificates for Application LBs and proxy Network LBs.
- [Manage certificates](https://cloud.google.com/certificate-manager/docs/certificates) — create/update/list/delete certificates and required IAM roles.
- [Manage DNS authorizations](https://cloud.google.com/certificate-manager/docs/dns-authorizations) — domain-ownership verification flow.
- [Manage certificate maps](https://cloud.google.com/certificate-manager/docs/maps) — maps and attaching them to target HTTPS proxies.
- [Deploy a Google-managed cert with DNS auth](https://cloud.google.com/certificate-manager/docs/deploy-google-managed-dns-auth) — end-to-end tutorial.
- [Deploy a self-managed cert](https://cloud.google.com/certificate-manager/docs/deploy-self-managed) — global load balancer tutorial.
- [Deploy a Google-managed cert with CA Service](https://cloud.google.com/certificate-manager/docs/deploy-google-managed-cas) — private PKI tutorial.
- [gcloud CLI reference](https://cloud.google.com/sdk/gcloud/reference/certificate-manager) — all six command groups and 34 GA commands.

---
name: gcloud-active-directory
description: >-
  Managed Service for Microsoft AD via gcloud (`gcloud active-directory`). Manage Managed Microsoft AD resources — domains, operations, peerings.
---

# gcloud active-directory — Managed Service for Microsoft AD

## Overview

`gcloud active-directory` manages Google Cloud's Managed Service for Microsoft Active Directory (Managed Microsoft AD): highly available, hardened Microsoft AD domains running on Google-managed Windows domain controllers. Reach for it when you need real Active Directory (Kerberos, LDAP, Group Policy, domain join) for Windows workloads on Google Cloud without operating the underlying DCs, patching, or backups yourself. You provide a domain name, a reserved IP range, and authorized VPC networks; Google manages topology, multi-region HA, schema, and trusts to your on-premises or other AD forests.

## Quick reference — common workflows

### 1. Enable the API and create a domain
Domain creation can take up to ~60 minutes; use `--async` plus `operations` to track it, or omit it to block until done.
```bash
gcloud services enable managedidentities.googleapis.com

gcloud active-directory domains create ad.example.com \
    --region=us-central1 \
    --reserved-ip-range="10.172.0.0/24" \
    --authorized-networks=projects/my-project/global/networks/my-network \
    --enable-audit-logs

gcloud active-directory domains describe ad.example.com
```

### 2. Add a region (multi-region HA) and peer another VPC
```bash
# Add a second region for high availability
gcloud active-directory domains update ad.example.com \
    --add-region=us-east1

# Authorize an additional VPC network on the domain
gcloud active-directory domains update ad.example.com \
    --add-authorized-networks=projects/my-project/global/networks/second-network
```

### 3. Reset the delegated admin password
```bash
# Resets the delegated administrator (MIAdmin) password and prints the new one
gcloud active-directory domains reset-admin-password ad.example.com
```

### 4. Create and validate a trust to another AD forest
```bash
# Create a bidirectional forest trust to an on-prem / external domain
gcloud active-directory domains trusts create ad.example.com \
    --target-domain-name=onprem.corp.com \
    --target-dns-ip-addresses=10.177.0.2 \
    --type=FOREST \
    --direction=BIDIRECTIONAL \
    --async

# Verify the trust is healthy
gcloud active-directory domains trusts validate-state ad.example.com \
    --target-domain-name=onprem.corp.com
```

### 5. Cross-project VPC access with peerings
```bash
# Let a VPC in another project reach the AD domain
gcloud active-directory peerings create my-peering \
    --domain=projects/domain-project/locations/global/domains/ad.example.com \
    --authorized-network=projects/network-project/global/networks/my-network

gcloud active-directory peerings list
gcloud active-directory peerings describe my-peering
```

### 6. Back up and restore a domain
```bash
# Create a manual backup
gcloud active-directory domains backups create my-backup \
    --domain=ad.example.com --async

gcloud active-directory domains backups list --domain=ad.example.com

# Restore the domain from a backup, then watch the operation
gcloud active-directory domains restore ad.example.com \
    --backup=my-backup --async
gcloud active-directory operations list
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `active-directory domains` | [`domains.md`](domains.md) | 21 | Manage Managed Microsoft AD domains, plus `backups` and `trusts` subgroups |
| `active-directory operations` | [`operations.md`](operations.md) | 3 | Track and cancel long-running domain operations |
| `active-directory peerings` | [`peerings.md`](peerings.md) | 5 | Authorize VPC networks in other projects to use a domain |

See [`index.md`](index.md) for a one-line index of all 29 GA commands.

## Common flags & tips

- **Resource naming.** Most commands accept either a short ID (e.g. `ad.example.com`) or a fully qualified name `projects/PROJECT/locations/global/domains/DOMAIN`. The domain resource lives at location `global` even though domain controllers are provisioned per `--region`. `backups` are addressed as `.../domains/DOMAIN/backups/BACKUP`.
- **`--async`.** Domain create/update/restore, trust, backup, and peering operations are long-running. Add `--async` to return immediately and poll with `gcloud active-directory operations list` / `describe NAME`, or cancel with `operations cancel NAME`.
- **`--reserved-ip-range` (create).** Must be a CIDR block that does not overlap any authorized network's CIDR, or creation fails.
- **`domains update` add/remove flags.** Regions and authorized networks are edited incrementally: `--add-region` / `--remove-region` and `--add-authorized-networks` / `--remove-authorized-networks` (mutually exclusive within each pair). Labels use `--update-labels` / `--remove-labels` / `--clear-labels`.
- **Trusts.** `--type` is `FOREST` (default) or `EXTERNAL`; `--direction` is `BIDIRECTIONAL` (default), `INBOUND`, or `OUTBOUND`. Omit `--handshake-secret` to be prompted securely. Use `--selective-authentication` to restrict trusted-side access.
- **LDAPS.** Enable by uploading a PKCS#12 chain with `domains update-ldaps-settings --certificate-pfx-file=...` (you are prompted for the password if `--certificate-password` is omitted); disable with `--clear-certificates`.
- **Filtering / formatting.** List commands support `--filter`, `--sort-by`, `--limit`, and `--page-size`. Examples:
  ```bash
  gcloud active-directory domains list --filter="state=READY" --format="table(name,locations,state)"
  gcloud active-directory operations list --filter="done=false"
  ```

## beta / alpha

`gcloud beta active-directory` adds domain subcommands that have no GA equivalent:

- `gcloud beta active-directory domains migration` — `check-permissions`, `enable`, `disable` for on-prem AD migration workflows.
- `gcloud beta active-directory domains sql-integrations` — `describe` and `list` for Cloud SQL + Managed AD integration.

Commands such as `extend-schema`, `describe-ldaps-settings`, `update-ldaps-settings`, `reset-admin-password`, `restore`, and the `backups` and `trusts` subgroups exist in both GA and beta. No `gcloud alpha active-directory` surface is published.

## Official documentation

- [Managed Microsoft AD documentation home](https://cloud.google.com/managed-microsoft-ad/docs) — quickstarts, how-tos, API reference, and pricing.
- [Service overview](https://cloud.google.com/managed-microsoft-ad/docs/overview) — architecture, forest models, and multi-region HA.
- [How-to guides](https://cloud.google.com/managed-microsoft-ad/docs/how-to) — create a domain, configure trusts, LDAPS, and more.
- [Access control (IAM)](https://cloud.google.com/managed-microsoft-ad/docs/access-control) — predefined `roles/managedidentities.*` roles.
- [Pricing](https://cloud.google.com/managed-microsoft-ad/pricing) — per-region, per-domain hourly cost.
- [gcloud active-directory CLI reference](https://cloud.google.com/sdk/gcloud/reference/active-directory) — full command/flag reference (GA).
- [gcloud beta active-directory CLI reference](https://cloud.google.com/sdk/gcloud/reference/beta/active-directory) — beta-only `migration` and `sql-integrations` subcommands.

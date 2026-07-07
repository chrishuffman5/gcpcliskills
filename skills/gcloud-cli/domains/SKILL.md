---
name: gcloud-domains
description: >-
  Cloud Domains via gcloud (`gcloud domains`). Manage domains for your Google Cloud projects — registrations.
---

# gcloud domains — Cloud Domains

## Overview
Cloud Domains is Google Cloud's domain registration and management service. Use `gcloud domains` to search availability across 300+ TLDs, register new domains, and manage an existing registration's DNS, DNSSEC, contacts, privacy, renewal, and transfer settings — all billed through Cloud Billing and governed by project IAM. Reach for it when you want to buy and operate a domain alongside your other Google Cloud resources (for example, wiring a registration directly to a Cloud DNS managed zone).

## Quick reference — common workflows

Enable the API once per project before using the commands below:

```bash
gcloud services enable domains.googleapis.com
```

### Search availability and pricing
```bash
# Cached suggestions for a search term or domain (fast, may be stale)
gcloud domains registrations search-domains my-new-project

# Up-to-date availability, price, privacy modes, and notices for one domain
gcloud domains registrations get-register-parameters example.com
```

### Register a domain (interactive vs. scripted)
```bash
# Interactive: prompts for contacts, DNS, privacy, and price
gcloud domains registrations register example.com

# Non-interactive: provide contacts, privacy, price, and a name-server source
gcloud domains registrations register example.com \
    --contact-data-from-file=contacts.yaml \
    --contact-privacy=private-contact-data \
    --yearly-price="12.00 USD" \
    --cloud-dns-zone=example-com \
    --quiet
```

### Point a registration at a Cloud DNS zone (and DNSSEC)
```bash
# Use a Cloud DNS managed zone; DNSSEC stays off unless it is safe to enable
gcloud domains registrations configure dns example.com \
    --cloud-dns-zone=example-zone

# Use a signed zone and enable DNSSEC explicitly
gcloud domains registrations configure dns example.com \
    --cloud-dns-zone=example-zone --no-disable-dnssec

# Disable DNSSEC
gcloud domains registrations configure dns example.com --disable-dnssec
```

### Manage renewal, transfer lock, and auth code
```bash
# Stop auto-renewal (domain expires at its expiration time)
gcloud domains registrations configure management example.com \
    --preferred-renewal-method=renewal-disabled

# Unlock the transfer lock before moving to another registrar
gcloud domains registrations configure management example.com \
    --transfer-lock-state=unlocked

# Get the authorization code (only after 60 days since registration)
gcloud domains registrations authorization-code get example.com

# Push transfer for .uk / .co.uk domains
gcloud domains registrations initiate-push-transfer example.co.uk \
    --tag=NEW_REGISTRY_TAG
```

### Inspect registrations and async operations
```bash
gcloud domains registrations list
gcloud domains registrations describe example.com

# Long-running changes return an operation you can poll
gcloud domains registrations operations list
gcloud domains registrations operations wait OPERATION_ID
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `domains registrations` | [`registrations.md`](registrations.md) | 19 | Manage Cloud Domains registrations: register, list/describe/delete, search, renew, update labels, plus `authorization-code`, `configure`, `google-domains-dns`, and `operations` subgroups |
| `domains` (top level) | [`_commands.md`](_commands.md) | 2 | `list-user-verified` and `verify` — verify domain ownership for use across Google Cloud products |

See [`index.md`](index.md) for a one-line index of all 21 commands.

## Common flags & tips
- **Registration ID = domain name.** Commands take the domain itself as the positional `REGISTRATION` (e.g. `example.com`); location is always `global`, so no `--location`/`--region` flag is needed.
- **Name-server source is mutually exclusive.** On `register` and `configure dns`, pick exactly one of `--cloud-dns-zone`, `--name-servers`, or `--use-google-domains-dns` (`configure dns` also accepts `--dns-settings-from-file`).
- **DNSSEC default.** With a Cloud DNS zone, DNSSEC is enabled only when the zone is signed and safe; pass `--no-disable-dnssec` to force-enable or `--disable-dnssec` to turn it off.
- **Scripting.** Add `--quiet` to suppress prompts and `--validate-only` (on `register`, `renew-domain`, `configure contacts`/`dns`) to dry-run a change. Use `--async` to return immediately and track progress with the `operations` subgroup.
- **Pricing.** `--yearly-price` must match the price returned by `get-register-parameters`, formatted as `"12.00 USD"`.
- **Labels.** `register --labels=KEY=VALUE` sets labels; `update --update-labels` / `--remove-labels` / `--clear-labels` manage them afterward (`update` currently changes labels only).
- **Filtering/formatting.** `list` and `operations list` support standard `--filter`, `--sort-by`, `--limit`, and `--uri`, e.g. `gcloud domains registrations list --format="table(domainName, state, expireTime)"`.

## beta / alpha
`gcloud beta domains` and `gcloud alpha domains` mirror the GA command surface (same `registrations` subgroups plus `list-user-verified` / `verify`) and carry the usual pre-GA stability warnings. They expose no extra commands beyond GA today; the underlying API also has a `v1beta1` version, but GA (`v1`) is recommended for production. Reach for the beta/alpha tracks only when explicitly targeting `v1beta1` API behavior.

## Official documentation
- [Cloud Domains documentation home](https://docs.cloud.google.com/domains/docs) — product docs landing page.
- [Product overview](https://docs.cloud.google.com/domains/docs/overview) — features and integration with Cloud DNS and IAM.
- [Key terms](https://docs.cloud.google.com/domains/docs/key-terms) — registrant, registrar, registry, DNSSEC, WHOIS, premium domains.
- [Buy and register a domain](https://docs.cloud.google.com/domains/docs/buy-register-domain) — quickstart for searching, configuring DNS, and registering.
- [Register a domain with gcloud](https://docs.cloud.google.com/domains/docs/register-domain) — step-by-step CLI how-to, including Cloud DNS zone creation.
- [Edit registration settings](https://docs.cloud.google.com/domains/docs/edit-registration-settings) — change contacts, DNS, and renewal via `configure` subcommands.
- [Transfer a domain to another registrar](https://docs.cloud.google.com/domains/docs/transfer-domain-to-another-registrar) — unlock, get auth code, and initiate transfer.
- [Access control (IAM)](https://docs.cloud.google.com/domains/docs/access-control) — roles and per-method permissions.
- [gcloud domains reference](https://docs.cloud.google.com/sdk/gcloud/reference/domains) — full CLI command reference.

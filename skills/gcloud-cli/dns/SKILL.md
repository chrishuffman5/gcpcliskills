---
name: gcloud-dns
description: >-
  Cloud DNS via gcloud (`gcloud dns`). Manage your Cloud DNS managed-zones and record-sets — dns-keys, managed-zones, operations, policies, project-info, record-sets, response-policies.
---

# gcloud dns — Cloud DNS

## Overview

Cloud DNS is Google Cloud's managed, authoritative DNS service that publishes your
domain names to the global internet (public zones) or to your VPC networks (private
zones) using Google's anycast name servers. Use `gcloud dns` to create and manage
managed-zones, edit resource record-sets (individually, atomically via transactions,
or in bulk via import/export), enable DNSSEC, and configure server policies and
response policies for forwarding, logging, and DNS overrides. Reach for it whenever
you need production-grade authoritative DNS hosting or VPC-internal name resolution
on Google Cloud.

## Quick reference — common workflows

### Create a public zone and add an A record

```bash
gcloud services enable dns.googleapis.com

# Create the public zone (the trailing dot on --dns-name is required)
gcloud dns managed-zones create my-zone \
    --dns-name=example.com. \
    --description="My public zone"

# Add an A record, then confirm
gcloud dns record-sets create www.example.com. \
    --type=A --ttl=300 --rrdatas=1.2.3.4 --zone=my-zone
gcloud dns record-sets list --zone=my-zone
```

After creation, look up the assigned name servers with `gcloud dns managed-zones
describe my-zone` and delegate your registrar to them.

### Atomic multi-record changes via a transaction

```bash
gcloud dns record-sets transaction start --zone=my-zone

gcloud dns record-sets transaction add "1.2.3.4" \
    --name=api.example.com. --ttl=300 --type=A --zone=my-zone

gcloud dns record-sets transaction add "api.example.com." \
    --name=www.example.com. --ttl=300 --type=CNAME --zone=my-zone

gcloud dns record-sets transaction describe --zone=my-zone   # inspect first
gcloud dns record-sets transaction execute --zone=my-zone    # commit
# (use 'transaction abort --zone=my-zone' to discard instead)
```

### Create a private zone for VPC-internal DNS

```bash
gcloud dns managed-zones create private-zone \
    --dns-name=internal.example.com. \
    --description="Internal VPC zone" \
    --visibility=private \
    --networks=my-vpc-network

gcloud dns record-sets create db.internal.example.com. \
    --type=A --ttl=60 --rrdatas=10.0.0.5 --zone=private-zone
```

### Enable DNSSEC and read the DS record

```bash
# Enable at creation time...
gcloud dns managed-zones create signed-zone \
    --dns-name=secure.example.com. \
    --description="DNSSEC-enabled zone" \
    --dnssec-state=on

# ...or turn it on for an existing zone
gcloud dns managed-zones update my-zone --dnssec-state=on

# Inspect keys; the DS record (give it to your registrar) comes from the KSK
gcloud dns dns-keys list --zone=my-zone \
    --filter='type=keySigning' --format='value(ds_record())'
```

### Configure a DNS server policy (inbound forwarding + query logging)

```bash
gcloud dns policies create my-policy \
    --description="Inbound forwarding with logging" \
    --networks=my-vpc-network \
    --enable-inbound-forwarding \
    --enable-logging

gcloud dns policies list
gcloud dns policies update my-policy \
    --alternative-name-servers=192.168.1.1
```

### Bulk import/export records

```bash
# Back up to YAML (default), or add --zone-file-format for BIND output
gcloud dns record-sets export records-backup.yaml --zone=my-zone

# Import a BIND zone file, replacing everything currently in the zone
gcloud dns record-sets import my-zone.db \
    --zone-file-format --delete-all-existing --zone=my-zone

# Review what changed
gcloud dns record-sets changes list --zone=my-zone
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `dns dns-keys` | [`dns-keys.md`](dns-keys.md) | 2 | View DNSKEY/DS records for DNSSEC-signed zones |
| `dns managed-zones` | [`managed-zones.md`](managed-zones.md) | 7 | Create/update/list/delete zones; manage zone IAM policy |
| `dns operations` | [`operations.md`](operations.md) | 2 | Describe and list long-running zone operations |
| `dns policies` | [`policies.md`](policies.md) | 5 | DNS server policies: inbound/outbound forwarding, logging |
| `dns project-info` | [`project-info.md`](project-info.md) | 1 | View per-project Cloud DNS quotas and info |
| `dns record-sets` | [`record-sets.md`](record-sets.md) | 15 | Manage records directly, by transaction, or via import/export; list changes |
| `dns response-policies` | [`response-policies.md`](response-policies.md) | 10 | Response policies and their rules for DNS overrides |

See [`index.md`](index.md) for a one-line index of all 42 commands.

## Common flags & tips

- **Trailing dot:** `--dns-name` and record-set DNS names are fully qualified — always
  end them with a dot (e.g. `example.com.`, `www.example.com.`).
- **`--zone` / `-z`:** required on every `record-sets` and `dns-keys` command. Set a
  default with `gcloud config set` is not supported here, so pass it each time.
- **`--rrdatas` is a list:** comma-separate multiple values, e.g.
  `--rrdatas=1.2.3.4,9.8.7.6`. On `record-sets create`/`update` you must supply either
  `--rrdatas` or a `--routing-policy-*` set (GEO/WRR/FAILOVER routing), not both.
- **Direct edits vs. transactions:** `record-sets create/update/delete` make one change
  at a time; use a `transaction` (start → add/remove → execute) when several records
  must change atomically. The transaction is staged locally in `transaction.yaml`
  (override with `--transaction-file`).
- **Visibility:** `--visibility=public` (default) or `--visibility=private`; private
  zones require `--networks` (and/or `--gkeclusters`).
- **DNSSEC:** `--dnssec-state` is one of `off`, `on`, `transfer`; algorithms/key lengths
  are tunable via `--ksk-algorithm`/`--ksk-key-length` and `--zsk-algorithm`/`--zsk-key-length`.
- **Zonal Cloud DNS:** the `--location` flag (e.g. `--location=us-east1-a`) targets the
  zonal service for GKE-scoped private zones; omit it for the global service.
- **Useful filters/formats:**
  - List a single name's records: `gcloud dns record-sets list --zone=my-zone --name="www.example.com." --type=A`
  - Get a key-signing DS record: `gcloud dns dns-keys list --zone=my-zone --filter='type=keySigning' --format='value(ds_record())'`
  - First N zones: `gcloud dns managed-zones list --limit=10`

## beta / alpha

`gcloud beta dns` and `gcloud alpha dns` expose the same seven subgroups as GA
(`dns-keys`, `managed-zones`, `operations`, `policies`, `project-info`, `record-sets`,
`response-policies`). No capability is known to be exclusively gated behind beta or
alpha; the `--location` flag for Zonal Cloud DNS is available on the GA commands above.
Use the beta/alpha tracks only if you need a preview behavior they document.

## Official documentation

- [Cloud DNS documentation home](https://cloud.google.com/dns/docs) — product overview and entry point to all guides.
- [DNS overview](https://cloud.google.com/dns/docs/dns-overview) — core concepts: zones, record types, DNSSEC, server roles.
- [Quickstart](https://cloud.google.com/dns/docs/quickstart) — create a managed zone and add A/CNAME records.
- [Managing zones](https://cloud.google.com/dns/docs/zones) — create, update, list, and delete public and private zones.
- [Managing records](https://cloud.google.com/dns/docs/records) — add, update, delete, import, and export record-sets.
- [DNSSEC](https://cloud.google.com/dns/docs/dnssec) — enable and manage DNSSEC to authenticate responses.
- [DNS server policies](https://cloud.google.com/dns/docs/policies-overview) — inbound/outbound forwarding and query logging on VPC networks.
- [Access control (IAM)](https://cloud.google.com/dns/docs/access-control) — roles such as `roles/dns.admin`, `roles/dns.reader`, `roles/dns.peer`.
- [gcloud dns CLI reference](https://cloud.google.com/sdk/gcloud/reference/dns) — full command and flag reference.

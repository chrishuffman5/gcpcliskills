# gcloud network-security — Network Security (Cloud NGFW)

## Overview

`gcloud network-security` manages the resources behind **Cloud Next Generation Firewall (Cloud NGFW)** and the broader Network Security API (`networksecurity.googleapis.com`). Reach for it to deploy zonal **firewall endpoints** (Firewall Plus) for Layer 7 inspection, author **security profiles / profile groups** (threat prevention, custom intercept/mirroring) consumed by firewall policies, manage **TLS inspection policies**, and maintain reusable **address groups** and **URL lists**. It also covers packet **intercept/mirroring** deployment resources and service-mesh mTLS policies (client/server TLS, authorization, and authz policies).

## Quick reference — common workflows

### Enable the API
```bash
gcloud services enable networksecurity.googleapis.com
```

### 1. Create a Firewall Plus endpoint (org-scoped) and associate a VPC
```bash
# Endpoints are zonal and org-scoped; --billing-project is required.
gcloud network-security firewall-endpoints create my-endpoint \
    --zone=us-central1-a \
    --organization=ORGANIZATION_ID \
    --billing-project=PROJECT_ID

# Check progress (endpoint reaches READY).
gcloud network-security firewall-endpoints list \
    --organization=ORGANIZATION_ID --zone=us-central1-a

# Associate a VPC network with the endpoint (enables L7 inspection for that network).
gcloud network-security firewall-endpoint-associations create \
    --network=projects/PROJECT_ID/global/networks/NETWORK_NAME \
    --endpoint=organizations/ORGANIZATION_ID/locations/us-central1-a/firewallEndpoints/my-endpoint \
    --zone=us-central1-a \
    --project=PROJECT_ID

gcloud network-security firewall-endpoint-associations list \
    --zone=us-central1-a --project=PROJECT_ID
```

### 2. Build a threat-prevention security profile and profile group
```bash
# 1. Create the threat-prevention profile (org-scoped, global location).
gcloud network-security security-profiles threat-prevention create my-security-profile \
    --organization=ORGANIZATION_ID --location=global \
    --description="Threat prevention profile"

# 2. Add a severity override (alert on HIGH-severity threats).
gcloud network-security security-profiles threat-prevention add-override my-security-profile \
    --organization=ORGANIZATION_ID --location=global \
    --severities=HIGH --action=ALERT

# 3. Wrap it in a profile group (referenced by firewall policy rules).
gcloud network-security security-profile-groups create my-spg \
    --organization=ORGANIZATION_ID --location=global \
    --threat-prevention-profile=organizations/ORGANIZATION_ID/locations/global/securityProfiles/my-security-profile \
    --description="Prod threat prevention group"

gcloud network-security security-profile-groups describe my-spg \
    --organization=ORGANIZATION_ID --location=global
```

### 3. Manage an address group
```bash
# Create a project-level IPv4 address group with capacity 100.
gcloud network-security address-groups create my-address-group \
    --location=global --type=ipv4 --capacity=100 \
    --description="Trusted CIDR ranges"

gcloud network-security address-groups add-items my-address-group \
    --location=global --items=192.168.1.0/24,10.0.0.0/8

gcloud network-security address-groups list --location=global

gcloud network-security address-groups remove-items my-address-group \
    --location=global --items=192.168.1.0/24
```

### 4. Export / import a TLS inspection policy and attach it
```bash
# Export to YAML (edit offline), then re-import to create or update.
gcloud network-security tls-inspection-policies export my-tls-policy \
    --location=us-central1 --destination=my-tls-policy.yaml

gcloud network-security tls-inspection-policies import my-tls-policy \
    --location=us-central1 --source=my-tls-policy.yaml

# Attach the policy to a firewall endpoint association.
gcloud network-security firewall-endpoint-associations update my-assoc \
    --zone=us-central1-a --project=PROJECT_ID \
    --tls-inspection-policy=my-tls-policy \
    --tls-inspection-policy-region=us-central1

gcloud network-security tls-inspection-policies list --location=us-central1
```

### 5. Inspect and adjust threat-prevention overrides
```bash
# List current overrides on a profile.
gcloud network-security security-profiles threat-prevention list-overrides \
    my-security-profile --organization=ORGANIZATION_ID --location=global

# Change the action for MEDIUM-severity threats.
gcloud network-security security-profiles threat-prevention update-override my-security-profile \
    --organization=ORGANIZATION_ID --location=global \
    --severities=MEDIUM --action=DENY

# Revert (delete) the MEDIUM override.
gcloud network-security security-profiles threat-prevention delete-override my-security-profile \
    --organization=ORGANIZATION_ID --location=global \
    --severities=MEDIUM
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `network-security address-groups` | [`address-groups.md`](address-groups.md) | 9 | manage Network Security AddressGroups |
| `network-security authorization-policies` | [`authorization-policies.md`](authorization-policies.md) | 4 | manage Network Security AuthorizationPolicies |
| `network-security authz-policies` | [`authz-policies.md`](authz-policies.md) | 4 | manage Network Security AuthzPolicy resources |
| `network-security backend-authentication-configs` | [`backend-authentication-configs.md`](backend-authentication-configs.md) | 6 | manage Network Security BackendAuthenticationConfigs |
| `network-security client-tls-policies` | [`client-tls-policies.md`](client-tls-policies.md) | 4 | manage Network Security ClientTlsPolicies |
| `network-security dns-threat-detectors` | [`dns-threat-detectors.md`](dns-threat-detectors.md) | 5 | manage Dns Threat Detector resources |
| `network-security firewall-endpoint-associations` | [`firewall-endpoint-associations.md`](firewall-endpoint-associations.md) | 5 | create and manage Firewall Plus endpoint associations |
| `network-security firewall-endpoints` | [`firewall-endpoints.md`](firewall-endpoints.md) | 5 | create and manage Firewall Plus endpoints |
| `network-security gateway-security-policies` | [`gateway-security-policies.md`](gateway-security-policies.md) | 8 | manage Network Security Gateway Security Policies |
| `network-security intercept-deployment-groups` | [`intercept-deployment-groups.md`](intercept-deployment-groups.md) | 5 | manage Intercept Deployment Group resources |
| `network-security intercept-deployments` | [`intercept-deployments.md`](intercept-deployments.md) | 5 | manage Intercept Deployment resources |
| `network-security intercept-endpoint-group-associations` | [`intercept-endpoint-group-associations.md`](intercept-endpoint-group-associations.md) | 5 | manage Intercept Endpoint Group Association resources |
| `network-security intercept-endpoint-groups` | [`intercept-endpoint-groups.md`](intercept-endpoint-groups.md) | 5 | manage Intercept Endpoint Group resources |
| `network-security mirroring-deployment-groups` | [`mirroring-deployment-groups.md`](mirroring-deployment-groups.md) | 5 | manage Mirroring Deployment Group resources |
| `network-security mirroring-deployments` | [`mirroring-deployments.md`](mirroring-deployments.md) | 5 | manage Mirroring Deployment resources |
| `network-security mirroring-endpoint-group-associations` | [`mirroring-endpoint-group-associations.md`](mirroring-endpoint-group-associations.md) | 5 | manage Mirroring Endpoint Group Association resources |
| `network-security mirroring-endpoint-groups` | [`mirroring-endpoint-groups.md`](mirroring-endpoint-groups.md) | 5 | manage Mirroring Endpoint Group resources |
| `network-security org-address-groups` | [`org-address-groups.md`](org-address-groups.md) | 9 | manage Network Security AddressGroups (org-scoped) |
| `network-security security-profile-groups` | [`security-profile-groups.md`](security-profile-groups.md) | 5 | manage Network Security - Security Profile Groups |
| `network-security security-profiles` | [`security-profiles.md`](security-profiles.md) | 17 | manage Network Security - Security Profiles |
| `network-security server-tls-policies` | [`server-tls-policies.md`](server-tls-policies.md) | 5 | manage Network Security ServerTlsPolicies |
| `network-security tls-inspection-policies` | [`tls-inspection-policies.md`](tls-inspection-policies.md) | 4 | manage Network Security TLS Inspection Policies |
| `network-security url-lists` | [`url-lists.md`](url-lists.md) | 4 | manage Network Security Url Lists |

See [`index.md`](index.md) for a one-line index of all 134 GA commands.

## Common flags & tips

- **Scoping (org vs project):** Firewall endpoints and security profiles/profile groups are **organization-scoped** — pass `--organization=ORGANIZATION_ID`. Address groups, URL lists, TLS inspection policies, and firewall endpoint associations are **project-scoped** (`--project`, or rely on `core/project`).
- **Location is required and varies by resource:** security profiles and profile groups use `--location=global`; address groups use `--location=global`; TLS inspection policies are **regional** (`--location=us-central1`); firewall endpoints/associations are **zonal** (`--zone=us-central1-a`).
- **Firewall endpoints need a billing project:** `firewall-endpoints create` requires `--billing-project`; `firewall-endpoints update` uses `--update-billing-project`.
- **Endpoint creation is async by default:** `create`/`delete`/`update` default to `--async` (use `--no-async` to block, with `--max-wait` controlling the synchronous wait, default `60m`). Poll readiness with the matching `list`/`describe`.
- **Address group type / purpose:** `--type` must be `ipv4` or `ipv6`; `--purpose` is one of `cloud-armor` or `default`. Manage membership with `add-items` / `remove-items` / `clone-items` (`--items=...`), and find consumers with `list-references`.
- **Threat-prevention overrides:** `add-override` / `update-override` take `--action` (`DEFAULT_ACTION`, `ALLOW`, `ALERT`, `DENY`) plus exactly one of `--antivirus`, `--severities`, or `--threat-ids`; `delete-override` omits `--action`.
- **TLS inspection policies use export/import**, not a `create` verb — round-trip YAML via `export --destination=...` and `import --source=...`.
- **Labels:** `create` accepts `--labels`; update verbs use `--update-labels`, `--remove-labels`, and `--clear-labels`.
- **Format / filter examples:**
  ```bash
  gcloud network-security firewall-endpoints list --organization=ORGANIZATION_ID \
      --zone=us-central1-a --format="table(name, state)"
  gcloud network-security address-groups list --location=global \
      --filter="type=IPV4" --format="value(name)"
  gcloud network-security security-profile-groups describe my-spg \
      --organization=ORGANIZATION_ID --location=global --format=yaml
  ```

## beta / alpha

`gcloud beta network-security` and `gcloud alpha network-security` expose the same subgroup set as GA; individual commands surface there when the underlying feature is in Preview. Capabilities that commonly require beta/alpha:

- **Project-level firewall endpoints** (vs. org-scoped) — use `gcloud beta network-security firewall-endpoints ...`.
- **`security-profiles custom-intercept` / `custom-mirroring`** profiles and the **`intercept-*` / `mirroring-*`** packet intercept/mirroring resources — check region availability; some operations are Preview.
- **`dns-threat-detectors`** — DNS threat detection may have limited regional GA coverage.

Prefer the beta/alpha track for any operation whose `cloud.google.com/sdk/gcloud/reference/beta/...` page shows the beta qualifier, until GA is confirmed in your region.

## Official documentation

- [Cloud NGFW product docs](https://cloud.google.com/firewall/docs) — guides, quickstarts, and API reference home.
- [About firewall endpoints](https://cloud.google.com/firewall/docs/about-firewall-endpoints) — zonal Firewall Plus endpoints and L7 inspection.
- [Security profiles](https://cloud.google.com/firewall/docs/security-profiles) — threat-prevention and custom profiles used by firewall policies.
- [Configure security profiles](https://cloud.google.com/firewall/docs/configure-security-profiles) — how-to for threat-prevention profiles (roles, APIs, gcloud).
- [Advanced threat protection](https://cloud.google.com/firewall/docs/about-advanced-threat-protection) — IDS/IPS, antivirus, and threat intelligence overview.
- [TLS inspection overview](https://cloud.google.com/firewall/docs/tls-inspection-overview) — decrypting/re-encrypting traffic for deep inspection.
- [Address groups overview](https://cloud.google.com/armor/docs/address-groups-overview) — reusable IP/CIDR collections shared with Cloud Armor.
- [gcloud network-security CLI reference](https://cloud.google.com/sdk/gcloud/reference/network-security) — full command and flag reference.

---
name: gcloud-recaptcha
description: >-
  reCAPTCHA Enterprise via gcloud (`gcloud recaptcha`). Manage reCAPTCHA Enterprise Keys — firewall-policies, keys.
---

# gcloud recaptcha — reCAPTCHA Enterprise

## Overview
`gcloud recaptcha` manages the **keys** and **firewall policies** that power reCAPTCHA Enterprise — Google Cloud's AI-driven fraud and abuse prevention platform that scores traffic to protect websites and mobile apps against bots, account takeover, credential stuffing, and other automated threats. Reach for it to provision the site keys you embed in web pages and mobile apps (score-based, checkbox, or challenge integrations), to manage IP allowlist overrides on those keys, and to define WAF firewall policies that act on reCAPTCHA scores (allow / block / substitute / set-header). Assessment verification and metrics live in the API/Console, not in this CLI group.

## Quick reference — common workflows

### 1. Enable the API, then create a score-based web key
A score key returns a risk score with no visible CAPTCHA challenge.
```bash
gcloud services enable recaptchaenterprise.googleapis.com

gcloud recaptcha keys create \
    --display-name=my-web-key \
    --web \
    --domains=example.com \
    --integration-type=score
```

### 2. Create mobile keys for Android and iOS
```bash
# Android
gcloud recaptcha keys create \
    --display-name=my-android-key \
    --android \
    --package-names=com.example.myapp

# iOS
gcloud recaptcha keys create \
    --display-name=my-ios-key \
    --ios \
    --bundle-ids=com.example.myapp
```

### 3. Inspect and update a key
```bash
# List all keys, then look at one in detail
gcloud recaptcha keys list
gcloud recaptcha keys describe KEY_ID

# Rename, add a label, and re-scope the allowed domain
gcloud recaptcha keys update KEY_ID \
    --display-name=updated-key \
    --labels="env=prod" \
    --web \
    --domains=newdomain.com
```

### 4. Manage IP overrides on a key
Allowlist trusted IPs (e.g. internal test hosts) so their traffic is exempted.
```bash
# Add an allow override
gcloud recaptcha keys add-ip-override KEY_ID --ip=1.2.3.4 --override=allow

# List the overrides currently on the key
gcloud recaptcha keys list-ip-overrides KEY_ID

# Remove the override
gcloud recaptcha keys remove-ip-override KEY_ID --ip=1.2.3.4 --override=allow
```

### 5. Create and order WAF firewall policies
Policies use a CEL condition + glob path; order determines evaluation priority.
```bash
# Allow high-score traffic on /login/ and stamp a header
gcloud recaptcha firewall-policies create \
    --path='/login/*' \
    --condition='recaptcha.score >= 0.5' \
    --actions=allow,set_header=foo=bar

# Block low-score traffic with an existing policy
gcloud recaptcha firewall-policies update POLICY_ID \
    --condition='recaptcha.score < 0.3' \
    --actions=block

# Set the evaluation order across all policies
gcloud recaptcha firewall-policies reorder \
    --names=policy-id-1,policy-id-2,policy-id-3
```

### 6. Migrate a legacy reCAPTCHA key to Enterprise
```bash
gcloud recaptcha keys migrate KEY_ID
# If usage is under the free quota, skip the billing check:
gcloud recaptcha keys migrate KEY_ID --skip-billing-check
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `recaptcha firewall-policies` | [`firewall-policies.md`](firewall-policies.md) | 6 | Managed reCAPTCHA Firewall Policies |
| `recaptcha keys` | [`keys.md`](keys.md) | 9 | Managed reCAPTCHA Keys |

See [`index.md`](index.md) for a one-line index of all 15 commands.

## Common flags & tips
- **Key platform is exclusive.** On `keys create` / `keys update` you pick exactly one of `--web`, `--android`, `--ios`, or `--express`. Web keys take `--domains=[...]` or `--allow-all-domains`; Android keys take `--package-names=[...]` or `--allow-all-package-names`; iOS keys take `--bundle-ids=[...]` or `--allow-all-bundle-ids`.
- **Web integration type.** `--integration-type=score` (verified in the reference) yields an invisible score key. Optional web tuning flags include `--default-score-threshold`, `--action-score-thresholds`, `--security-preference`, `--allow-amp-traffic`, and `--testing-challenge`.
- **Testing.** `--testing-score=0..1` forces a fixed score for every assessment (handy for QA on web keys).
- **Labels** use `--labels=KEY=VALUE,...`; keys/values must be lowercase letters, numbers, hyphens, and underscores.
- **IP overrides** require both `--ip` and `--override`; `--override` is one of `allow` or `override-type-unspecified`.
- **Firewall policy actions** allow at most one terminal action (allow / block / substitute) plus non-terminal actions like `set_header=key=value`, e.g. `--actions=block,set_header=foo=bar` or `--actions=substitute=google.com`. The `--condition` is a CEL expression and `--path` is a glob pattern.
- **List filtering / formatting** — `keys list` and `firewall-policies list` support `--filter`, `--limit`, `--sort-by`, `--page-size`, and `--uri`. Examples:
  ```bash
  gcloud recaptcha keys list --filter="displayName:web" --format="table(name, displayName)"
  gcloud recaptcha keys list --uri
  ```
- **Resource naming.** Pass the bare key/policy ID (e.g. `test-key`, `policy-id`) or a fully qualified resource name; project is taken from `--project` or the `core/project` property. reCAPTCHA Enterprise keys/policies are global — no `--region`/`--zone`.
- **IAM roles:** `roles/recaptchaenterprise.admin` (full), `.editor`, `.viewer` (read-only), and `.agent` (assessments + list policies).

## beta / alpha
- `gcloud alpha recaptcha keys` and `gcloud alpha recaptcha firewall-policies` mirror the GA subgroups (same 9 + 6 commands). Alpha may expose unreleased flag options — run `--help` on the alpha command to spot differences.
- No `gcloud beta recaptcha` track exists; only GA and alpha are available.

## Official documentation
- [reCAPTCHA Enterprise overview](https://cloud.google.com/recaptcha/docs/overview) — product docs home: capabilities, key types, and platform support.
- [Quickstart](https://cloud.google.com/recaptcha/docs/quickstart) — deploy a demo site; covers API-enable and IAM prerequisites.
- [reCAPTCHA keys](https://cloud.google.com/recaptcha/docs/keys) — key concepts: site-key strings and platform types (web, Android, iOS, WAF, API).
- [Create keys for websites](https://cloud.google.com/recaptcha/docs/create-key-website) — score, checkbox, and policy-based-challenge integration types.
- [Create keys for mobile apps](https://cloud.google.com/recaptcha/docs/create-key-mobile) — Android (`--android --package-names`) and iOS (`--ios --bundle-ids`).
- [WAF features](https://cloud.google.com/recaptcha/docs/waf-features) — Cloud Armor action-tokens, session-tokens, and challenge-page integration.
- [Access control with IAM](https://cloud.google.com/recaptcha/docs/access-control) — the four predefined reCAPTCHA Enterprise roles.
- [gcloud recaptcha CLI reference](https://cloud.google.com/sdk/gcloud/reference/recaptcha) — full command/flag reference for `keys` and `firewall-policies`.

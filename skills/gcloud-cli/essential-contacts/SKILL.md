---
name: gcloud-essential-contacts
description: >-
  Essential Contacts via gcloud (`gcloud essential-contacts`). Manage Essential Contacts.
---

# gcloud essential-contacts — Essential Contacts

## Overview
Essential Contacts (part of Resource Manager) lets you designate the people who
should receive important Google Cloud notifications — billing, legal, security,
suspension, technical, and product-update communications — for a project,
folder, or organization. Each contact is subscribed to one or more
*notification categories*, and contacts set on a parent resource are inherited
down the hierarchy. Reach for this group when you want notifications routed to a
curated directory of recipients instead of relying on default role-based
fall-backs.

## Quick reference — common workflows

### 1. Enable the API
```bash
gcloud services enable essentialcontacts.googleapis.com
```

### 2. Create a contact on the current project
```bash
# Subscribe a team to technical + product-update notices (all three flags are required)
gcloud essential-contacts create \
    --email=contact-email@example.com \
    --notification-categories=technical,product-updates \
    --language=en-US
```

### 3. Create an organization-level contact (inherited by folders/projects)
```bash
gcloud essential-contacts create \
    --email=legal@example.com \
    --notification-categories=legal \
    --language=en-US \
    --organization=456
```

### 4. List and inspect contacts on a resource
```bash
# Contacts directly set on the current project
gcloud essential-contacts list

# Contacts set on a specific folder
gcloud essential-contacts list --folder=456

# Full details for one contact by id
gcloud essential-contacts describe 123
```

### 5. Compute effective contacts for a notification category
```bash
# Who (including inherited contacts) receives technical notices on this project?
gcloud essential-contacts compute \
    --notification-categories=technical

# For a folder, across two categories
gcloud essential-contacts compute \
    --notification-categories=product-updates,billing --folder=123

# For an organization
gcloud essential-contacts compute \
    --notification-categories=legal --organization=456
```

### 6. Update or delete a contact
```bash
# Change category subscriptions for contact 123 in the current project
gcloud essential-contacts update 123 \
    --notification-categories=legal,suspension

# Change the language preference for a contact in a folder
gcloud essential-contacts update 123 --language=es --folder=456

# Delete contact 123 from an organization
gcloud essential-contacts delete 123 --organization=456
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| essential-contacts (top-level) | [`_commands.md`](_commands.md) | 6 | Manage Essential Contacts directly — `compute`, `create`, `delete`, `describe`, `list`, `update`. |

See [`index.md`](index.md) for the one-line index of all 6 commands.

## Common flags & tips

- **Resource selector** — every command targets exactly one resource via at most
  one of `--project`, `--folder`, or `--organization`. If none is supplied, the
  `core/project` config property is used. Folders and organizations are
  identified by number (e.g. `--folder=456`, `--organization=456`); projects
  accept a project id or number.
- **`--notification-categories`** must be drawn from: `all`, `billing`, `legal`,
  `notification-category-unspecified`, `product-updates`, `security`,
  `suspension`, `technical`, `technical-incidents`. Pass several as a
  comma-separated list (e.g. `--notification-categories=technical,security`).
- **`create` requires all three of** `--email`, `--language`, and
  `--notification-categories`. `--language` must be a valid ISO 639-1 code
  (e.g. `en-US`, `es`).
- **`compute` vs `list`** — `list` returns only contacts set directly on the
  named resource, while `compute --notification-categories=...` returns the
  *effective* set, including contacts inherited from ancestor resources.
- **Contact id** — `delete`, `describe`, and `update` take the numeric
  `CONTACT_ID` as a positional argument; find it via `gcloud essential-contacts list`.
- **`list` paging/filtering** — `list` and `compute` support the standard
  `--filter`, `--limit`, `--page-size`, and `--sort-by` flags. Example:
  `gcloud essential-contacts list --filter="notificationCategorySubscriptions:SECURITY"`.
- **IAM** — `roles/essentialcontacts.admin` grants full management;
  `roles/essentialcontacts.viewer` grants read-only (`describe`/`list`).

## beta / alpha
Both `gcloud beta essential-contacts` and `gcloud alpha essential-contacts`
expose the same six subcommands as GA (`compute`, `create`, `delete`,
`describe`, `list`, `update`) with no additional flags or commands documented.
They "might change without notice"; use the GA `gcloud essential-contacts`
group for production workloads.

## Official documentation

- [Managing notification contacts](https://cloud.google.com/resource-manager/docs/managing-notification-contacts) — product home: notification categories, best practices, and resource-hierarchy inheritance.
- [gcloud essential-contacts reference](https://cloud.google.com/sdk/gcloud/reference/essential-contacts) — full CLI reference for all 6 GA commands.
- [IAM roles for Essential Contacts](https://cloud.google.com/iam/docs/roles-permissions/essentialcontacts) — predefined roles and granular permissions.
- [gcloud beta essential-contacts](https://cloud.google.com/sdk/gcloud/reference/beta/essential-contacts) / [gcloud alpha essential-contacts](https://cloud.google.com/sdk/gcloud/reference/alpha/essential-contacts) — pre-release command variants.

---
name: gcloud-identity
description: >-
  Cloud Identity via gcloud (`gcloud identity`). Manage Cloud Identity Groups and Memberships resources.
---

# gcloud identity — Cloud Identity

## Overview
`gcloud identity` manages **Cloud Identity Groups and Memberships** — the groups (discussion, security, dynamic, POSIX, identity-mapped) and member relationships that Cloud Identity, Google Workspace, and IAM use to organize users and govern access. Reach for it to create and update groups, add/remove members and roles, and analyze direct or transitive membership across nested groups. Note that group/membership management is governed largely by Google Workspace admin roles rather than Google Cloud IAM.

## Quick reference — common workflows

### 1. Enable the API and create a discussion group
```bash
gcloud services enable cloudidentity.googleapis.com

# A standard Google Groups discussion group (the default --group-type)
gcloud identity groups create eng-discuss@example.com \
    --organization="example.com" \
    --display-name="Engineering Discussion" \
    --description="Group for engineering team discussions"
```

### 2. Create a security group (for IAM access control)
```bash
gcloud identity groups create sec-group@example.com \
    --organization="example.com" \
    --group-type="security" \
    --display-name="Security Group" \
    --description="Access control group for production resources"
```

### 3. Add members and manage membership roles
```bash
# Add a user as a regular member (MEMBER is the default role)
gcloud identity groups memberships add \
    --group-email="eng-discuss@example.com" \
    --member-email="alice@example.com"

# Promote the member to OWNER
gcloud identity groups memberships modify-membership-roles \
    --group-email="eng-discuss@example.com" \
    --member-email="alice@example.com" \
    --add-roles=OWNER

# List all members of the group with full detail
gcloud identity groups memberships list \
    --group-email="eng-discuss@example.com" \
    --view=full --limit=50
```

### 4. Search groups and inspect a membership graph
```bash
# Search all discussion-forum groups in an org
gcloud identity groups search \
    --organization="example.com" \
    --labels="cloudidentity.googleapis.com/groups.discussion_forum" \
    --page-size=50

# Get the membership graph for a member
gcloud identity groups memberships get-membership-graph \
    --member-email="alice@example.com" \
    --labels=cloudidentity.googleapis.com/groups.discussion_forum
```

### 5. Explore transitive (nested) memberships
```bash
# Is a user transitively a member of a group (via nested groups)?
gcloud identity groups memberships check-transitive-membership \
    --group-email="eng@example.com" \
    --member-email="alice@example.com"

# Search all transitive groups a member belongs to
gcloud identity groups memberships search-transitive-groups \
    --labels=cloudidentity.googleapis.com/groups.discussion_forum \
    --member-email="alice@example.com" --page-size=50

# Search all (flattened) transitive memberships of a group
gcloud identity groups memberships search-transitive-memberships \
    --group-email="eng@example.com" --page-size=50
```

### 6. Update and tear down a group
```bash
# Update display name and description
gcloud identity groups update eng-discuss@example.com \
    --display-name="Engineering Discuss (Updated)" \
    --description="Renamed discussion group"

# Remove a member, then delete the group
gcloud identity groups memberships delete \
    --group-email="eng-discuss@example.com" \
    --member-email="alice@example.com"

gcloud identity groups delete eng-discuss@example.com
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `identity groups` | [`groups.md`](groups.md) | 14 | Manage Cloud Identity Groups and their memberships (create, delete, describe, search, update; plus the `memberships` subcommands: add, delete, describe, list, modify-membership-roles, check-transitive-membership, get-membership-graph, search-transitive-groups, search-transitive-memberships) |

See [`index.md`](index.md) for a one-line index of all 14 commands.

## Common flags & tips
- **Group identity:** groups are addressed by their **EMAIL** (a positional arg on `create`/`delete`/`describe`/`update`/`search`). Membership commands instead use `--group-email` and `--member-email`.
- **Customer vs organization:** `create` and `search` require exactly one of `--customer` (G Suite customer ID, e.g. `C01k1e9nw`) or `--organization` (numeric org ID `"123456789"` or domain `"example.com"`).
- **Group types via labels:** `--group-type` accepts `discussion` (default) or `security`. The richer group taxonomy is expressed as label keys used by `search`, `get-membership-graph`, and `search-transitive-groups`:
  - `cloudidentity.googleapis.com/groups.discussion_forum` — standard Google Group
  - `cloudidentity.googleapis.com/groups.security` — security group (immutable once added)
  - `cloudidentity.googleapis.com/groups.posix` — POSIX group
  - `cloudidentity.googleapis.com/groups.dynamic` — dynamic group
  - `system/groups/external` — identity-mapped group (Cloud Search)
- **Dynamic groups:** supply `--dynamic-user-query` (CEL), e.g. `--dynamic-user-query="user.organizations.exists(org,org.title=='SWE')"`, on `create`/`update`.
- **Roles:** membership roles are `MEMBER` (default on `add`), `OWNER`, `MANAGER`. Use `--add-roles` / `--remove-roles` (or `--update-roles-params`) on `modify-membership-roles`. A MEMBER-less owner is not supported.
- **Membership expiry:** `memberships add --expiration` takes a duration from now, e.g. `30d`, `6m`, `3y`.
- **Views & paging:** `search` and `memberships list` support `--view=basic|full` (default `basic`) and token-based paging via `--page-size`/`--page-token`. `memberships list` also supports the standard `--filter`, `--limit`, and `--sort-by`.
- **Formatting examples:**
  ```bash
  # Just the member emails and roles
  gcloud identity groups memberships list --group-email="eng-discuss@example.com" \
      --view=full --format="table(preferredMemberKey.id, roles[].name)"

  # Group display names from a search
  gcloud identity groups search --organization="example.com" \
      --labels="cloudidentity.googleapis.com/groups.discussion_forum" \
      --format="value(displayName)"
  ```

## beta / alpha
`gcloud beta identity` and `gcloud alpha identity` mirror the GA `groups` structure with extra capabilities:
- **`gcloud beta identity groups preview`** (beta-only) — list users in a customer account via a CEL `--query` (required `--customer`; optional `--query`, `--projection`, `--max-results`, `--page-token`, `--view-type`). Useful as a pre-flight check before creating a dynamic group.
- **`gcloud alpha identity groups config`** (alpha-only subgroup) — manage Cloud Identity group configurations.
- **`gcloud alpha identity groups preview`** — same as the beta `preview` command.

For stable production use, the 14 GA commands cover the full group and membership lifecycle.

## Official documentation
- [Cloud Identity overview](https://cloud.google.com/identity/docs/overview) — IDaaS product overview: user/group management and federation.
- [Cloud Identity Groups](https://cloud.google.com/identity/docs/groups) — group types (discussion, security, dynamic, POSIX, identity-mapped) and membership roles.
- [Set up the Groups API](https://cloud.google.com/identity/docs/how-to/setup) — prerequisites and domain setup for the Cloud Identity Groups API.
- [Cloud Identity REST reference](https://cloud.google.com/identity/docs/reference/rest) — REST API home (v1 and v1beta1).
- [groups REST resource](https://cloud.google.com/identity/docs/reference/rest/v1/groups) — create, delete, get, list, lookup, patch, search, and security-settings methods.
- [gcloud identity CLI reference](https://cloud.google.com/sdk/gcloud/reference/identity) — the GA command group documented here.
- [gcloud beta identity CLI reference](https://cloud.google.com/sdk/gcloud/reference/beta/identity) — beta surface, including the `preview` command.

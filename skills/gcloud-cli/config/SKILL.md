---
name: gcloud-config
description: >-
  CLI properties & configurations via gcloud (`gcloud config`). View and edit Google Cloud CLI properties — configurations.
---

# gcloud config — CLI properties & configurations

## Overview

`gcloud config` manages the gcloud CLI itself, not a Google Cloud product. It reads and writes the *properties* that control gcloud's behavior — the default project, account, Compute Engine region/zone, log verbosity, proxy settings, prompt suppression, and more — and organizes them into named *configurations* you can switch between. Reach for it to set your defaults once (so you stop passing `--project` on every command), to keep separate property sets for different projects or environments, or to tune gcloud for scripting and CI.

Everything here is client-side: it operates on local files under `~/.config/gcloud` (Linux/macOS) or `%APPDATA%\gcloud` (Windows). There is no API to enable and no IAM role required to set or read these properties.

## Quick reference — common workflows

### 1. Initial project / region / zone setup

```bash
# Set the default project (core section — section prefix optional)
gcloud config set project PROJECT_ID

# Set the default Compute Engine region and zone
gcloud config set compute/region us-central1
gcloud config set compute/zone us-central1-a

# Confirm what is set in the active configuration
gcloud config list
```

### 2. Read or list individual properties

```bash
# Print one property's value (core/ prefix optional)
gcloud config get project
gcloud config get compute/zone

# List the whole compute section, including unset properties
gcloud config list compute/ --all
```

### 3. Create and switch between named configurations (multi-project)

```bash
# Create a new configuration (activated automatically; use --no-activate to keep current)
gcloud config configurations create staging

# Set properties — they apply to the now-active "staging" configuration
gcloud config set project staging-project-456
gcloud config set compute/region europe-west1

# Inspect a configuration without activating it
gcloud config configurations describe staging

# Switch back to another configuration
gcloud config configurations activate default

# See all configurations and which one is active
gcloud config configurations list
```

### 4. Run a single command under a different configuration

```bash
# --configuration is a gcloud-wide flag, not a config subcommand;
# it overrides the active configuration for just this invocation
gcloud config list --configuration=staging
```

### 5. Unset properties (active config vs. installation-wide)

```bash
# Remove a property from the active configuration
gcloud config unset compute/zone

# Remove a property across the entire installation (all configurations)
gcloud config unset compute/region --installation
```

### 6. Rename and delete configurations

```bash
# Rename a configuration
gcloud config configurations rename staging --new-name=staging-eu

# You cannot delete the active configuration — activate another first
gcloud config configurations activate default

# Delete one, or several at once
gcloud config configurations delete staging-eu
gcloud config configurations delete old-config1 old-config2
```

### 7. Tune gcloud for scripting / CI

```bash
# Suppress interactive prompts (essential in non-interactive pipelines)
gcloud config set disable_prompts true

# Route gcloud through an HTTP proxy
gcloud config set proxy/type http
gcloud config set proxy/address 1.234.56.78
gcloud config set proxy/port 8080

# Apply a default to the whole installation rather than one configuration
gcloud config set compute/region us-central1 --installation
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `config` (top level) | [`_commands.md`](_commands.md) | 4 | `get`, `list`, `set`, `unset` — read and edit individual properties |
| `config configurations` | [`configurations.md`](configurations.md) | 6 | manage the set of gcloud named configurations |

See [`index.md`](index.md) for a one-line index of all 10 commands.

## Common flags & tips

- **`SECTION/PROPERTY` syntax** — properties are namespaced by section (`compute/region`, `proxy/port`). The `core/` prefix is optional, so `project` and `core/project` are equivalent; other sections must be named explicitly.
- **`--installation`** (on `set` and `unset`) — writes to the installation-wide config that backs *every* configuration, instead of only the active one. Use it for machine-wide defaults; per-configuration values still override it.
- **`--all`** (on `list` and `configurations describe`) — includes unset properties. With `list` you may combine `--all` only with a section, e.g. `gcloud config list compute/ --all`; you cannot pass both `--all` and a specific property name.
- **`--configuration=NAME`** — a gcloud-wide flag (works on any gcloud command) that runs under a named configuration for that single invocation without activating it.
- **Can't delete the active config** — `configurations delete` refuses the active configuration even when overridden with `--configuration`; activate another one first. `delete` accepts multiple names.
- **`configurations create` activates by default** — pass `--no-activate` to create without switching.
- **`configurations rename` requires `--new-name`** — e.g. `--new-name=new-config`.
- **Filtering/sorting lists** — `gcloud config configurations list` and `gcloud config list` support `--filter`, `--limit`, and `--sort-by`, plus the usual gcloud-wide `--format` (e.g. `--format="value(name)"`).
- **Cloud Shell caveat** — in Cloud Shell, gcloud preferences live in a temporary per-tab folder and do not persist across sessions unless you configure persistence.

## Official documentation

- **Cloud SDK docs home** — https://cloud.google.com/sdk/docs — top-level documentation for the gcloud CLI and Cloud SDK.
- **Managing configurations** — https://cloud.google.com/sdk/docs/configurations — concepts and how-to for creating, activating, switching, and deleting named configurations.
- **Properties reference** — https://cloud.google.com/sdk/docs/properties — all property sections (core, compute, auth, storage, …) and the precedence rules for how values are resolved.
- **`gcloud topic configurations`** — https://cloud.google.com/sdk/gcloud/reference/topic/configurations — detailed topic page covering all property sections, `CLOUDSDK_*` environment variables, and config file locations.
- **gcloud config reference** — https://cloud.google.com/sdk/gcloud/reference/config — the CLI reference landing page for this command group.

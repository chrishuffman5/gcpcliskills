---
name: gcloud-components
description: >-
  Google Cloud CLI component manager via gcloud (`gcloud components`). List, install, update, or remove Google Cloud CLI components — repositories.
---

# gcloud components — Google Cloud CLI component manager

## Overview
`gcloud components` manages the Google Cloud CLI's own component system — the installable parts of the CLI itself, such as the `gcloud`, `bq`, and `gsutil` tools, the `alpha`/`beta` command surfaces, and supporting packages like `kubectl` or local emulators. Reach for it to inspect what is installed, add tools, update or pin/downgrade the CLI version, remove components, or repair a corrupt installation. This is not a Google Cloud API-backed service: every command runs locally against the Cloud SDK component repository, with no project or API enablement required.

> Note: the component manager is disabled when the CLI was installed via a package manager (APT, yum/dnf). In that case, manage components through the OS package manager instead (for example `apt-get install google-cloud-cli-kubectl`). On Windows "All Users" installs, run install/update/remove from an Administrator terminal, and keep your working directory outside the `google-cloud-cli` install directory.

## Quick reference — common workflows

### 1. Inspect installed and available components
```bash
# Status (not installed / installed / update available) of every component
gcloud components list

# Include installed and latest-available version numbers
gcloud components list --show-versions

# Only what is installed locally
gcloud components list --only-local-state
```

### 2. Install a component (e.g. kubectl, or the alpha/beta surfaces)
```bash
# See available component IDs first
gcloud components list

# Install one component (dependencies resolved automatically)
gcloud components install kubectl

# Install several at once
gcloud components install alpha beta
```

### 3. Update — or pin/downgrade — the CLI
```bash
# Update all installed components to the latest version
gcloud components update

# Update (or downgrade) to a fixed Google Cloud CLI version
gcloud components update --version=1.2.3
```

### 4. Remove a component
```bash
# Remove a component and anything that depends on it
gcloud components remove kubectl

# Remove several at once
gcloud components remove alpha beta
```

### 5. Repair a corrupt installation
```bash
# Downloads the latest CLI and reinstalls the same component set
gcloud components reinstall
```

### 6. Manage Trusted Tester repositories
```bash
# Register a Trusted Tester component repository
gcloud components repositories add http://repo.location.com

# List registered repositories
gcloud components repositories list

# Remove all registered repositories
gcloud components repositories remove --all
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `components repositories` | [`repositories.md`](repositories.md) | 3 | Manage additional component repositories for Trusted Tester programs |

Top-level commands (see [`_commands.md`](_commands.md)):

- `gcloud components install` — install one or more components
- `gcloud components list` — list the status of all components
- `gcloud components reinstall` — reinstall the CLI with the components you have now
- `gcloud components remove` — remove one or more installed components
- `gcloud components update` — update all installed components to the latest version

See [`index.md`](index.md) for a one-line index of all 8 commands.

## Common flags & tips
- **Component IDs come from `list`.** `gcloud components list` is the canonical source of installable IDs (`kubectl`, `alpha`, `beta`, `gsutil`, emulators, and so on); use those exact IDs as the positional args to `install` and `remove`.
- **`list` is filterable like any gcloud list.** It accepts `--filter`, `--limit`, and `--sort-by` in addition to the component-specific `--only-local-state`, `--show-versions`, and `--show-platform`.
- **Dependencies are automatic.** `install` also installs dependencies; `remove` also uninstalls anything that depends on the targets. Both list what they will change and prompt for confirmation.
- **Versions live on `update`, not `install`.** `install` always installs at your current CLI version; to move the whole installation use `gcloud components update --version=VERSION` (a lower version downgrades the CLI).
- **`reinstall` takes no arguments** — it rebuilds the installation in place with the current component set.
- **`repositories remove` can target specific URLs or use `--all`.** With no URL and no flag it prompts you to pick a registered repository.

## Official documentation
- [Managing gcloud CLI components](https://cloud.google.com/sdk/docs/components) — primary how-to for list/install/update/remove, including the package-manager caveats.
- [Install the Google Cloud CLI](https://cloud.google.com/sdk/docs/install) — all platform installation methods; references component management for post-install add-ons.
- [Google Cloud CLI quickstart](https://cloud.google.com/sdk/docs/quickstart) — install + init flow that points to component management for kubectl, emulators, and alpha/beta.
- [gcloud components reference](https://cloud.google.com/sdk/gcloud/reference/components) — the command group and every subcommand.

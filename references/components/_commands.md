# gcloud components (top-level commands)

### `gcloud components install`

Install one or more Google Cloud CLI components

Ensure that each of the specified components (as well as any dependent
components) is installed on the local workstation. Components are installed
without performing any upgrades to your existing CLI installation. All
components are installed at the current version of your CLI.

Components that are available for installation can be viewed by running:

    $ gcloud components list

Installing a given component will also install all components on which it
depends. The command lists all components it is about to install, and asks
for confirmation before proceeding.

gcloud components install installs components from the version of the
Google Cloud CLI you currently have installed. You can see your current
version by running:

    $ gcloud version

If you want to update your Google Cloud CLI installation to the latest
available version, use:

    $ gcloud components update

**Synopsis:**
```
gcloud components install COMPONENT-IDS [COMPONENT-IDS ...]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
COMPONENT-IDS [COMPONENT-IDS ...]
   The IDs of the components to be installed.
```

**Examples:**
```bash
The following command installs COMPONENT-1, COMPONENT-2, and all components
that they depend on:

    $ gcloud components install COMPONENT-1 COMPONENT-2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/components/install)

---
### `gcloud components list`

List the status of all Google Cloud CLI components

This command lists all the available components in the Google Cloud CLI.
For each component, the command lists the following information:

  o Status on your local workstation: not installed, installed (and up to
    date), and update available (installed, but not up to date)
  o Name of the component (a description)
  o ID of the component (used to refer to the component in other [gcloud
    components] commands)
  o Size of the component

**Synopsis:**
```
gcloud components list [--only-local-state] [--show-platform]
    [--show-versions] [--filter=EXPRESSION] [--limit=LIMIT]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--only-local-state` |  |  | Only show locally installed components. |
| `--show-platform` |  |  | Show operating system and architecture of all components |
| `--show-versions` |  |  | Show installed and available versions of all components. |


**Examples:**
```bash
To list the status of all Google Cloud CLI components, run:

    $ gcloud components list

To show the currently installed version (if any) and the latest available
version of each component, run:

    $ gcloud components list --show-versions
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/components/list)

---
### `gcloud components reinstall`

Reinstall the Google Cloud CLI with the same components you have now

If your Google Cloud CLI installation becomes corrupt, this command
attempts to fix it by downloading the latest version of the Google Cloud
CLI and reinstalling it. This will replace your existing installation with
a fresh one. The command is the equivalent of deleting your current
installation, downloading a fresh copy of the gcloud CLI, and installing in
the same location.

**Synopsis:**
```
gcloud components reinstall [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To reinstall all components you have installed, run:

    $ gcloud components reinstall
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/components/reinstall)

---
### `gcloud components remove`

Remove one or more installed components

Uninstall all listed components, as well as all components that directly or
indirectly depend on them.

The command lists all components it is about to remove, and asks for
confirmation before proceeding.

**Synopsis:**
```
gcloud components remove COMPONENT_ID [COMPONENT_ID ...]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
COMPONENT_ID [COMPONENT_ID ...]
   The IDs of the components to be removed.
```

**Examples:**
```bash
To remove COMPONENT-1, COMPONENT-2, and all components that directly or
indirectly depend on COMPONENT-1 or COMPONENT-2, type the following:

    $ gcloud components remove COMPONENT-1 COMPONENT-2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/components/remove)

---
### `gcloud components update`

Update all of your installed components to the latest version

Ensure that the latest version of all installed components is installed on
the local workstation.

The command lists all components it is about to update, and asks for
confirmation before proceeding.

By default, this command will update all components to their latest
version. This can be configured by using the --version flag to choose a
specific version to update to. This version may also be a version older
than the one that is currently installed, thus allowing you to downgrade
your Google Cloud CLI installation.

You can see your current Google Cloud CLI version by running:

    $ gcloud version

To see the latest version of the Google Cloud CLI, run:

    $ gcloud components list

If you run this command without the --version flag and you already have the
latest version installed, no update will be performed.

**Synopsis:**
```
gcloud components update [--version=VERSION] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--version` | VERSION |  | An optional Google Cloud CLI version to update your components to. By default, components are updated to the latest available version. By selecting an older version you can downgrade your Google Cloud CLI installation. |


**Examples:**
```bash
To update all installed components to the latest version:

    $ gcloud components update

To update all installed components to a fixed Google Cloud CLI version
1.2.3:

    $ gcloud components update --version=1.2.3
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/components/update)

---
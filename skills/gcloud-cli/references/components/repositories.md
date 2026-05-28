# gcloud components repositories

manage additional component repositories for Trusted Tester programs

### `gcloud components repositories add`

Add a new Trusted Tester component repository

Add a new Trusted Tester component repository to the list of repositories
used by the component manager. This will allow you to install and update
components found in this repository.

If you are participating in a Trusted Tester program, you will be
instructed on the location of repositories with additional versions of one
or more Google Cloud CLI components.

**Synopsis:**
```
gcloud components repositories add URL [URL ...] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URL [URL ...]
   One or more URLs for the component repositories you want to add.
```

**Examples:**
```bash
To add the Trusted Tester component repository http://repo.location.com
run:

    $ gcloud components repositories add http://repo.location.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/components/repositories/add)

---
### `gcloud components repositories list`

List any Trusted Tester component repositories you have registered

List all Trusted Tester component repositories that are registered with the
component manager. If you have additional repositories, the component
manager will look at them to discover additional components to install, or
different versions of existing components that are available.

**Synopsis:**
```
gcloud components repositories list [--filter=EXPRESSION] [--limit=LIMIT]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all Trusted Tester component repositories that are registered with
the component manager, run:

    $ gcloud components repositories list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/components/repositories/list)

---
### `gcloud components repositories remove`

Remove a registered Trusted Test component repository

Remove a registered Trusted Tester component repository from the list of
repositories used by the component manager. After removing a repository,
you can run: $ gcloud components update to revert back to the standard
version of any components that were installed from that repository.

**Synopsis:**
```
gcloud components repositories remove [URL ...] [--all]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[URL ...]
   Zero or more URLs for the component repositories you want to remove. If
   none are given, you will be prompted to choose which existing
   repository you want to remove.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--all` |  |  | Remove all registered repositories. |


**Examples:**
```bash
To be prompted for registered Trusted Tester component repositories to
remove run:

    $ gcloud components repositories remove
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/components/repositories/remove)

---
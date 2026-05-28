# gcloud config configurations

manage the set of gcloud named configurations

### `gcloud config configurations activate`

Activates an existing named configuration

Activates an existing named configuration.

See gcloud topic configurations for an overview of named configurations.

**Synopsis:**
```
gcloud config configurations activate CONFIGURATION_NAME
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CONFIGURATION_NAME
   Name of the configuration to activate
```

**Examples:**
```bash
To activate an existing configuration named my-config, run:

    $ gcloud config configurations activate my-config

To list all properties in the activated configuration, run:

    $ gcloud config list --all
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/config/configurations/activate)

---
### `gcloud config configurations create`

Creates a new named configuration

Creates a new named configuration.

Except for special cases (NONE), configuration names start with a lower
case letter and contain only lower case letters a-z, digits 0-9, and
hyphens '-'.

See gcloud topic configurations for an overview of named configurations.

**Synopsis:**
```
gcloud config configurations create CONFIGURATION_NAME [--no-activate]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CONFIGURATION_NAME
   Name of the configuration to create
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--activate` |  |  | If true, activate this configuration upon create. Enabled by default, use --no-activate to disable. |


**Examples:**
```bash
To create a new named configuration, run:

    $ gcloud config configurations create my-config
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/config/configurations/create)

---
### `gcloud config configurations delete`

Deletes a named configuration

Deletes a named configuration. You cannot delete a configuration that is
active, even when overridden with the --configuration flag. To delete the
current active configuration, first gcloud config configurations activate
another one.

See gcloud topic configurations for an overview of named configurations.

**Synopsis:**
```
gcloud config configurations delete CONFIGURATION_NAMES
    [CONFIGURATION_NAMES ...] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CONFIGURATION_NAMES [CONFIGURATION_NAMES ...]
   Name of the configuration to delete. Cannot be currently active
   configuration.
```

**Examples:**
```bash
To delete an existing configuration named my-config, run:

    $ gcloud config configurations delete my-config

To delete more than one configuration, run:

    $ gcloud config configurations delete my-config1 my-config2

To list existing configurations, run:

    $ gcloud config configurations list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/config/configurations/delete)

---
### `gcloud config configurations describe`

Describes a named configuration by listing its properties

Describes a named configuration by listing its properties.

See gcloud topic configurations for an overview of named configurations.

**Synopsis:**
```
gcloud config configurations describe CONFIGURATION_NAME [--all]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CONFIGURATION_NAME
   Name of the configuration to describe
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--all` |  |  | Include unset properties in output. |


**Examples:**
```bash
To describe an existing configuration named my-config, run:

    $ gcloud config configurations describe my-config

This is similar to:

    $ gcloud config configurations activate my-config

    $ gcloud config list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/config/configurations/describe)

---
### `gcloud config configurations list`

Lists existing named configurations

Lists existing named configurations.

Run $ gcloud topic configurations for an overview of named configurations.

**Synopsis:**
```
gcloud config configurations list [--filter=EXPRESSION] [--limit=LIMIT]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all available configurations, run:

    $ gcloud config configurations list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/config/configurations/list)

---
### `gcloud config configurations rename`

Renames a named configuration

Renames a named configuration.

See gcloud topic configurations for an overview of named configurations.

**Synopsis:**
```
gcloud config configurations rename CONFIGURATION_NAME --new-name=NEW_NAME
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CONFIGURATION_NAME
   Name of the configuration to rename
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--new-name` | NEW_NAME |  | Specifies the new name of the configuration. |


**Examples:**
```bash
To rename an existing configuration named my-config, run:

    $ gcloud config configurations rename my-config --new-name=new-config
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/config/configurations/rename)

---
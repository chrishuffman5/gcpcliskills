# gcloud config (top-level commands)

### `gcloud config get`

Print the value of a Google Cloud CLI property

gcloud config get prints the property value from your active client side
configuration only.

**Synopsis:**
```
gcloud config get SECTION/PROPERTY [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SECTION/PROPERTY
   The property to be fetched. Note that SECTION/ is optional while
   referring to properties in the core section.
```

**Examples:**
```bash
To print the project property in the core section, run:

    $ gcloud config get project

To print the zone property in the compute section, run:

    $ gcloud config get compute/zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/config/get)

---
### `gcloud config list`

List Google Cloud CLI properties for the currently active configuration

gcloud config list lists the properties of the specified section using the
active configuration. These include the account used to authorize access to
Google Cloud, the current Google Cloud project, and the default Compute
Engine region and zone, if set. See gcloud topic configurations for more
about configurations.

**Synopsis:**
```
gcloud config list [SECTION/PROPERTY] [--all] [--filter=EXPRESSION]
    [--limit=LIMIT] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[SECTION/PROPERTY]
   Property to be listed. Note that SECTION/ is optional while referring
   to properties in the core section.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--all` |  |  | List all set and unset properties that match the arguments. |


**Examples:**
```bash
To list the set project property in the core section, run:

    $ gcloud config list project

To list the set zone property in the compute section, run:

    $ gcloud config list compute/zone

To list all the set properties in the compute section, run:

    $ gcloud config list compute/

To list all the properties in the compute section, run:

    $ gcloud config list compute/ --all

To list all the properties, run:

    $ gcloud config list --all

Note, you cannot specify both --all and a property name. Only a section
name and the --all flag can be used together in the format gcloud config
list <SECTION>/ --all.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/config/list)

---
### `gcloud config set`

Set a Google Cloud CLI property

gcloud config set sets the specified property in your active configuration
only. A property governs the behavior of a specific aspect of Google Cloud
CLI such as the service account to use or the verbosity level of logs. To
set the property across all configurations, use the --installation flag.
For more information regarding creating and using configurations, see
gcloud topic configurations.

To view a list of properties currently in use, run gcloud config list.

To unset properties, use gcloud config unset.

Google Cloud CLI comes with a default configuration. To create multiple
configurations, use gcloud config configurations create, and gcloud config
configurations activate to switch between them.

Note: If you are using Cloud Shell, your gcloud command-line tool
preferences are stored in a temporary tmp folder, set for your current tab
only, and do not persist across sessions. For details on how to make these
configurations persist, refer to the Cloud Shell guide on setting gcloud
command-line tool preferences:
https://cloud.google.com/shell/docs/configuring-cloud-shell#gcloud_command-line_tool_preferences.

**Synopsis:**
```
gcloud config set SECTION/PROPERTY VALUE [--installation]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SECTION/PROPERTY
   Property to be set. Note that SECTION/ is optional while referring to
   properties in the core section, i.e., using either core/project or
   project is a valid way of setting a project. Using section names is
   required for setting other properties like compute/region. Consult the
   Available Properties section below for a comprehensive list of
   properties.

VALUE
   Value to be set.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--installation` |  |  | If set, the property is updated for the entire Google Cloud CLI installation. Otherwise, by default, the property is updated only in the currently active configuration. |


**Examples:**
```bash
To set the project property in the core section, run:

    $ gcloud config set project PROJECT_ID

To set the zone property in the compute section, run:

    $ gcloud config set compute/zone ZONE_NAME

To disable prompting for scripting, run:

    $ gcloud config set disable_prompts true

To set a proxy with the appropriate type, and specify the address and port
on which to reach it, run:

    $ gcloud config set proxy/type http
    $ gcloud config set proxy/address 1.234.56.78
    $ gcloud config set proxy/port 8080

For a full list of accepted values, see
https://cloud.google.com/sdk/gcloud/reference/topic/configurations#AVAILABLE-PROPERTIES.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/config/set)

---
### `gcloud config unset`

Unset a Google Cloud CLI property

By default, unsets the property in your active configuration only. Use the
--installation flag to unset the property across all configurations. See
gcloud topic configurations for more information.

**Synopsis:**
```
gcloud config unset SECTION/PROPERTY [--installation]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SECTION/PROPERTY
   The property to be unset. Note that SECTION/ is optional while
   referring to properties in the core section.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--installation` |  |  | If set, the property is updated for the entire Google Cloud CLI installation. Otherwise, by default, the property is updated only in the currently active configuration. |


**Examples:**
```bash
To unset the project property in the core section, run:

    $ gcloud config unset project

To unset the zone property in the compute section, run:

    $ gcloud config unset compute/zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/config/unset)

---
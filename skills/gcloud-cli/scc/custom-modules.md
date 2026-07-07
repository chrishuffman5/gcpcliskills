# gcloud scc custom-modules

manage Cloud SCC (Security Command Center) custom modules


## `gcloud scc custom-modules sha` — manage Security Health Analytics custom modules
### `gcloud scc custom-modules sha create`

Create a Security Health Analytics custom module

Create a Security Health Analytics custom module.

**Synopsis:**
```
gcloud scc custom-modules sha create --custom-config-from-file=PATH_TO_FILE
    --display-name=DISPLAY_NAME --enablement-state=ENABLEMENT_STATE
    [--folder=FOLDER | --organization=ORGANIZATION | --project=PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--custom-config-from-file` | PATH_TO_FILE |  | Path to a YAML file that contains the configuration for the Security Health Analytics custom module. Use a full or relative path to a local file containing the value of custom_config. |
| `--display-name` | DISPLAY_NAME |  | Sets the display name of the Security Health Analytics custom module. This display name becomes the finding category for all findings that are returned by this custom module. The display name must be between 1 and 128 characters, start with a lowercase letter, and contain alphanumeric characters or underscores only. |
| `--enablement-state` | one of: disabled, enabled, enablement-state-unspecified, inherited |  | Sets the enablement state of the Security Health Analytics custom module. From the following list of possible enablement states, specify either enabled or disabled only. ENABLEMENT_STATE must be one of: disabled, enabled, enablement-state-unspecified, inherited. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER |  | _[At most one of these can be specified:]_ Folder where the Security Health Analytics custom module resides. Formatted as folders/456 or just 456. |
| `--organization` | ORGANIZATION |  | _[At most one of these can be specified:]_ Organization where the Security Health Analytics custom module resides. Formatted as organizations/123 or just 123. |
| `--project` | PROJECT |  | _[At most one of these can be specified:]_ ID or number of the project where the Security Health Analytics custom module resides. Formatted as projects/789 or just 789. |


**Examples:**
```bash
To create a Security Health Analytics custom module for given organization
123, run:

    $ gcloud scc custom-modules sha create \
        --organization=organizations/123 \
        --display-name="test_display_name" \
        --enablement-state="ENABLED" \
        --custom-config-from-file=custom_config.yaml

To create a Security Health Analytics custom module for given folder 456,
run:

    $ gcloud scc custom-modules sha create --folder=folders/456 \
        --display-name="test_display_name" \
        --enablement-state="ENABLED" \
        --custom-config-from-file=custom_config.yaml

To create a Security Health Analytics custom module for given project 789,
run:

    $ gcloud scc custom-modules sha create --project=projects/789 \
        --display-name="test_display_name" \
        --enablement-state="ENABLED" \
        --custom-config-from-file=custom_config.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/custom-modules/sha/create)

---
### `gcloud scc custom-modules sha delete`

Delete a Security Health Analytics custom module

Delete a Security Health Analytics custom module.

**Synopsis:**
```
gcloud scc custom-modules sha delete CUSTOM_MODULE
    [--folder=FOLDER | --organization=ORGANIZATION | --project=PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CUSTOM_MODULE
   ID or the full resource name of the Security Health Analytics custom
   module. If you specify the full resource name, you do not need to
   specify the --organization, --folder, or --project flags.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER |  | _[At most one of these can be specified:]_ Folder where the Security Health Analytics custom module resides. Formatted as folders/456 or just 456. |
| `--organization` | ORGANIZATION |  | _[At most one of these can be specified:]_ Organization where the Security Health Analytics custom module resides. Formatted as organizations/123 or just 123. |
| `--project` | PROJECT |  | _[At most one of these can be specified:]_ ID or number of the project where the Security Health Analytics custom module resides. Formatted as projects/789 or just 789. |


**Examples:**
```bash
To delete a Security Health Analytics custom module with ID 123456 for
organization 123, run:

    $ gcloud scc custom-modules sha delete 123456 \
        --organization=organizations/123

To delete a Security Health Analytics custom module with ID 123456 for
folder 456, run:

    $ gcloud scc custom-modules sha delete 123456 --folder=folders/456

To delete a Security Health Analytics custom module with ID 123456 for
project 789, run:

    $ gcloud scc custom-modules sha delete 123456 --project=projects/789
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/custom-modules/sha/delete)

---
### `gcloud scc custom-modules sha get`

Get the details of a Security Health Analytics custom module

Get the details of a Security Health Analytics custom module. It does not
resolve INHERITED enablement states to ENABLED or DISABLED for modules
created at ancestor levels. For example, if the module is enabled at the
ancestor level, modules for all child resources will have the enablement
state set to INHERITED. Use gcloud scc custom-modules sha get-effective to
retrieve a custom module with its effective enablement state.

**Synopsis:**
```
gcloud scc custom-modules sha get CUSTOM_MODULE
    [--folder=FOLDER | --organization=ORGANIZATION | --project=PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CUSTOM_MODULE
   ID or the full resource name of the Security Health Analytics custom
   module. If you specify the full resource name, you do not need to
   specify the --organization, --folder, or --project flags.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER |  | _[At most one of these can be specified:]_ Folder from which to get the custom module details. Formatted as folders/456 or just 456. |
| `--organization` | ORGANIZATION |  | _[At most one of these can be specified:]_ Organization from which to get the custom module details. Formatted as organizations/123 or just 123. |
| `--project` | PROJECT |  | _[At most one of these can be specified:]_ ID or number of the project from which to get the custom module details. Formatted as projects/789 or just 789. |


**Examples:**
```bash
To get the details of a Security Health Analytics custom module with ID
123456 for organization 123, run:

    $ gcloud scc custom-modules sha get 123456 \
        --organization=organizations/123

To get the details of a Security Health Analytics custom module with ID
123456 for folder 456, run:

    $ gcloud scc custom-modules sha get 123456 --folder=folders/456

To get the details of a Security Health Analytics custom module with ID
123456 for project 789, run:

    $ gcloud scc custom-modules sha get 123456 --project=projects/789
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/custom-modules/sha/get)

---
### `gcloud scc custom-modules sha get-effective`

Get the details of a Security Health Analytics custom module with effective enablement state

Get the details of a Security Health Analytics custom module. For inherited
custom modules, the get-effective command resolves INHERITED enablement
states to ENABLED or DISABLED. For example, if an inherited custom module
is enabled at the ancestor level, then the get-effective command displays
the enablement state as ENABLED instead of INHERITED in a child folder or
project.

**Synopsis:**
```
gcloud scc custom-modules sha get-effective CUSTOM_MODULE
    [--folder=FOLDER | --organization=ORGANIZATION | --project=PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CUSTOM_MODULE
   ID or the full resource name of the effective Security Health Analytics
   custom module. If you specify the full resource name, you do not need
   to specify the --organization, --folder, or --project flags.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER |  | _[At most one of these can be specified:]_ Folder from which to get the custom module details. Formatted as folders/456 or just 456. |
| `--organization` | ORGANIZATION |  | _[At most one of these can be specified:]_ Organization from which to get the custom module details. Formatted as organizations/123 or just 123. |
| `--project` | PROJECT |  | _[At most one of these can be specified:]_ ID or number of the project from which to get the custom module details. Formatted as projects/789 or just 789. |


**Examples:**
```bash
To get the details of a Security Health Analytics custom module 123456 with
its effective enablement state from organization 123, run:

    $ gcloud scc custom-modules sha get-effective 123456 \
        --organization=organizations/123

To get the details of a Security Health Analytics custom module 123456 with
its effective enablement state from folder 456, run:

    $ gcloud scc custom-modules sha get-effective 123456 \
        --folder=folders/456

To get the details of a Security Health Analytics custom module 123456 with
its effective enablement state from project 789, run:

    $ gcloud scc custom-modules sha get-effective 123456 \
        --project=projects/789
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/custom-modules/sha/get-effective)

---
### `gcloud scc custom-modules sha list`

List the details of Security Health Analytics custom modules

List the details of the resident and inherited Security Health Analytics
custom modules for the specified folder or project. For an organization,
this command lists only the custom modules that are created at the
organization level. Custom modules created in child folders or projects are
not included in the list. To list the resident custom modules and the
modules that are created in child folders or projects, use gcloud scc
custom-modules sha list-descendant.

**Synopsis:**
```
gcloud scc custom-modules sha list
    (--folder=FOLDER | --organization=ORGANIZATION | --project=PROJECT)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER |  | _[Exactly one of these must be specified:]_ Folder for listing the Security Health Analytics custom modules created at the current folder level and inherited modules from CRM ancestors. Formatted as folders/456 or just 456. |
| `--organization` | ORGANIZATION |  | _[Exactly one of these must be specified:]_ Organization for listing the Security Health Analytics custom modules created at the organization level. Formatted as organizations/123 or just 123. |
| `--project` | PROJECT |  | _[Exactly one of these must be specified:]_ ID or number of the project for listing the Security Health Analytics custom modules created at current project level and inherited modules from CRM ancestors. Formatted as projects/789 or just 789. |


**Examples:**
```bash
To list resident and inherited Security Health Analytics custom modules for
organization 123, run:

    $ gcloud scc custom-modules sha list --organization=organizations/123

To list resident and inherited Security Health Analytics custom modules for
folder 456, run:

    $ gcloud scc custom-modules sha list --folder=folders/456

To list resident and inherited Security Health Analytics custom modules for
project 789, run:

    $ gcloud scc custom-modules sha list --project=projects/789
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/custom-modules/sha/list)

---
### `gcloud scc custom-modules sha list-descendant`

List the details of the resident and descendant Security Health Analytics custom modules

List the details of the resident and descendant Security Health Analytics
custom modules for a specified organization or folder. For a project, this
command lists only the custom modules that are created in the project.
Modules created in a parent organization or folder are excluded from the
list. To list the resident custom modules and the modules that are
inherited from a parent organization and folder, use gcloud scc
custom-modules sha list.

**Synopsis:**
```
gcloud scc custom-modules sha list-descendant
    (--folder=FOLDER | --organization=ORGANIZATION | --project=PROJECT)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER |  | _[Exactly one of these must be specified:]_ Folder for listing the Security Health Analytics custom modules created at the current folder level and its child resources. Formatted as folders/456 or just 456. |
| `--organization` | ORGANIZATION |  | _[Exactly one of these must be specified:]_ Organization for listing the Security Health Analytics custom modules created at the organization level and its child resources. Formatted as organizations/123 or just 123. |
| `--project` | PROJECT |  | _[Exactly one of these must be specified:]_ ID or number of the project for listing the Security Health Analytics custom modules at current project level. Formatted as projects/789 or just 789. |


**Examples:**
```bash
To list resident and descendant Security Health Analytics custom modules
for organization 123, run:

    $ gcloud scc custom-modules sha list-descendant \
        --organization=organizations/123

To list resident and descendant Security Health Analytics custom modules
for folder 456, run:

    $ gcloud scc custom-modules sha list-descendant --folder=folders/456

To list resident and descendant Security Health Analytics custom modules
for project 789, run:

    $ gcloud scc custom-modules sha list-descendant \
        --project=projects/789
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/custom-modules/sha/list-descendant)

---
### `gcloud scc custom-modules sha list-effective`

List the details of Security Health Analytics custom modules with effective enablement states

List the details of resident and inherited Security Health Analytics custom
modules for the specified folder or project with their effective enablement
states. For an organization, this command lists only the custom modules
that are created at the organization level. Custom modules created in child
folders or projects are not included in the list.

**Synopsis:**
```
gcloud scc custom-modules sha list-effective
    (--folder=FOLDER | --organization=ORGANIZATION | --project=PROJECT)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER |  | _[Exactly one of these must be specified:]_ Folder for listing the effective Security Health Analytics custom modules created at the current folder level and inherited modules from CRM ancestors. Formatted as folders/456 or just 456. |
| `--organization` | ORGANIZATION |  | _[Exactly one of these must be specified:]_ Organization for listing the effective Security Health Analytics custom modules created at the organization level. Formatted as organizations/123 or just 123. |
| `--project` | PROJECT |  | _[Exactly one of these must be specified:]_ ID or number of the project for listing the effective Security Health Analytics custom modules for the current project level and inherited modules from CRM ancestors. Formatted as projects/789 or just 789. |


**Examples:**
```bash
To list resident and inherited Security Health Analytics custom modules
with effective enablement states for organization 123, run:

    $ gcloud scc custom-modules sha list-effective \
        --organization=organizations/123

To list resident and inherited effective Security Health Analytics custom
modules with effective enablement states for folder 456, run:

    $ gcloud scc custom-modules sha list-effective --folder=folders/456

To list resident and inherited effective Security Health Analytics custom
modules with effective enablement states for project 789, run:

    $ gcloud scc custom-modules sha list-effective --project=projects/789
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/custom-modules/sha/list-effective)

---
### `gcloud scc custom-modules sha simulate`

Validates a Security Health Analytics custom module

Validates a given Security Health Analytics custom module and resource.

**Synopsis:**
```
gcloud scc custom-modules sha simulate
    --custom-config-from-file=PATH_TO_FILE
    --resource-from-file=PATH_TO_FILE
    (--folder=FOLDER | --organization=ORGANIZATION | --project=PROJECT)
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--custom-config-from-file` | PATH_TO_FILE |  | Path to a YAML file that contains the configuration for the Security Health Analytics custom module. Use a full or relative path to a local file containing the value of custom_config. |
| `--resource-from-file` | PATH_TO_FILE |  | Path to a YAML file that contains the resource data to validate the Security Health Analytics custom module against. Use a full or relative path to a local file containing the value of resource. |


**Examples:**
```bash
To validate a Security Health Analytics custom module against a custom
resource for organization 123, run:

    $ gcloud scc custom-modules sha simulate \
        --organization=organizations/123 \
        --custom-config-from-file=/tmp/custom_config.yaml \
        --resource-from-file=/tmp/resource.yaml

To validate a Security Health Analytics custom module against a custom
resource for folder 456, run:

    $ gcloud scc custom-modules sha simulate --folder=folders/456 \
        --custom-config-from-file=/tmp/custom_config.yaml \
        --resource-from-file=/tmp/resource.yaml

To validate a Security Health Analytics custom module against a custom
resource for project 789, run:

    $ gcloud scc custom-modules sha simulate --project=projects/789 \
        --custom-config-from-file=/tmp/custom_config.yaml \
        --resource-from-file=/tmp/resource.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/custom-modules/sha/simulate)

---
### `gcloud scc custom-modules sha update`

Update a Security Health Analytics custom module

Update a Security Health Analytics custom module.

**Synopsis:**
```
gcloud scc custom-modules sha update CUSTOM_MODULE
    [--custom-config-from-file=PATH_TO_FILE]
    [--enablement-state=ENABLEMENT_STATE] [--update-mask=UPDATE_MASK]
    [--folder=FOLDER | --organization=ORGANIZATION | --project=PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CUSTOM_MODULE
   ID or the full resource name of the Security Health Analytics custom
   module. If you specify the full resource name, you do not need to
   specify the --organization, --folder, or --project flags.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--custom-config-from-file` | PATH_TO_FILE |  | Path to a YAML file that contains the configuration for the Security Health Analytics custom module. Use a full or relative path to a local file containing the value of custom_config. |
| `--enablement-state` | one of: disabled, enabled, enablement-state-unspecified, inherited |  | Sets the enablement state of the Security Health Analytics custom module. From the following list of possible enablement states, specify either enabled, disabled or inherited only. ENABLEMENT_STATE must be one of: disabled, enabled, enablement-state-unspecified, inherited. |
| `--update-mask` | UPDATE_MASK |  | Optional: If left unspecified (default), an update-mask is automatically created using the flags specified in the command and only those values are updated. |


**Examples:**
```bash
To update a Security Health Analytics custom module with ID 123456 for
organization 123, run:

    $ gcloud scc custom-modules sha update 123456 \
        --organization=organizations/123 --enablement-state="ENABLED" \
        --custom-config-from-file=custom_config.yaml

To update a Security Health Analytics custom module with ID 123456 for
folder 456, run:

    $ gcloud scc custom-modules sha update 123456 --folder=folders/456 \
        --enablement-state="ENABLED" \
        --custom-config-from-file=custom_config.yaml

To update a Security Health Analytics custom module with ID 123456 for
project 789, run:

    $ gcloud scc custom-modules sha update 123456 \
        --project=projects/789 --enablement-state="ENABLED" \
        --custom-config-from-file=custom_config.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/custom-modules/sha/update)

---
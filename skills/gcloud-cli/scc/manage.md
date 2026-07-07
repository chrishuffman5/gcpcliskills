# gcloud scc manage

manage Cloud SCC (Security Command Center) settings


## `gcloud scc manage custom-modules` — manage Cloud SCC (Security Command Center) custom modules

## `gcloud scc manage custom-modules etd` — manage custom modules
### `gcloud scc manage custom-modules etd create`

Create an Event Threat Detection custom module

**Synopsis:**
```
gcloud scc manage custom-modules etd create
    --custom-config-file=CUSTOM_CONFIG --display-name=DISPLAY-NAME
    --enablement-state=ENABLEMENT_STATE --module-type=MODULE_TYPE
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID | --parent=PARENT
      | --project=PROJECT_ID_OR_NUMBER) [--validate-only]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--custom-config-file` | CUSTOM_CONFIG |  | Path to a JSON custom configuration file of the ETD custom module. Use a full or relative path to a local file containing the value of custom_config_file. |
| `--display-name` | DISPLAY-NAME |  | The display name of the custom module. |
| `--enablement-state` | ENABLEMENT_STATE |  | Sets the enablement state of the Event Threat Detection custom module. Valid options are ENABLED, DISABLED, OR INHERITED. |
| `--module-type` | MODULE_TYPE |  | Type of the custom module. For a list of valid module types please visit https://cloud.google.com/security-command-center/docs/custom-modules-etd-overview#custom_modules_and_templates. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--validate-only` |  |  | If present, the request is validated (including IAM checks) but no action is taken. |


**Examples:**
```bash
To create an Event Threat Detection custom module for organization 123,
run:

    $ gcloud scc manage custom-modules etd create \
        --organization=organizations/123 \
        --display-name="test_display_name" \
        --module-type="CONFIGURABLE_BAD_IP" \
        --enablement-state="ENABLED" --custom-config-file=config.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/manage/custom-modules/etd/create)

---
### `gcloud scc manage custom-modules etd delete`

Delete an Event Threat Detection custom module

Delete a Event Threat Detection custom module. User specifies the custom
module as well as the parent of the module to delete. A validation_only
flag is optional. When set to true only validations (including IAM checks)
will done for the request (module will not be deleted).

**Synopsis:**
```
gcloud scc manage custom-modules etd delete MODULE_ID_OR_NAME
    [--validate-only]
    [--folder=FOLDER_ID | --organization=ORGANIZATION_ID | --parent=PARENT
      | --project=PROJECT_ID_OR_NUMBER] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
MODULE_ID_OR_NAME
   The custom module ID or name. The expected format is
   {parent}/[locations/global]/eventThreatDetectionCustomModules/{module_id}
   or just {module_id}. Where module_id is a numeric identifier 1-20
   characters in length. Parent is of the form organizations/{id},
   projects/{id or name}, folders/{id}.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--validate-only` |  |  | If present, the request is validated (including IAM checks) but no action is taken. |


**Examples:**
```bash
To delete an Event Threat Detection custom module with ID 123456 for
organization 123, run:

    $ gcloud scc manage custom-modules etd delete 123456 \
        --organization=123

To delete a Event Threat Detection custom module with ID 123456 for folder
456, run:

    $ gcloud scc manage custom-modules etd delete 123456 --folder=456

To delete a Event Threat Detection custom module with ID 123456 for project
789, run:

    $ gcloud scc manage custom-modules etd delete 123456 --project=789

You can also specify the parent more generally:

    $ gcloud scc manage custom-modules etd delete 123456 \
        --parent=organizations/123

Or just specify the fully qualified module name:

    $ gcloud scc manage custom-modules etd delete \
        organizations/123/locations/global/\
    eventThreatDetectionCustomModules/123456
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/manage/custom-modules/etd/delete)

---
### `gcloud scc manage custom-modules etd describe`

Get the details of a Event Threat Detection custom module

Get the details of a Event Threat Detection custom module. It does not
resolve INHERITED enablement states to ENABLED or DISABLED for modules
created at ancestor levels. For example, if the module is enabled at the
ancestor level, modules for all child resources will have the enablement
state set to INHERITED. Use gcloud scc manage custom-modules etd
get-effective to retrieve a custom module with its effective enablement
state.

**Synopsis:**
```
gcloud scc manage custom-modules etd describe MODULE_ID_OR_NAME
    [--folder=FOLDER_ID | --organization=ORGANIZATION_ID | --parent=PARENT
      | --project=PROJECT_ID_OR_NUMBER] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
MODULE_ID_OR_NAME
   The custom module ID or name. The expected format is
   {parent}/[locations/global]/eventThreatDetectionCustomModules/{module_id}
   or just {module_id}. Where module_id is a numeric identifier 1-20
   characters in length. Parent is of the form organizations/{id},
   projects/{id or name}, folders/{id}.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[At most one of these can be specified:]_ Folder associated with the custom module. |
| `--organization` | ORGANIZATION_ID |  | _[At most one of these can be specified:]_ Organization associated with the custom module. |
| `--parent` | PARENT |  | _[At most one of these can be specified:]_ Parent associated with the custom module. Can be one of organizations/<id>, projects/<id or name>, folders/<id> |
| `--project` | PROJECT_ID_OR_NUMBER |  | _[At most one of these can be specified:]_ Project associated with the custom module. |


**Examples:**
```bash
To get the details of a Event Threat Detection custom module with ID 123456
for organization 123, run:

    $ gcloud scc manage custom-modules etd describe 123456 \
        --organization=123

To get the details of a Event Threat Detection custom module with ID 123456
for folder 456, run:

    $ gcloud scc manage custom-modules etd describe 123456 --folder=456

To get the details of a Event Threat Detection custom module with ID 123456
for project 789, run:

    $ gcloud scc manage custom-modules etd describe 123456 --project=789

You can also specify the parent more generally:

    $ gcloud scc manage custom-modules etd describe 123456 \
        --parent=organizations/123

Or just specify the fully qualified module name:

    $ gcloud scc manage custom-modules etd describe \
        organizations/123/locations/global/\
    eventThreatDetectionCustomModules/123456
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/manage/custom-modules/etd/describe)

---
### `gcloud scc manage custom-modules etd describe-effective`

Get the effective details of a Event Threat Detection effective custom module

Get the effective details of a Event Threat Detection effective custom
module. It retrieves a custom module with its effective enablement state.

**Synopsis:**
```
gcloud scc manage custom-modules etd describe-effective MODULE_ID_OR_NAME
    [--folder=FOLDER_ID | --organization=ORGANIZATION_ID | --parent=PARENT
      | --project=PROJECT_ID_OR_NUMBER] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
MODULE_ID_OR_NAME
   The custom module ID or name. The expected format is
   {parent}/[locations/global]/effectiveEventThreatDetectionCustomModules/{module_id}
   or just {module_id}. Where module_id is a numeric identifier 1-20
   characters in length. Parent is of the form organizations/{id},
   projects/{id or name}, folders/{id}.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[At most one of these can be specified:]_ Folder associated with the custom module. |
| `--organization` | ORGANIZATION_ID |  | _[At most one of these can be specified:]_ Organization associated with the custom module. |
| `--parent` | PARENT |  | _[At most one of these can be specified:]_ Parent associated with the custom module. Can be one of organizations/<id>, projects/<id or name>, folders/<id> |
| `--project` | PROJECT_ID_OR_NUMBER |  | _[At most one of these can be specified:]_ Project associated with the custom module. |


**Examples:**
```bash
To get the effective details of a Event Threat Detection custom module with
ID 123456 for organization 123, run:

    $ gcloud scc manage custom-modules etd describe-effective 123456 \
        --organization=123

To get the effective details of a Event Threat Detection custom module with
ID 123456 for folder 456, run:

    $ gcloud scc manage custom-modules etd describe-effective 123456 \
        --folder=456

To get the effective details of a Event Threat Detection custom module with
ID 123456 for project 789, run:

    $ gcloud scc manage custom-modules etd describe-effective 123456 \
        --project=789

You can also specify the parent more generally:

    $ gcloud scc manage custom-modules etd describe-effective 123456 \
        --parent=organizations/123

Or just specify the fully qualified module name:

    $ gcloud scc manage custom-modules etd describe-effective \
        organizations/123/locations/global/\
    effectiveEventThreatDetectionCustomModules/123456
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/manage/custom-modules/etd/describe-effective)

---
### `gcloud scc manage custom-modules etd list`

List details of resident and inherited Event Threat Detection Custom Modules

List the details of the resident and inherited Event Threat Detection
custom modules for the specified folder or project. For an organization,
this command lists only the custom modules that are created at the
organization level. Custom modules created in child folders or projects are
not included in the list. To list the resident custom modules and the
modules that are created in child folders or projects, use gcloud scc
manage custom-modules etd list-descendant.

**Synopsis:**
```
gcloud scc manage custom-modules etd list
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID | --parent=PARENT
      | --project=PROJECT_ID_OR_NUMBER) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[Exactly one of these must be specified:]_ Folder associated with the custom module. |
| `--organization` | ORGANIZATION_ID |  | _[Exactly one of these must be specified:]_ Organization associated with the custom module. |
| `--parent` | PARENT |  | _[Exactly one of these must be specified:]_ Parent associated with the custom module. Can be one of organizations/<id>, projects/<id or name>, folders/<id> |
| `--project` | PROJECT_ID_OR_NUMBER |  | _[Exactly one of these must be specified:]_ Project associated with the custom module. |


**Examples:**
```bash
To list resident and inherited Event Threat Detection custom modules for
organization 123, run:

    $ gcloud scc manage custom-modules etd list \
        --organization=organizations/123

To list resident and inherited Event Threat Detection custom modules for
folder 456, run:

    $ gcloud scc manage custom-modules etd list --folder=folders/456

To list resident and inherited Event Threat Detection custom modules for
project 789, run:

    $ gcloud scc manage custom-modules etd list --project=projects/789
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/manage/custom-modules/etd/list)

---
### `gcloud scc manage custom-modules etd list-descendant`

List the details of the resident and descendant Event Threat Detection custom modules

List the details of the resident and descendant Event Threat Detection
custom modules for a specified organization or folder. For a project, this
command lists only the custom modules that are created in the project.
Modules created in a parent organization or folder are excluded from the
list. To list the resident custom modules and the modules that are
inherited from a parent organization and folder, use gcloud scc manage
custom-modules etd list.

**Synopsis:**
```
gcloud scc manage custom-modules etd list-descendant
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID | --parent=PARENT
      | --project=PROJECT_ID_OR_NUMBER) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[Exactly one of these must be specified:]_ Folder associated with the custom module. |
| `--organization` | ORGANIZATION_ID |  | _[Exactly one of these must be specified:]_ Organization associated with the custom module. |
| `--parent` | PARENT |  | _[Exactly one of these must be specified:]_ Parent associated with the custom module. Can be one of organizations/<id>, projects/<id or name>, folders/<id> |
| `--project` | PROJECT_ID_OR_NUMBER |  | _[Exactly one of these must be specified:]_ Project associated with the custom module. |


**Examples:**
```bash
To list resident and descendant Event Threat Detection custom modules for
organization 123, run:

    $ gcloud scc manage custom-modules etd list-descendant \
        --organization=organizations/123

To list resident and descendant Event Threat Detection custom modules for
folder 456, run:

    $ gcloud scc manage custom-modules etd list-descendant \
        --folder=folders/456

To list resident and descendant Event Threat Detection custom modules for
project 789, run:

    $ gcloud scc manage custom-modules etd list-descendant \
        --project=projects/789
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/manage/custom-modules/etd/list-descendant)

---
### `gcloud scc manage custom-modules etd list-effective`

List the details of an Event Threat Detection effective custom module

List the details of resident and inherited Event Threat Detection custom
modules for the specified folder or project with their effective enablement
states. For an organization, this command lists only the custom modules
that are created at the organization level. Custom modules created in child
folders or projects are not included in the list.

**Synopsis:**
```
gcloud scc manage custom-modules etd list-effective
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID | --parent=PARENT
      | --project=PROJECT_ID_OR_NUMBER) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[Exactly one of these must be specified:]_ Folder associated with the custom module. |
| `--organization` | ORGANIZATION_ID |  | _[Exactly one of these must be specified:]_ Organization associated with the custom module. |
| `--parent` | PARENT |  | _[Exactly one of these must be specified:]_ Parent associated with the custom module. Can be one of organizations/<id>, projects/<id or name>, folders/<id> |
| `--project` | PROJECT_ID_OR_NUMBER |  | _[Exactly one of these must be specified:]_ Project associated with the custom module. |


**Examples:**
```bash
To list resident and inherited Event Threat Detection custom modules with
effective enablement states for organization 123, run:

    $ gcloud scc manage custom-modules etd list-effective \
        --organization=organizations/123

To list resident and inherited effective Event Threat Detection custom
modules with effective enablement states for folder 456, run:

    $ gcloud scc manage custom-modules etd list-effective \
        --folder=folders/456

To list resident and inherited effective Event Threat Detection custom
modules with effective enablement states for project 789, run:

    $ gcloud scc manage custom-modules etd list-effective \
        --project=projects/789
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/manage/custom-modules/etd/list-effective)

---
### `gcloud scc manage custom-modules etd update`

Update an Event Threat Detection custom module

**Synopsis:**
```
gcloud scc manage custom-modules etd update MODULE_ID_OR_NAME
    (--custom-config-file=PATH_TO_FILE --enablement-state=ENABLEMENT_STATE)
    [--validate-only]
    [--folder=FOLDER_ID | --organization=ORGANIZATION_ID | --parent=PARENT
      | --project=PROJECT_ID_OR_NUMBER] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
MODULE_ID_OR_NAME
   The custom module ID or name. The expected format is
   {parent}/[locations/global]/eventThreatDetectionCustomModules/{module_id}
   or just {module_id}. Where module_id is a numeric identifier 1-20
   characters in length. Parent is of the form organizations/{id},
   projects/{id or name}, folders/{id}.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--custom-config-file` | PATH_TO_FILE |  | _[At least one of these must be specified:]_ Path to a JSON file that contains the custom config to set for the module. Use a full or relative path to a local file containing the value of custom_config_file. |
| `--enablement-state` | ENABLEMENT_STATE |  | _[At least one of these must be specified:]_ Sets the enablement state of the Event Threat Detection custom module. Valid options are ENABLED, DISABLED, OR INHERITED. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--validate-only` |  |  | If present, the request is validated (including IAM checks) but no action is taken. |


**Examples:**
```bash
To update an Event Threat Detection custom module with ID 123456 for
organization 123, run:

    $ gcloud scc manage custom-modules etd update 123456 \
      --organization=organizations/123 --enablement-state="ENABLED" \
      --custom-config-file=custom_config.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/manage/custom-modules/etd/update)

---
### `gcloud scc manage custom-modules etd validate`

Command to validate an ETD custom module

**Synopsis:**
```
gcloud scc manage custom-modules etd validate
    --custom-config-file=CUSTOM_CONFIG --module-type=MODULE_TYPE
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID | --parent=PARENT
      | --project=PROJECT_ID_OR_NUMBER) [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--custom-config-file` | CUSTOM_CONFIG |  | Path to a JSON custom configuration file of the ETD custom module. Use a full or relative path to a local file containing the value of custom_config_file. |
| `--module-type` | MODULE_TYPE |  | Type of the custom module. For a list of valid module types please visit https://cloud.google.com/security-command-center/docs/custom-modules-etd-overview#custom_modules_and_templates. |


**Examples:**
```bash
To validate an Event Threat Detection custom module 'config.json' with a
module type 'CONFIGURABLE_BAD_IP', run:

    $ gcloud scc manage custom-modules etd validate \
        --organization=organizations/252600681248 \
        --custom-config-file=config.json \
        --module-type=CONFIGURABLE_BAD_IP

You can also specify the parent more generally:

    $ gcloud scc manage custom-modules etd validate \
        --parent=organizations/252600681248 \
        --custom-config-file=config.json \
        --module-type=CONFIGURABLE_BAD_IP
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/manage/custom-modules/etd/validate)

---

## `gcloud scc manage custom-modules sha` — manage Security Health Analytics custom modules
### `gcloud scc manage custom-modules sha create`

Create an Security Health Analytics custom module

**Synopsis:**
```
gcloud scc manage custom-modules sha create
    --custom-config-from-file=CUSTOM_CONFIG --display-name=DISPLAY-NAME
    --enablement-state=ENABLEMENT_STATE
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID | --parent=PARENT
      | --project=PROJECT_ID_OR_NUMBER) [--validate-only]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--custom-config-from-file` | CUSTOM_CONFIG |  | Path to a YAML custom configuration file. Use a full or relative path to a local file containing the value of custom_config. |
| `--display-name` | DISPLAY-NAME |  | The display name of the custom module. |
| `--enablement-state` | ENABLEMENT_STATE |  | Sets the enablement state of the Security Health Analytics custom module. Valid options are ENABLED, DISABLED, OR INHERITED. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--validate-only` |  |  | If present, the request is validated (including IAM checks) but no action is taken. |


**Examples:**
```bash
To create a Security Health Analytics custom module for organization 123,
run:

    $ gcloud scc manage custom-modules sha create \
        --organization=organizations/123 \
        --display-name="test_display_name" \
        --enablement-state="ENABLED" \
        --custom-config-from-file=custom_config.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/manage/custom-modules/sha/create)

---
### `gcloud scc manage custom-modules sha delete`

Delete a Security Health Analytics custom module

Delete a Security Health Analytics custom module. User specifies the custom
module as well as the parent of the module to delete. A validation_only
flag is optional. When set to true only validations (including IAM checks)
will done for the request (module will not be deleted).

**Synopsis:**
```
gcloud scc manage custom-modules sha delete MODULE_ID_OR_NAME
    [--validate-only]
    [--folder=FOLDER_ID | --organization=ORGANIZATION_ID | --parent=PARENT
      | --project=PROJECT_ID_OR_NUMBER] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
MODULE_ID_OR_NAME
   The custom module ID or name. The expected format is
   {parent}/[locations/global]/securityHealthAnalyticsCustomModules/{module_id}
   or just {module_id}. Where module_id is a numeric identifier 1-20
   characters in length. Parent is of the form organizations/{id},
   projects/{id or name}, folders/{id}.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--validate-only` |  |  | If present, the request is validated (including IAM checks) but no action is taken. |


**Examples:**
```bash
To delete an Security Health Analytics custom module with ID 123456 for
organization 123, run:

    $ gcloud scc manage custom-modules sha delete 123456 \
        --organization=123

To delete a Security Health Analytics custom module with ID 123456 for
folder 456, run:

    $ gcloud scc manage custom-modules sha delete 123456 --folder=456

To delete a Security Health Analytics custom module with ID 123456 for
project 789, run:

    $ gcloud scc manage custom-modules sha delete 123456 --project=789

You can also specify the parent more generally:

    $ gcloud scc manage custom-modules sha delete 123456 \
        --parent=organizations/123

Or just specify the fully qualified module name:

    $ gcloud scc manage custom-modules sha delete \
        organizations/123/locations/global/\
    securityHealthAnalyticsCustomModules/123456
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/manage/custom-modules/sha/delete)

---
### `gcloud scc manage custom-modules sha describe`

Get the details of a Security Health Analytics custom module

Get the details of a Security Health Analytics custom module. It does not
resolve INHERITED enablement states to ENABLED or DISABLED for modules
created at ancestor levels. For example, if the module is enabled at the
ancestor level, modules for all child resources will have the enablement
state set to INHERITED. Use gcloud scc manage custom-modules sha
describe-effective to retrieve a custom module with its effective
enablement state.

**Synopsis:**
```
gcloud scc manage custom-modules sha describe MODULE_ID_OR_NAME
    [--folder=FOLDER_ID | --organization=ORGANIZATION_ID | --parent=PARENT
      | --project=PROJECT_ID_OR_NUMBER] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
MODULE_ID_OR_NAME
   The custom module ID or name. The expected format is
   {parent}/[locations/global]/securityHealthAnalyticsCustomModules/{module_id}
   or just {module_id}. Where module_id is a numeric identifier 1-20
   characters in length. Parent is of the form organizations/{id},
   projects/{id or name}, folders/{id}.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[At most one of these can be specified:]_ Folder associated with the custom module. |
| `--organization` | ORGANIZATION_ID |  | _[At most one of these can be specified:]_ Organization associated with the custom module. |
| `--parent` | PARENT |  | _[At most one of these can be specified:]_ Parent associated with the custom module. Can be one of organizations/<id>, projects/<id or name>, folders/<id> |
| `--project` | PROJECT_ID_OR_NUMBER |  | _[At most one of these can be specified:]_ Project associated with the custom module. |


**Examples:**
```bash
To get the details of a Security Health Analytics custom module with ID
123456 for organization 123, run:

    $ gcloud scc manage custom-modules sha describe 123456 \
        --organization=123

To get the details of a Security Health Analytics custom module with ID
123456 for folder 456, run:

    $ gcloud scc manage custom-modules sha describe 123456 --folder=456

To get the details of a Security Health Analytics custom module with ID
123456 for project 789, run:

    $ gcloud scc manage custom-modules sha describe 123456 --project=789

You can also specify the parent more generally:

    $ gcloud scc manage custom-modules sha describe 123456 \
        --parent=organizations/123

Or just specify the fully qualified module name:

    $ gcloud scc manage custom-modules sha describe \
        organizations/123/locations/global/\
    securityHealthAnalyticsCustomModules/123456
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/manage/custom-modules/sha/describe)

---
### `gcloud scc manage custom-modules sha describe-effective`

Get effective the details of a Security Health Analytics effective custom module

Get the effective details of a Security Health Analytics effective custom
module. It retrieves a custom module with its effective enablement state.

**Synopsis:**
```
gcloud scc manage custom-modules sha describe-effective MODULE_ID_OR_NAME
    [--folder=FOLDER_ID | --organization=ORGANIZATION_ID | --parent=PARENT
      | --project=PROJECT_ID_OR_NUMBER] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
MODULE_ID_OR_NAME
   The custom module ID or name. The expected format is
   {parent}/[locations/global]/effectiveSecurityHealthAnalyticsCustomModules/{module_id}
   or just {module_id}. Where module_id is a numeric identifier 1-20
   characters in length. Parent is of the form organizations/{id},
   projects/{id or name}, folders/{id}.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[At most one of these can be specified:]_ Folder associated with the custom module. |
| `--organization` | ORGANIZATION_ID |  | _[At most one of these can be specified:]_ Organization associated with the custom module. |
| `--parent` | PARENT |  | _[At most one of these can be specified:]_ Parent associated with the custom module. Can be one of organizations/<id>, projects/<id or name>, folders/<id> |
| `--project` | PROJECT_ID_OR_NUMBER |  | _[At most one of these can be specified:]_ Project associated with the custom module. |


**Examples:**
```bash
To get the effective details of a Security Health Analytics custom module
with ID 123456 for organization 123, run:

    $ gcloud scc manage custom-modules sha describe-effective 123456 \
        --organization=123

To get the effective details of a Security Health Analytics custom module
with ID 123456 for folder 456, run:

    $ gcloud scc manage custom-modules sha describe-effective 123456 \
        --folder=456

To get the effective details of a Security Health Analytics custom module
with ID 123456 for project 789, run:

    $ gcloud scc manage custom-modules sha describe-effective 123456 \
        --project=789

You can also specify the parent more generally:

    $ gcloud scc manage custom-modules sha describe-effective 123456 \
        --parent=organizations/123

Or just specify the fully qualified module name:

    $ gcloud scc manage custom-modules sha describe-effective \
        organizations/123/locations/global/\
    effectiveSecurityHealthAnalyticsCustomModules/123456
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/manage/custom-modules/sha/describe-effective)

---
### `gcloud scc manage custom-modules sha list`

List the details of Security Health Analyics custom modules

List the details of the resident and inherited Security Health Analytics
custom modules for the specified folder or project. For an organization,
this command lists only the custom modules that are created at the
organization level. Custom modules created in child folders or projects are
not included in the list. To list the resident custom modules and the
modules that are created in child folders or projects, use gcloud scc
manage custom-modules sha list-descendant.

**Synopsis:**
```
gcloud scc manage custom-modules sha list
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID | --parent=PARENT
      | --project=PROJECT_ID_OR_NUMBER) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[Exactly one of these must be specified:]_ Folder associated with the custom module. |
| `--organization` | ORGANIZATION_ID |  | _[Exactly one of these must be specified:]_ Organization associated with the custom module. |
| `--parent` | PARENT |  | _[Exactly one of these must be specified:]_ Parent associated with the custom module. Can be one of organizations/<id>, projects/<id or name>, folders/<id> |
| `--project` | PROJECT_ID_OR_NUMBER |  | _[Exactly one of these must be specified:]_ Project associated with the custom module. |


**Examples:**
```bash
To list resident and inherited Security Health Analytics custom modules for
organization 123, run:

    $ gcloud scc manage custom-modules sha list \
        --organization=organizations/123

To list resident and inherited Security Health Analytics custom modules for
folder 456, run:

    $ gcloud scc manage custom-modules sha list --folder=folders/456

To list resident and inherited Security Health Analytics custom modules for
project 789, run:

    $ gcloud scc manage custom-modules sha list --project=projects/789

You can also specify the parent more generally:

    $ gcloud scc manage custom-modules sha list 123456 \
        --parent=organizations/123

Or just specify the fully qualified module name:

    $ gcloud scc manage custom-modules sha list \
        organizations/123/locations/global/\
    securityHealthAnalyticsCustomModules/123456
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/manage/custom-modules/sha/list)

---
### `gcloud scc manage custom-modules sha list-descendant`

List the details of the resident and descendant Security Health Analytics custom modules

List the details of the resident and descendant Security Health Analytics
custom modules for a specified organization or folder. For a project, this
command lists only the custom modules that are created in the project.
Modules created in a parent organization or folder are excluded from the
list. To list the resident custom modules and the modules that are
inherited from a parent organization and folder, use gcloud scc manage
custom-modules sha list.

**Synopsis:**
```
gcloud scc manage custom-modules sha list-descendant
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID | --parent=PARENT
      | --project=PROJECT_ID_OR_NUMBER) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[Exactly one of these must be specified:]_ Folder associated with the custom module. |
| `--organization` | ORGANIZATION_ID |  | _[Exactly one of these must be specified:]_ Organization associated with the custom module. |
| `--parent` | PARENT |  | _[Exactly one of these must be specified:]_ Parent associated with the custom module. Can be one of organizations/<id>, projects/<id or name>, folders/<id> |
| `--project` | PROJECT_ID_OR_NUMBER |  | _[Exactly one of these must be specified:]_ Project associated with the custom module. |


**Examples:**
```bash
To list resident and inherited Security Health Analytics custom modules for
organization 123, run:

    $ gcloud scc manage custom-modules sha list-descendant \
        --organization=organizations/123

To list resident and inherited Security Health Analytics custom modules for
folder 456, run:

    $ gcloud scc manage custom-modules sha list-descendant \
        --folder=folders/456

To list resident and inherited Security Health Analytics custom modules for
project 789, run:

    $ gcloud scc manage custom-modules sha list-descendant \
        --project=projects/789
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/manage/custom-modules/sha/list-descendant)

---
### `gcloud scc manage custom-modules sha list-effective`

List the details of an Security Health Analytics effective custom module

List the details of resident and inherited Security Health Analytics custom
modules for the specified folder or project with their effective enablement
states. For an organization, this command lists only the custom modules
that are created at the organization level. Custom modules created in child
folders or projects are not included in the list.

**Synopsis:**
```
gcloud scc manage custom-modules sha list-effective
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID | --parent=PARENT
      | --project=PROJECT_ID_OR_NUMBER) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[Exactly one of these must be specified:]_ Folder associated with the custom module. |
| `--organization` | ORGANIZATION_ID |  | _[Exactly one of these must be specified:]_ Organization associated with the custom module. |
| `--parent` | PARENT |  | _[Exactly one of these must be specified:]_ Parent associated with the custom module. Can be one of organizations/<id>, projects/<id or name>, folders/<id> |
| `--project` | PROJECT_ID_OR_NUMBER |  | _[Exactly one of these must be specified:]_ Project associated with the custom module. |


**Examples:**
```bash
To list resident and inherited Security Health Analytics custom modules
with effective enablement states for organization 123, run:

    $ gcloud scc manage custom-modules sha list-effective \
        --organization=organizations/123

To list resident and inherited effective Security Health Analytics custom
modules with effective enablement states for folder 456, run:

    $ gcloud scc manage custom-modules sha list-effective \
        --folder=folders/456

To list resident and inherited effective Security Health Analytics custom
modules with effective enablement states for project 789, run:

    $ gcloud scc manage custom-modules sha list-effective \
        --project=projects/789
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/manage/custom-modules/sha/list-effective)

---
### `gcloud scc manage custom-modules sha simulate`

Command to simulate a SHA custom module

**Synopsis:**
```
gcloud scc manage custom-modules sha simulate
    --custom-config-from-file=CUSTOM_CONFIG --resource-from-file=TEST_DATA
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID | --parent=PARENT
      | --project=PROJECT_ID_OR_NUMBER) [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--custom-config-from-file` | CUSTOM_CONFIG |  | Path to a YAML custom configuration file. Use a full or relative path to a local file containing the value of custom_config. |
| `--resource-from-file` | TEST_DATA |  | Path to a YAML file that contains the resource data to validate the Security Health Analytics custom module against. Use a full or relative path to a local file containing the value of resource. |


**Examples:**
```bash
To simulate a Security Health Analytics custom module with ID 123456 for
organization 123, run:

    $ gcloud scc manage custom-modules sha simulate 123456 \
        --organization=123 \
        --custom-config-from-file=custom_config.yaml \
        --resource-from-file=test.yaml

To simulate a Security Health Analytics custom module with ID 123456 for
folder 456, run:

    $ gcloud scc manage custom-modules sha simulate 123456 \
        --folder=456 --custom-config-from-file=custom_config.yaml \
        --resource-from-file=test.yaml

To simulate a Security Health Analytics custom module with ID 123456 for
project 789, run:

    $ gcloud scc manage custom-modules sha simulate 123456 \
        --project=789 --custom-config-from-file=custom_config.yaml \
        --resource-from-file=test.yaml

You can also specify the parent more generally:

    $ gcloud scc manage custom-modules sha simulate 123456 \
        --parent=organizations/123 \
        --custom-config-from-file=custom_config.yaml \
        --resource-from-file=test.yaml

Or just specify the fully qualified module name:

    $ gcloud scc manage custom-modules sha simulate \
        organizations/123/locations/global/\
    effectiveSecurityHealthAnalyticsCustomModules/123456 \
        --custom-config-from-file=custom_config.yaml \
        --resource-from-file=test.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/manage/custom-modules/sha/simulate)

---
### `gcloud scc manage custom-modules sha update`

Update a Security Health Analytics custom module

**Synopsis:**
```
gcloud scc manage custom-modules sha update MODULE_ID_OR_NAME
    (--custom-config-file=PATH_TO_FILE --enablement-state=ENABLEMENT_STATE)
    [--validate-only]
    [--folder=FOLDER_ID | --organization=ORGANIZATION_ID | --parent=PARENT
      | --project=PROJECT_ID_OR_NUMBER] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
MODULE_ID_OR_NAME
   The custom module ID or name. The expected format is
   {parent}/[locations/global]/securityHealthAnalyticsCustomModules/{module_id}
   or just {module_id}. Where module_id is a numeric identifier 1-20
   characters in length. Parent is of the form organizations/{id},
   projects/{id or name}, folders/{id}.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--custom-config-file` | PATH_TO_FILE |  | _[At least one of these must be specified:]_ Path to a YAML file that contains the custom config to set for the module. Use a full or relative path to a local file containing the value of custom_config_file. |
| `--enablement-state` | ENABLEMENT_STATE |  | _[At least one of these must be specified:]_ Sets the enablement state of the Security Health Analytics custom module. Valid options are ENABLED, DISABLED, OR INHERITED. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--validate-only` |  |  | If present, the request is validated (including IAM checks) but no action is taken. |


**Examples:**
```bash
To update an Security Health Analytics custom module with ID 123456 for
organization 123, run:

    $ gcloud scc manage custom-modules sha update 123456 \
      --organization=organizations/123 --enablement-state="ENABLED" \
      --custom-config-file=custom_config.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/manage/custom-modules/sha/update)

---

## `gcloud scc manage services` — manage Cloud SCC (Security Command Center) services
### `gcloud scc manage services describe`

Get the details of a Security Command Center service

Get the details of a Security Command Center service. It resolves INHERITED
enablement states to ENABLED or DISABLED for services at ancestor levels.
For example, if the service is enabled at the ancestor level, services for
all child resources will have the enablement state set to ENABLED.

**Synopsis:**
```
gcloud scc manage services describe SERVICE_NAME
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID | --parent=PARENT
      | --project=PROJECT_ID_OR_NUMBER) [--filter-modules=FILTER_MODULES]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SERVICE_NAME
   The service name, provided either in lowercase hyphenated form (e.g.
   security-health-analytics), or in abbreviated form (e.g. sha) if
   applicable.

   The list of supported services is:

   * security-health-analytics (can be abbreviated as sha)

   * event-threat-detection (can be abbreviated as etd)

   * container-threat-detection (can be abbreviated as ctd)

   * vm-threat-detection (can be abbreviated as vmtd)

   * web-security-scanner (can be abbreviated as wss)

   * vm-threat-detection-aws (can be abbreviated as vmtd-aws)

   * cloud-run-threat-detection (can be abbreviated as crtd)

   * vm-manager (can be abbreviated as vmm)

   * ec2-vulnerability-assessment (can be abbreviated as ec2-va)

   * gce-vulnerability-assessment (can be abbreviated as gce-va)

   * azure-vulnerability-assessment (can be abbreviated as azure-va)

   * notebook-security-scanner (can be abbreviated as nss)

   * agent-engine-threat-detection (can be abbreviated as aetd)
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[Exactly one of these must be specified:]_ Folder associated with the custom module. |
| `--organization` | ORGANIZATION_ID |  | _[Exactly one of these must be specified:]_ Organization associated with the custom module. |
| `--parent` | PARENT |  | _[Exactly one of these must be specified:]_ Parent associated with the custom module. Can be one of organizations/<id>, projects/<id or name>, folders/<id> |
| `--project` | PROJECT_ID_OR_NUMBER |  | _[Exactly one of these must be specified:]_ Project associated with the custom module. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--filter-modules` | FILTER_MODULES |  | If provided, only prints module information for modules specified in the list. Provided as a comma separated list of module names in SCREAMING_SNAKE_CASE format (e.g. WEB_UI_ENABLED, API_KEY_NOT_ROTATED). A single module name is also valid. |


**Examples:**
```bash
To get the details of a Security Command Center service with name sha for
organization 123, run:

    $ gcloud scc manage services describe sha --organization=123

To get the details of a Security Command Center service with name sha for
folder 456, run:

    $ gcloud scc manage services describe sha --folder=456

To get the details of a Security Command Center service with ID sha for
project 789, run:

    $ gcloud scc manage services describe sha --project=789

You can also specify the parent more generally:

    $ gcloud scc manage services describe sha --parent=organizations/123

To get the details of modules, [ABC, DEF] of a Security Command Center
service with name sha for organization 123, run:

    $ gcloud scc manage services describe sha --module-list=[ABC, DEF] \
        --organization=123
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/manage/services/describe)

---
### `gcloud scc manage services list`

List the details of Security Command Center services

List the details of Security Command Center services for the specified
folder, project or organization. Services along with their corresponding
module information is returned as the response.

**Synopsis:**
```
gcloud scc manage services list
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID | --parent=PARENT
      | --project=PROJECT_ID_OR_NUMBER) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[Exactly one of these must be specified:]_ Folder associated with the Security Center service. |
| `--organization` | ORGANIZATION_ID |  | _[Exactly one of these must be specified:]_ Organization associated with the Security Center service. |
| `--parent` | PARENT |  | _[Exactly one of these must be specified:]_ Parent associated with the Security Center service. Can be one of organizations/<id>, projects/<id or name>, folders/<id> |
| `--project` | PROJECT_ID_OR_NUMBER |  | _[Exactly one of these must be specified:]_ Project associated with the Security Center service. |


**Examples:**
```bash
To list the Security Center services for organization 123, run:

    $ gcloud scc manage services list --organization=organizations/123

To list Security Center services for folder 456, run:

    $ gcloud scc manage services list --folder=folders/456

To list Security Center services for project 789, run:

    $ gcloud scc manage services list --project=projects/789

You can also specify the parent more generally:

    $ gcloud scc manage services list --parent=organizations/123
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/manage/services/list)

---
### `gcloud scc manage services update`

Update a Security Command Center service

Update the enablement state of the Security Center service and its
corresponding modules for the specified folder, project or organization.

**Synopsis:**
```
gcloud scc manage services update SERVICE_NAME
    (--enablement-state=ENABLEMENT_STATE --module-config-file=PATH_TO_FILE)
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID | --parent=PARENT
      | --project=PROJECT_ID_OR_NUMBER) [--validate-only]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SERVICE_NAME
   The service name, provided either in lowercase hyphenated form (e.g.
   security-health-analytics), or in abbreviated form (e.g. sha) if
   applicable.

   The list of supported services is:

   * security-health-analytics (can be abbreviated as sha)

   * event-threat-detection (can be abbreviated as etd)

   * container-threat-detection (can be abbreviated as ctd)

   * vm-threat-detection (can be abbreviated as vmtd)

   * web-security-scanner (can be abbreviated as wss)

   * vm-threat-detection-aws (can be abbreviated as vmtd-aws)

   * cloud-run-threat-detection (can be abbreviated as crtd)

   * vm-manager (can be abbreviated as vmm)

   * ec2-vulnerability-assessment (can be abbreviated as ec2-va)

   * gce-vulnerability-assessment (can be abbreviated as gce-va)

   * azure-vulnerability-assessment (can be abbreviated as azure-va)

   * notebook-security-scanner (can be abbreviated as nss)

   * agent-engine-threat-detection (can be abbreviated as aetd)
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--enablement-state` | ENABLEMENT_STATE |  | _[At least one of these must be specified:]_ Sets the enablement state of the Security Center service. Valid options are ENABLED, DISABLED, OR INHERITED. The INHERITED state is only valid when setting the enablement state at the project or folder level. |
| `--module-config-file` | PATH_TO_FILE |  | _[At least one of these must be specified:]_ Path to a JSON or YAML file that contains the module config to set for the given module and service. Use a full or relative path to a local file containing the value of module_config_file. |
| `--folder` | FOLDER_ID |  | _[Exactly one of these must be specified:]_ Folder associated with the custom module. |
| `--organization` | ORGANIZATION_ID |  | _[Exactly one of these must be specified:]_ Organization associated with the custom module. |
| `--parent` | PARENT |  | _[Exactly one of these must be specified:]_ Parent associated with the custom module. Can be one of organizations/<id>, projects/<id or name>, folders/<id> |
| `--project` | PROJECT_ID_OR_NUMBER |  | _[Exactly one of these must be specified:]_ Project associated with the custom module. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--validate-only` |  |  | If present, the request is validated (including IAM checks) but no action is taken. |


**Examples:**
```bash
To update a Security Center Service with name sha for organization 123,
run:

    $ gcloud scc manage services update sha \
      --organization=organizations/123 --enablement-state="ENABLED"

To update a Security Center Service with name sha and its modules for
organization 123, run:

    $ gcloud scc manage services update sha \
      --organization=organizations/123 --enablement-state="ENABLED" \
      --module-config-file=module_config.yaml

To validate an update of Security Center Service with name sha and its
modules for organization 123, run:

    $ gcloud scc manage services update sha \
      --organization=organizations/123 --enablement-state="ENABLED" \
      --module-config-file=module_config.yaml --validate-only
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/manage/services/update)

---
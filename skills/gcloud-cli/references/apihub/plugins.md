# gcloud apihub plugins

manage Plugin resources

This file also covers the nested command group `gcloud apihub plugins instances` (manage Plugin Instance resources).

### `gcloud apihub plugins create`

Create a plugin

Create a plugin. Note: The positional argument for Plugin ID is currently not supported. Please use the `--plugin` flag to specify the Plugin ID.

**Synopsis:**
```
gcloud apihub plugins create (PLUGIN : --location=LOCATION)
    --display-name=DISPLAY_NAME
    [--actions-config=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[triggerMode=TRIGGERMODE]]
    [--description=DESCRIPTION]
    [--documentation-external-uri=DOCUMENTATION_EXTERNAL_URI]
    [--gateway-type=GATEWAY_TYPE]
    [--hosting-service-uri=HOSTING_SERVICE_URI]
    [--plugin-category=PLUGIN_CATEGORY]
    [--auth-config-template-supported-types=[AUTH_CONFIG_TEMPLATE_SUPPORTED_TYPES,...]
      --config-template-additional=[description=DESCRIPTION],[enumOptions=ENUMOPTIONS],[id=ID],[multiSelectOptions=MULTISELECTOPTIONS],[required=REQUIRED],[validationRegex=VALIDATIONREGEX],[valueType=VALUETYPE]]
    [--enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      | --json-values=[JSON_VALUES,...]
      | --string-values=[STRING_VALUES,...]
      | --uri-values=[URI_VALUES,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Plugin resource - Identifier. The name of the plugin. Format:
projects/{project}/locations/{location}/plugins/{plugin} The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument plugin on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

  PLUGIN
     ID of the plugin or fully qualified identifier for the plugin.

     To set the plugin attribute:
     + provide the argument plugin on the command line.

  --location=LOCATION
     The location id of the plugin resource.

     To set the location attribute:
     + provide the argument plugin on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | The display name of the plugin. Max length is 50 characters (Unicode code points). |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--actions-config` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[triggerMode=TRIGGERMODE] |  | The configuration of actions supported by the plugin. REQUIRED: This field must be provided when creating or updating a Plugin. Keys: description (the description of the operation performed by the action), displayName (the display name of the action), id (the id of the action), triggerMode (the trigger mode supported by the action). |
| `--description` | DESCRIPTION |  | The plugin description. Max length is 2000 characters (Unicode code points). |
| `--documentation-external-uri` | DOCUMENTATION_EXTERNAL_URI |  | The uri of the externally hosted documentation. |
| `--gateway-type` | GATEWAY_TYPE |  | The type of the gateway. CHOICES: api-discovery, apigee-edge-private-cloud, apigee-edge-public-cloud, apigee-x-and-hybrid, cloud-api-gateway, cloud-endpoints, others. |
| `--hosting-service-uri` | HOSTING_SERVICE_URI |  | The URI of the service implemented by the plugin developer, used to invoke the plugin's functionality. This information is required for user defined plugins. |
| `--plugin-category` | PLUGIN_CATEGORY |  | The category of the plugin, identifying its primary category or purpose. This field is required for all plugins. CHOICES: api-gateway, api-producer. |
| `--auth-config-template-supported-types` | [AUTH_CONFIG_TEMPLATE_SUPPORTED_TYPES,...] |  | The list of authentication types supported by the plugin. CHOICES: api-key, google-service-account, no-auth, oauth2-client-credentials, user-password. |
| `--config-template-additional` | [description=DESCRIPTION],[enumOptions=ENUMOPTIONS],[id=ID],[multiSelectOptions=MULTISELECTOPTIONS],[required=REQUIRED],[validationRegex=VALIDATIONREGEX],[valueType=VALUETYPE] |  | The list of additional configuration variables for the plugin's configuration. Keys: description, enumOptions (options for ENUM value type), id (unique within the configuration), multiSelectOptions (options for MULTI_SELECT value type), required (boolean flag), validationRegex (RE2 syntax), valueType (type of the parameter). |
| `--enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | The attribute values of data type enum. Keys: description (detailed description of the allowed value), displayName (display name of the allowed value), id (4-63 characters, valid characters are /[a-z][0-9]-/), immutable (boolean; when true, the value cannot be changed; system-defined only). Mutually exclusive with --json-values, --string-values, and --uri-values. |
| `--json-values` | [JSON_VALUES,...] |  | The attribute values of data type string or JSON. Mutually exclusive with --enum-values, --string-values, and --uri-values. |
| `--string-values` | [STRING_VALUES,...] |  | The attribute values of data type string or JSON. Mutually exclusive with --enum-values, --json-values, and --uri-values. |
| `--uri-values` | [URI_VALUES,...] |  | The attribute values of data type string or JSON. Mutually exclusive with --enum-values, --json-values, and --string-values. |

**Examples:**
```bash
To create a plugin with the ID my-plugin, run:

    $ gcloud apihub plugins create --plugin=my-plugin \
        --display-name="My Plugin" --type=apigee --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/plugins/create)

---
### `gcloud apihub plugins delete`

Delete a plugin

Delete a plugin.

**Synopsis:**
```
gcloud apihub plugins delete (PLUGIN : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Plugin resource - The name of the Plugin resource to delete. Format:
projects/{project}/locations/{location}/plugins/{plugin} The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument plugin on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PLUGIN
     ID of the plugin or fully qualified identifier for the plugin.

     To set the plugin attribute:
     + provide the argument plugin on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the plugin resource.

     To set the location attribute:
     + provide the argument plugin on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |

**Examples:**
```bash
To delete a plugin with the ID my-plugin, run:

    $ gcloud apihub plugins delete my-plugin --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/plugins/delete)

---
### `gcloud apihub plugins describe`

Describe a plugin

Describe a plugin.

**Synopsis:**
```
gcloud apihub plugins describe (PLUGIN : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Plugin resource - The name of the plugin to retrieve. Format:
projects/{project}/locations/{location}/plugins/{plugin} The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument plugin on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PLUGIN
     ID of the plugin or fully qualified identifier for the plugin.

     To set the plugin attribute:
     + provide the argument plugin on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the plugin resource.

     To set the location attribute:
     + provide the argument plugin on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe a plugin with the ID my-plugin, run:

    $ gcloud apihub plugins describe my-plugin --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/plugins/describe)

---
### `gcloud apihub plugins disable`

Disable a plugin

Disable a plugin.

**Synopsis:**
```
gcloud apihub plugins disable (PLUGIN : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Plugin resource - The name of the plugin to disable. Format:
projects/{project}/locations/{location}/plugins/{plugin} The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument plugin on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PLUGIN
     ID of the plugin or fully qualified identifier for the plugin.

     To set the plugin attribute:
     + provide the argument plugin on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the plugin resource.

     To set the location attribute:
     + provide the argument plugin on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To disable a plugin with the ID my-plugin, run:

    $ gcloud apihub plugins disable my-plugin --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/plugins/disable)

---
### `gcloud apihub plugins enable`

Enable a plugin

Enable a plugin.

**Synopsis:**
```
gcloud apihub plugins enable (PLUGIN : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Plugin resource - The name of the plugin to enable. Format:
projects/{project}/locations/{location}/plugins/{plugin} The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument plugin on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PLUGIN
     ID of the plugin or fully qualified identifier for the plugin.

     To set the plugin attribute:
     + provide the argument plugin on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the plugin resource.

     To set the location attribute:
     + provide the argument plugin on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To enable a plugin with the ID my-plugin, run:

    $ gcloud apihub plugins enable my-plugin --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/plugins/enable)

---
### `gcloud apihub plugins list`

List plugins

List plugins.

**Synopsis:**
```
gcloud apihub plugins list --location=LOCATION [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Location resource - The parent resource where this plugin will be listed. Format: projects/{project}/locations/{location}. ID of the location or fully qualified identifier for the location. To set the project attribute: provide the argument --location on the command line with a fully specified name; provide the argument --project on the command line; set the property core/project. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--filter` | EXPRESSION |  | Apply a Boolean filter EXPRESSION to each resource item to be listed. If the expression evaluates True, then that item is listed. For more details and examples of filter expressions, run $ gcloud topic filters. This flag interacts with other flags that are applied in this order: --flatten, --sort-by, --filter, --limit. |
| `--limit` | LIMIT | unlimited | Maximum number of resources to list. The default is unlimited. This flag interacts with other flags that are applied in this order: --flatten, --sort-by, --filter, --limit. |
| `--page-size` | PAGE_SIZE | determined by service | Some services group resource list output into pages. This flag specifies the maximum number of resources per page. The default is determined by the service if it supports paging, otherwise it is unlimited (no paging). Paging may be applied before or after --filter and --limit depending on the service. |
| `--sort-by` | [FIELD,...] | ascending | Comma-separated list of resource field key names to sort by. The default order is ascending. Prefix a field with "~" for descending order on that field. This flag interacts with other flags that are applied in this order: --flatten, --sort-by, --filter, --limit. |
| `--uri` |  |  | Print a list of resource URIs instead of the default output, and change the command output to a list of URIs. If this flag is used with --format, the formatting is applied on this URI list. To display URIs alongside other keys instead, use the uri() transform. |

**Examples:**
```bash
To list all plugins in project my-project and location us-central1, run:

    $ gcloud apihub plugins list --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/plugins/list)

---
### `gcloud apihub plugins instances create`

Create a plugin instance

Create a plugin instance. Note: The positional argument for Plugin Instance ID is currently not supported. Please use the `--plugin-instance` flag to specify the Plugin Instance ID.

**Synopsis:**
```
gcloud apihub plugins instances create
    (INSTANCE : --location=LOCATION --plugin=PLUGIN)
    --actions=[actionId=ACTIONID],[curationConfig=CURATIONCONFIG],[scheduleCronExpression=SCHEDULECRONEXPRESSION],[scheduleTimeZone=SCHEDULETIMEZONE],[serviceAccount=SERVICEACCOUNT]
    --display-name=DISPLAY_NAME
    [--additional-config=[ADDITIONAL_CONFIG,...]] [--async]
    [--source-environments-config=[SOURCE_ENVIRONMENTS_CONFIG,...]]
    [--source-project-id=SOURCE_PROJECT_ID]
    [--auth-config-type=AUTH_CONFIG_TYPE
      : --api-key-config-http-element-location=API_KEY_CONFIG_HTTP_ELEMENT_LOCATION
      --api-key-config-name=API_KEY_CONFIG_NAME
      --api-key-config-secret-version=API_KEY_CONFIG_SECRET_VERSION
      | --oauth2-client-credentials-config-id=OAUTH2_CLIENT_CREDENTIALS_CONFIG_ID
      --oauth2-client-credentials-config-secret-version=OAUTH2_CLIENT_CREDENTIALS_CONFIG_SECRET_VERSION
      | --user-password-config-secret-version=USER_PASSWORD_CONFIG_SECRET_VERSION
      --user-password-config-username=USER_PASSWORD_CONFIG_USERNAME]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Identifier. The unique name of the plugin instance
resource. Format:
projects/{project}/locations/{location}/plugins/{plugin}/instances/{instance}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

  --location=LOCATION
     The location id of the instance resource.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --plugin=PLUGIN
     The plugin id of the instance resource.

     To set the plugin attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --plugin on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--actions` | [actionId=ACTIONID],[curationConfig=CURATIONCONFIG],[scheduleCronExpression=SCHEDULECRONEXPRESSION],[scheduleTimeZone=SCHEDULETIMEZONE],[serviceAccount=SERVICEACCOUNT] |  | Required, The action status for the plugin instance. Keys: actionId (this should map to one of the action id specified in actions_config in the plugin), curationConfig (this configuration should be provided if the plugin action is publishing data to API hub curate layer), scheduleCronExpression (the schedule for this plugin instance action), scheduleTimeZone (the time zone for the schedule cron expression; if not provided, UTC will be used), serviceAccount (the service account used to publish data). |
| `--display-name` | DISPLAY_NAME |  | The display name for this plugin instance. Max length is 255 characters. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-config` | [ADDITIONAL_CONFIG,...] |  | The additional information for this plugin instance corresponding to the additional config template of the plugin. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--source-environments-config` | [SOURCE_ENVIRONMENTS_CONFIG,...] |  | The source environment's config present in the gateway instance linked to the plugin instance. |
| `--source-project-id` | SOURCE_PROJECT_ID |  | The source project id of the plugin instance. This will be the id of runtime project in case of Google Cloud based plugins. |
| `--auth-config-type` | AUTH_CONFIG_TYPE |  | The authentication type. CHOICES: api-key, google-service-account, no-auth, oauth2-client-credentials, user-password. |
| `--api-key-config-http-element-location` | API_KEY_CONFIG_HTTP_ELEMENT_LOCATION | QUERY | The location of the API key. The default value is QUERY. CHOICES: body, cookie, header, path, query. |
| `--api-key-config-name` | API_KEY_CONFIG_NAME |  | The parameter name of the API key. |
| `--api-key-config-secret-version` | API_KEY_CONFIG_SECRET_VERSION |  | The resource name of the secret version in format: projects/*/secrets/*/versions/* |
| `--oauth2-client-credentials-config-id` | OAUTH2_CLIENT_CREDENTIALS_CONFIG_ID |  | The client identifier. |
| `--oauth2-client-credentials-config-secret-version` | OAUTH2_CLIENT_CREDENTIALS_CONFIG_SECRET_VERSION |  | The resource name of the secret version in format: projects/*/secrets/*/versions/* |
| `--user-password-config-secret-version` | USER_PASSWORD_CONFIG_SECRET_VERSION |  | The resource name of the secret version in format: projects/*/secrets/*/versions/* |
| `--user-password-config-username` | USER_PASSWORD_CONFIG_USERNAME |  | Username. |

**Examples:**
```bash
To create a plugin instance with the ID my-instance for plugin my-plugin,
run:

    $ gcloud apihub plugins instances create --plugin-instance=my-instance \
        --plugin=my-plugin --display-name="My Instance" \
        --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/plugins/instances/create)

---
### `gcloud apihub plugins instances delete`

Delete a plugin instance

Delete a plugin instance.

**Synopsis:**
```
gcloud apihub plugins instances delete
    (INSTANCE : --location=LOCATION --plugin=PLUGIN) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The name of the plugin instance to delete. Format:
projects/{project}/locations/{location}/plugins/{plugin}/instances/{instance}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the instance resource.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --plugin=PLUGIN
     The plugin id of the instance resource.

     To set the plugin attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --plugin on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |

**Examples:**
```bash
To delete a plugin instance with the ID my-instance for plugin my-plugin,
run:

    $ gcloud apihub plugins instances delete my-instance \
        --plugin=my-plugin --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/plugins/instances/delete)

---
### `gcloud apihub plugins instances describe`

Describe a plugin instance

Describe a plugin instance.

**Synopsis:**
```
gcloud apihub plugins instances describe
    (INSTANCE : --location=LOCATION --plugin=PLUGIN) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The name of the plugin instance to retrieve. Format:
projects/{project}/locations/{location}/plugins/{plugin}/instances/{instance}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the instance resource.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --plugin=PLUGIN
     The plugin id of the instance resource.

     To set the plugin attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --plugin on the command line.
```

**Examples:**
```bash
To describe a plugin instance with the ID my-instance for plugin
my-plugin, run:

    $ gcloud apihub plugins instances describe my-instance \
        --plugin=my-plugin --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/plugins/instances/describe)

---
### `gcloud apihub plugins instances list`

List plugin instances

List plugin instances.

**Synopsis:**
```
gcloud apihub plugins instances list (--plugin=PLUGIN : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--plugin` | PLUGIN |  | ID of the plugin or fully qualified identifier for the plugin. To set the plugin attribute: provide the argument --plugin on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | The location id of the plugin resource. To set the location attribute: provide the argument --plugin on the command line with a fully specified name; provide the argument --location on the command line. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--filter` | EXPRESSION |  | Apply a Boolean filter EXPRESSION to each resource item to be listed. If the expression evaluates True, then that item is listed. For more details and examples of filter expressions, run $ gcloud topic filters. This flag interacts with other flags that are applied in this order: --flatten, --sort-by, --filter, --limit. |
| `--limit` | LIMIT | unlimited | Maximum number of resources to list. The default is unlimited. This flag interacts with other flags that are applied in this order: --flatten, --sort-by, --filter, --limit. |
| `--page-size` | PAGE_SIZE | determined by service | Some services group resource list output into pages. This flag specifies the maximum number of resources per page. The default is determined by the service if it supports paging, otherwise it is unlimited (no paging). Paging may be applied before or after --filter and --limit depending on the service. |
| `--sort-by` | [FIELD,...] | ascending | Comma-separated list of resource field key names to sort by. The default order is ascending. Prefix a field with "~" for descending order on that field. This flag interacts with other flags that are applied in this order: --flatten, --sort-by, --filter, --limit. |
| `--uri` |  |  | Print a list of resource URIs instead of the default output, and change the command output to a list of URIs. If this flag is used with --format, the formatting is applied on this URI list. To display URIs alongside other keys instead, use the uri() transform. |

**Examples:**
```bash
To list all plugin instances for plugin my-plugin, run:

    $ gcloud apihub plugins instances list --plugin=my-plugin \
        --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/plugins/instances/list)

---
### `gcloud apihub plugins instances manage-source-data`

Manage pluginInstances

Manage pluginInstances.

**Synopsis:**
```
gcloud apihub plugins instances manage-source-data
    (INSTANCE : --location=LOCATION --plugin=PLUGIN) --action=ACTION
    --data=DATA --data-type=DATA_TYPE --relative-path=RELATIVE_PATH
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The name of the plugin instance for which data needs
to be managed. Format:
projects/{project}/locations/{location}/plugins/{plugin}/instances/{instance}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the instance resource.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --plugin=PLUGIN
     The plugin id of the instance resource.

     To set the plugin attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --plugin on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--action` | ACTION |  | Action to be performed. CHOICES: delete (Delete data), upload (Upload or upsert data). |
| `--data` | DATA |  | Data to be managed. |
| `--data-type` | DATA_TYPE |  | Type of data to be managed. CHOICES: environment-manifest (Environment manifest), proxy-bundle (Proxy bundle), proxy-deployment-manifest (Proxy deployment manifest), shared-flow-bundle (Shared flow bundle). |
| `--relative-path` | RELATIVE_PATH |  | Relative path of data being managed for a given plugin instance. |

**Examples:**
```bash
To manage all pluginInstances, run:

    $ gcloud apihub plugins instances manage-source-data
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/plugins/instances/manage-source-data)

---
### `gcloud apihub plugins instances update`

Update a plugin instance

Update a plugin instance.

**Synopsis:**
```
gcloud apihub plugins instances update
    (INSTANCE : --location=LOCATION --plugin=PLUGIN)
    [--display-name=DISPLAY_NAME] [--source-project-id=SOURCE_PROJECT_ID]
    [--actions=[actionId=ACTIONID],[curationConfig=CURATIONCONFIG],[scheduleCronExpression=SCHEDULECRONEXPRESSION],[scheduleTimeZone=SCHEDULETIMEZONE],[serviceAccount=SERVICEACCOUNT]
      | --add-actions=[actionId=ACTIONID],[curationConfig=CURATIONCONFIG],[scheduleCronExpression=SCHEDULECRONEXPRESSION],[scheduleTimeZone=SCHEDULETIMEZONE],[serviceAccount=SERVICEACCOUNT]
      | --clear-actions
      | --remove-actions=[actionId=ACTIONID],[curationConfig=CURATIONCONFIG],[scheduleCronExpression=SCHEDULECRONEXPRESSION],[scheduleTimeZone=SCHEDULETIMEZONE],[serviceAccount=SERVICEACCOUNT]]
    [--additional-config=[ADDITIONAL_CONFIG,...]
      | --update-additional-config=[UPDATE_ADDITIONAL_CONFIG,...]
      | --clear-additional-config
      | --remove-additional-config=REMOVE_ADDITIONAL_CONFIG]
    [--auth-config-type=AUTH_CONFIG_TYPE --clear-auth-config
      --api-key-config-http-element-location=API_KEY_CONFIG_HTTP_ELEMENT_LOCATION
      --api-key-config-name=API_KEY_CONFIG_NAME
      --api-key-config-secret-version=API_KEY_CONFIG_SECRET_VERSION
      | --oauth2-client-credentials-config-id=OAUTH2_CLIENT_CREDENTIALS_CONFIG_ID
      --oauth2-client-credentials-config-secret-version=OAUTH2_CLIENT_CREDENTIALS_CONFIG_SECRET_VERSION
      | --user-password-config-secret-version=USER_PASSWORD_CONFIG_SECRET_VERSION
      --user-password-config-username=USER_PASSWORD_CONFIG_USERNAME]
    [--source-environments-config=[SOURCE_ENVIRONMENTS_CONFIG,...]
      | --update-source-environments-config=[UPDATE_SOURCE_ENVIRONMENTS_CONFIG,...]
      | --clear-source-environments-config
      | --remove-source-environments-config=REMOVE_SOURCE_ENVIRONMENTS_CONFIG]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Identifier. The unique name of the plugin instance
resource. Format:
projects/{project}/locations/{location}/plugins/{plugin}/instances/{instance}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the instance resource.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --plugin=PLUGIN
     The plugin id of the instance resource.

     To set the plugin attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --plugin on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | The display name for this plugin instance. Max length is 255 characters. |
| `--source-project-id` | SOURCE_PROJECT_ID |  | The source project id of the plugin instance. This will be the id of runtime project in case of Google Cloud based plugins and org id in case of non-Google Cloud based plugins. |
| `--actions` | [actionId=ACTIONID],[curationConfig=CURATIONCONFIG],[scheduleCronExpression=SCHEDULECRONEXPRESSION],[scheduleTimeZone=SCHEDULETIMEZONE],[serviceAccount=SERVICEACCOUNT] |  | Set actions to new value. The action status for the plugin instance. Keys: actionId (this should map to one of the action id specified in actions_config in the plugin), curationConfig (this configuration should be provided if the plugin action is publishing data to API hub curate layer), scheduleCronExpression (the schedule for this plugin instance action), scheduleTimeZone (the time zone for the schedule cron expression; if not provided, UTC will be used), serviceAccount (the service account used to publish data). Mutually exclusive with --add-actions, --clear-actions, and --remove-actions. |
| `--add-actions` | [actionId=ACTIONID],... |  | Add new value to actions list. The action status for the plugin instance. Mutually exclusive with --actions, --clear-actions, and --remove-actions. |
| `--clear-actions` |  |  | Clear actions value and set to empty list. Mutually exclusive with --actions, --add-actions, and --remove-actions. |
| `--remove-actions` | [actionId=ACTIONID],... |  | Remove existing value from actions list. The action status for the plugin instance. Mutually exclusive with --actions, --add-actions, and --clear-actions. |
| `--additional-config` | [ADDITIONAL_CONFIG,...] |  | Set additional_config to new value. The additional information for this plugin instance corresponding to the additional config template of the plugin. Mutually exclusive with --update-additional-config, --clear-additional-config, and --remove-additional-config. |
| `--update-additional-config` | [UPDATE_ADDITIONAL_CONFIG,...] |  | Update additional_config value or add key value pair. Mutually exclusive with --additional-config, --clear-additional-config, and --remove-additional-config. |
| `--clear-additional-config` |  |  | Clear additional_config value and set to empty map. Mutually exclusive with --additional-config, --update-additional-config, and --remove-additional-config. |
| `--remove-additional-config` | REMOVE_ADDITIONAL_CONFIG |  | Remove existing value from map additional_config. Mutually exclusive with --additional-config, --update-additional-config, and --clear-additional-config. |
| `--auth-config-type` | AUTH_CONFIG_TYPE |  | The authentication type. CHOICES: api-key, google-service-account, no-auth, oauth2-client-credentials, user-password. |
| `--clear-auth-config` |  |  | Set googleCloudApihubV1PluginInstance.authConfig back to default value. |
| `--api-key-config-http-element-location` | API_KEY_CONFIG_HTTP_ELEMENT_LOCATION | QUERY | The location of the API key. The default value is QUERY. CHOICES: body, cookie, header, path, query. |
| `--api-key-config-name` | API_KEY_CONFIG_NAME |  | The parameter name of the API key. |
| `--api-key-config-secret-version` | API_KEY_CONFIG_SECRET_VERSION |  | The resource name of the secret version in format: projects/*/secrets/*/versions/* |
| `--oauth2-client-credentials-config-id` | OAUTH2_CLIENT_CREDENTIALS_CONFIG_ID |  | The client identifier. |
| `--oauth2-client-credentials-config-secret-version` | OAUTH2_CLIENT_CREDENTIALS_CONFIG_SECRET_VERSION |  | The resource name of the secret version in format: projects/*/secrets/*/versions/* |
| `--user-password-config-secret-version` | USER_PASSWORD_CONFIG_SECRET_VERSION |  | The resource name of the secret version in format: projects/*/secrets/*/versions/* |
| `--user-password-config-username` | USER_PASSWORD_CONFIG_USERNAME |  | Username. |
| `--source-environments-config` | [SOURCE_ENVIRONMENTS_CONFIG,...] |  | Set source_environments_config to new value. The source environment's config present in the gateway instance linked to the plugin instance. Mutually exclusive with --update-source-environments-config, --clear-source-environments-config, and --remove-source-environments-config. |
| `--update-source-environments-config` | [UPDATE_SOURCE_ENVIRONMENTS_CONFIG,...] |  | Update source_environments_config value or add key value pair. Mutually exclusive with --source-environments-config, --clear-source-environments-config, and --remove-source-environments-config. |
| `--clear-source-environments-config` |  |  | Clear source_environments_config value and set to empty map. Mutually exclusive with --source-environments-config, --update-source-environments-config, and --remove-source-environments-config. |
| `--remove-source-environments-config` | REMOVE_SOURCE_ENVIRONMENTS_CONFIG |  | Remove existing value from map source_environments_config. Mutually exclusive with --source-environments-config, --update-source-environments-config, and --clear-source-environments-config. |

**Examples:**
```bash
To update the display name of a plugin instance with the ID my-instance,
run:

    $ gcloud apihub plugins instances update my-instance \
        --plugin=my-plugin --display-name="New Instance Name" \
        --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/plugins/instances/update)

---

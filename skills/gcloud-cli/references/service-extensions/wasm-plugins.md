# gcloud service-extensions wasm-plugins

interact with and manage Service Extensions WasmPlugins

### `gcloud service-extensions wasm-plugins create`

Create a WasmPlugin resource

Create a new WasmPlugin resource.

**Synopsis:**
```
gcloud service-extensions wasm-plugins create
    (WASM_PLUGIN : --location=LOCATION) [--async]
    [--description=DESCRIPTION] [--labels=[KEY=VALUE,...]]
    [--log-config=[LOG_CONFIG,...]]
    [--image=IMAGE
      --main-version=MAIN_VERSION --plugin-config=PLUGIN_CONFIG
      | --plugin-config-file=PATH_TO_FILE
      | --plugin-config-uri=PLUGIN_CONFIG_URI] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
WasmPlugin resource - The ID of the WasmPlugin resource to create. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument wasm_plugin on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  WASM_PLUGIN
     ID of the WasmPlugin or fully qualified identifier for the
     WasmPlugin.

     To set the wasm_plugin attribute:
     + provide the argument wasm_plugin on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location ID.

     To set the location attribute:
     + provide the argument wasm_plugin on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + use global location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | A human-readable description of the resource. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--log-config` | [LOG_CONFIG,...] |  | Logging options for the activity performed by this plugin. The following options can be set: * enable: whether to enable logging. If log-config flag is set, enable option is required. * sample-rate: configures the sampling rate of activity logs, where 1.0 means all logged activity is reported and 0.0 means no activity is reported. The default value is 1.0, and the value of the field must be in range 0 to 1 (inclusive). * min-log-level: specifies the lowest level of the logs that should be exported to Cloud Logging. The default value is INFO. Example usage: --log-config=enable=True,sample-rate=0.5,min-log-level=INFO --log_config=enable=False |
| `--image` | IMAGE |  | URI of the container image containing the plugin's Wasm module, stored in the Artifact Registry. |
| `--main-version` | MAIN_VERSION |  | ID of the WasmPluginVersion resource that will be created for that WasmPlugin and that will be set as the current main version. |


**Examples:**
```bash
To create a WasmPlugin called my-plugin, together with a new version called
v1, and set it as main, run:

    $ gcloud service-extensions wasm-plugins create my-plugin \
        --main-version=v1 \
        --image=...-docker.pkg.dev/my-project/repository/container:tag
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-extensions/wasm-plugins/create)

---
### `gcloud service-extensions wasm-plugins delete`

Delete a WasmPlugin resource

Delete a WasmPlugin resource.

Please note that all WasmPluginVersions associated with the WasmPlugin will
also be deleted.

**Synopsis:**
```
gcloud service-extensions wasm-plugins delete
    (WASM_PLUGIN : --location=LOCATION) [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
WasmPlugin resource - The WasmPlugin resource to delete. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument wasm_plugin on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  WASM_PLUGIN
     ID of the WasmPlugin or fully qualified identifier for the
     WasmPlugin.

     To set the wasm_plugin attribute:
     + provide the argument wasm_plugin on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location ID.

     To set the location attribute:
     + provide the argument wasm_plugin on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + use global location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a WasmPlugin called my-plugin, run:

    $ gcloud service-extensions wasm-plugins delete my-plugin
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-extensions/wasm-plugins/delete)

---
### `gcloud service-extensions wasm-plugins describe`

Show details about a WasmPlugin resource

Show details about a WasmPlugin resource.

**Synopsis:**
```
gcloud service-extensions wasm-plugins describe
    (WASM_PLUGIN : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
WasmPlugin resource - The WasmPlugin resource that you want to describe.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument wasm_plugin on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  WASM_PLUGIN
     ID of the WasmPlugin or fully qualified identifier for the
     WasmPlugin.

     To set the wasm_plugin attribute:
     + provide the argument wasm_plugin on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location ID.

     To set the location attribute:
     + provide the argument wasm_plugin on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + use global location.
```

**Examples:**
```bash
To show details about a WasmPlugin, run:

    $ gcloud service-extensions wasm-plugins describe my-plugin
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-extensions/wasm-plugins/describe)

---
### `gcloud service-extensions wasm-plugins list`

List all WasmPlugin resources

List WasmPlugin resources.

**Synopsis:**
```
gcloud service-extensions wasm-plugins list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + use global location. |


**Examples:**
```bash
To list existing WasmPlugin resources, run:

    $ gcloud service-extensions wasm-plugins list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-extensions/wasm-plugins/list)

---
### `gcloud service-extensions wasm-plugins update`

Update a WasmPlugin resource

Update an existing WasmPlugin resource and optionally create a
WasmPluginVersion resource and set it as the main (serving) one.

If --image is not specified:
  o the method only updates the WasmPlugin resource without creating a
    WasmPluginVersion.
  o the --plugin-config*** flags are disallowed.
  o if --main-version is set, then the referenced WasmPluginVersion must
    already exist and it is set as the main (serving) one.

If --image is specified:
  o the --main-version flag must also be specified.
  o the method updates the WasmPlugin resource and creates a new
    WasmPluginVersion with --main-version name and sets it as the main
    (serving) one.
  o the --plugin-config*** flags are allowed.
  o the --async flag is disallowed.

**Synopsis:**
```
gcloud service-extensions wasm-plugins update
    (WASM_PLUGIN : --location=LOCATION) [--async]
    [--description=DESCRIPTION] [--labels=[KEY=VALUE,...]]
    [--log-config=[LOG_CONFIG,...]]
    [--image=IMAGE
      --main-version=MAIN_VERSION --plugin-config=PLUGIN_CONFIG
      | --plugin-config-file=PATH_TO_FILE
      | --plugin-config-uri=PLUGIN_CONFIG_URI] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
WasmPlugin resource - The ID of the WasmPlugin to update. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument wasm_plugin on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  WASM_PLUGIN
     ID of the WasmPlugin or fully qualified identifier for the
     WasmPlugin.

     To set the wasm_plugin attribute:
     + provide the argument wasm_plugin on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location ID.

     To set the location attribute:
     + provide the argument wasm_plugin on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + use global location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | A human-readable description of the resource. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--log-config` | [LOG_CONFIG,...] |  | Logging options for the activity performed by this plugin. The following options can be set: * enable: whether to enable logging. If log-config flag is set, enable option is required. * sample-rate: configures the sampling rate of activity logs, where 1.0 means all logged activity is reported and 0.0 means no activity is reported. The default value is 1.0, and the value of the field must be in range 0 to 1 (inclusive). * min-log-level: specifies the lowest level of the logs that should be exported to Cloud Logging. The default value is INFO. Example usage: --log-config=enable=True,sample-rate=0.5,min-log-level=INFO --log_config=enable=False |
| `--image` | IMAGE |  | URI of the container image containing the plugin's Wasm module, stored in the Artifact Registry. |
| `--main-version` | MAIN_VERSION |  | The ID of the WasmPluginVersion that should be the currently serving one. The version referred to must be a child of this WasmPlugin. If the --image flag was also provided, the WasmPluginVersion will be created for that WasmPlugin and will be set as the current main version. |


**Examples:**
```bash
To update a WasmPlugin called my-plugin, run:

    $ gcloud service-extensions wasm-plugins update my-plugin \
        --main-version=new-version --description="A new description." \
        --labels=label1=value1

To update a WasmPlugin called my-plugin and also create a new version
called v1 and set it as main:

    $ gcloud service-extensions wasm-plugins update my-plugin \
        --main-version=v1 --description="A new description." \
        --labels=label1=value1 \
        --image=...-docker.pkg.dev/my-project/repository/container:tag
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-extensions/wasm-plugins/update)

---
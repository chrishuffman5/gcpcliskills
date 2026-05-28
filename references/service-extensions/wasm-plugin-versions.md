# gcloud service-extensions wasm-plugin-versions

interact with and manage Service Extensions WasmPluginVersions

### `gcloud service-extensions wasm-plugin-versions create`

Create a WasmPluginVersion resource

Create a new WasmPluginVersion resource.

**Synopsis:**
```
gcloud service-extensions wasm-plugin-versions create
    (WASM_PLUGIN_VERSION : --location=LOCATION --wasm-plugin=WASM_PLUGIN)
    --image=IMAGE [--async] [--description=DESCRIPTION]
    [--labels=[KEY=VALUE,...]]
    [--plugin-config=PLUGIN_CONFIG | --plugin-config-file=PATH_TO_FILE
      | --plugin-config-uri=PLUGIN_CONFIG_URI] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
WasmPluginVersion resource - The ID of the WasmPluginVersion resource to
create. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument wasm_plugin_version on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  WASM_PLUGIN_VERSION
     ID of the WasmPluginVersion or fully qualified identifier for the
     WasmPluginVersion.

     To set the wasm_plugin_version attribute:
     + provide the argument wasm_plugin_version on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location ID.

     To set the location attribute:
     + provide the argument wasm_plugin_version on the command line with
       a fully specified name;
     + provide the argument --location on the command line;
     + use global location.

  --wasm-plugin=WASM_PLUGIN
     The ID of the WasmPlugin.

     To set the wasm-plugin attribute:
     + provide the argument wasm_plugin_version on the command line with
       a fully specified name;
     + provide the argument --wasm-plugin on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--image` | IMAGE |  | URI of the image containing the plugin's Wasm module, stored in the Artifact Registry. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | A human-readable description of the resource. |
| `--labels` | [KEY=VALUE,...] |  | List of KEY=VALUE labels to attach to this resource. |


**Examples:**
```bash
To create a WasmPluginVersion called my-plugin-version, run:

    $ gcloud service-extensions wasm-plugin-versions create \
        my-plugin-version --wasm-plugin=my-plugin \
        --image=...-docker.pkg.dev/my-project/repository/container:tag
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-extensions/wasm-plugin-versions/create)

---
### `gcloud service-extensions wasm-plugin-versions delete`

Delete a WasmPluginVersion resource

Delete a WasmPluginVersion resource.

**Synopsis:**
```
gcloud service-extensions wasm-plugin-versions delete
    (WASM_PLUGIN_VERSION : --location=LOCATION --wasm-plugin=WASM_PLUGIN)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
WasmPluginVersion resource - The WasmPluginVersion resource to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument wasm_plugin_version on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  WASM_PLUGIN_VERSION
     ID of the WasmPluginVersion or fully qualified identifier for the
     WasmPluginVersion.

     To set the wasm_plugin_version attribute:
     + provide the argument wasm_plugin_version on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location ID.

     To set the location attribute:
     + provide the argument wasm_plugin_version on the command line with
       a fully specified name;
     + provide the argument --location on the command line;
     + use global location.

  --wasm-plugin=WASM_PLUGIN
     The ID of the WasmPlugin.

     To set the wasm-plugin attribute:
     + provide the argument wasm_plugin_version on the command line with
       a fully specified name;
     + provide the argument --wasm-plugin on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a WasmPluginVersion called 'my-plugin-version', run:

    $ gcloud service-extensions wasm-plugin-versions delete \
        my-plugin-version
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-extensions/wasm-plugin-versions/delete)

---
### `gcloud service-extensions wasm-plugin-versions describe`

Show details about a WasmPluginVersion resource

Show details about a WasmPluginVersion resource.

**Synopsis:**
```
gcloud service-extensions wasm-plugin-versions describe
    (WASM_PLUGIN_VERSION : --location=LOCATION --wasm-plugin=WASM_PLUGIN)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
WasmPluginVersion resource - The WasmPluginVersion resource that you want
to describe. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument wasm_plugin_version on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  WASM_PLUGIN_VERSION
     ID of the WasmPluginVersion or fully qualified identifier for the
     WasmPluginVersion.

     To set the wasm_plugin_version attribute:
     + provide the argument wasm_plugin_version on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location ID.

     To set the location attribute:
     + provide the argument wasm_plugin_version on the command line with
       a fully specified name;
     + provide the argument --location on the command line;
     + use global location.

  --wasm-plugin=WASM_PLUGIN
     The ID of the WasmPlugin.

     To set the wasm-plugin attribute:
     + provide the argument wasm_plugin_version on the command line with
       a fully specified name;
     + provide the argument --wasm-plugin on the command line.
```

**Examples:**
```bash
To show details about a WasmPluginVersion, run:

    $ gcloud service-extensions wasm-plugin-versions describe \
        my-plugin-version
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-extensions/wasm-plugin-versions/describe)

---
### `gcloud service-extensions wasm-plugin-versions list`

List all WasmPluginVersion resources for a WasmPlugin

List WasmPluginVersion resources.

**Synopsis:**
```
gcloud service-extensions wasm-plugin-versions list
    (--wasm-plugin=WASM_PLUGIN : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--wasm-plugin` | WASM_PLUGIN |  | _[This must be specified.]_ ID of the WasmPlugin or fully qualified identifier for the WasmPlugin. To set the wasm-plugin attribute: + provide the argument --wasm-plugin on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The location ID. To set the location attribute: + provide the argument --wasm-plugin on the command line with a fully specified name; + provide the argument --location on the command line; + use global location. |


**Examples:**
```bash
To list existing WasmPluginVersion resources, run:

    $ gcloud service-extensions wasm-plugin-versions list \
        --wasm-plugin=WASM_PLUGIN
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-extensions/wasm-plugin-versions/list)

---
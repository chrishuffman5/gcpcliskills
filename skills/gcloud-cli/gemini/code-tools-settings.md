# gcloud gemini code-tools-settings

manage Code Tools Setting resources

### `gcloud gemini code-tools-settings create`

Create codeToolsSettings

Create a codeToolsSetting

**Synopsis:**
```
gcloud gemini code-tools-settings create
    (CODE_TOOLS_SETTING : --location=LOCATION)
    --enabled-tool=[accountConnector=ACCOUNTCONNECTOR],
      [config=CONFIG],[handle=HANDLE],[tool=TOOL],[uriOverride=URIOVERRIDE]
    [--labels=[LABELS,...]] [--request-id=REQUEST_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CodeToolsSetting resource - Identifier. Name of the resource.
Format:projects/{project}/locations/{location}/codeToolsSettings/{codeToolsSetting}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument code_tools_setting on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CODE_TOOLS_SETTING
     ID of the codeToolsSetting or fully qualified identifier for the
     codeToolsSetting.

     To set the code_tools_setting attribute:
     + provide the argument code_tools_setting on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the codeToolsSetting resource.

     To set the location attribute:
     + provide the argument code_tools_setting on the command line with
       a fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--enabled-tool` | [accountConnector=ACCOUNTCONNECTOR],[config=CONFIG],[handle=HANDLE],[tool=TOOL],[uriOverride=URIOVERRIDE] |  | Required, Represents the full set of enabled tools. accountConnector Link to the Dev Connect Account Connector that holds the user credentials. projects/{project}/locations/{location}/accountConnectors/{account_connector_id}. config Configuration parameters for the tool. key Key of the configuration item. value Value of the configuration item. handle Handle used to invoke the tool. tool Link to the Tool. uriOverride Overridden URI, if allowed by Tool. Shorthand Example: --enabled-tool=accountConnector=string,config=[{key=string,value=string}],handle=string,tool=string,uriOverride=string --enabled-tool=accountConnector=string,config=[{key=string,value=string}],handle=string,tool=string,uriOverride=string JSON Example: --enabled-tool='[{"accountConnector": "string", "config": [{"key": "string", "value": "string"}], "handle": "string", "tool": "string", "uriOverride": "string"}]' File Example: --enabled-tool=path_to_file.(yaml\|json) |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--labels` | [LABELS,...] |  | Labels as key value pairs. KEY Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. VALUE Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Shorthand Example: --labels=string=string JSON Example: --labels='{"string": "string"}' File Example: --labels=path_to_file.(yaml\|json) |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes since the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To create the codeToolsSetting, run:

    $ gcloud gemini code-tools-settings create
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/code-tools-settings/create)

---
### `gcloud gemini code-tools-settings delete`

Delete codeToolsSettings

Delete a codeToolsSetting

**Synopsis:**
```
gcloud gemini code-tools-settings delete
    (CODE_TOOLS_SETTING : --location=LOCATION) [--force]
    [--request-id=REQUEST_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CodeToolsSetting resource - Name of the resource The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument code_tools_setting on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CODE_TOOLS_SETTING
     ID of the codeToolsSetting or fully qualified identifier for the
     codeToolsSetting.

     To set the code_tools_setting attribute:
     + provide the argument code_tools_setting on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the codeToolsSetting resource.

     To set the location attribute:
     + provide the argument code_tools_setting on the command line with
       a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--force` |  |  | If set to true, any code tools settings from this publisher will also be deleted. (Otherwise, the request will only work if the publisher has no books.) |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes after the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To delete the codeToolsSetting, run:

    $ gcloud gemini code-tools-settings delete
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/code-tools-settings/delete)

---
### `gcloud gemini code-tools-settings describe`

Describe codeToolsSettings

Describe a codeToolsSetting

**Synopsis:**
```
gcloud gemini code-tools-settings describe
    (CODE_TOOLS_SETTING : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CodeToolsSetting resource - Name of the resource. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument code_tools_setting on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CODE_TOOLS_SETTING
     ID of the codeToolsSetting or fully qualified identifier for the
     codeToolsSetting.

     To set the code_tools_setting attribute:
     + provide the argument code_tools_setting on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the codeToolsSetting resource.

     To set the location attribute:
     + provide the argument code_tools_setting on the command line with
       a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe the codeToolsSetting, run:

    $ gcloud gemini code-tools-settings describe
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/code-tools-settings/describe)

---
### `gcloud gemini code-tools-settings list`

List codeToolsSettings

**Synopsis:**
```
gcloud gemini code-tools-settings list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all codeToolsSettings, run:

    $ gcloud gemini code-tools-settings list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/code-tools-settings/list)

---
### `gcloud gemini code-tools-settings update`

Update codeToolsSettings

Update a codeToolsSetting

**Synopsis:**
```
gcloud gemini code-tools-settings update
    (CODE_TOOLS_SETTING : --location=LOCATION) [--request-id=REQUEST_ID]
    [--enabled-tool=[accountConnector=ACCOUNTCONNECTOR],
      [config=CONFIG],[handle=HANDLE],[tool=TOOL],[uriOverride=URIOVERRIDE]
      | --add-enabled-tool=[accountConnector=ACCOUNTCONNECTOR],
      [config=CONFIG],[handle=HANDLE],[tool=TOOL],[uriOverride=URIOVERRIDE]
      --clear-enabled-tool
      | --remove-enabled-tool=[accountConnector=ACCOUNTCONNECTOR],
      [config=CONFIG],
      [handle=HANDLE],[tool=TOOL],[uriOverride=URIOVERRIDE]]
    [--labels=[LABELS,...]
      | --update-labels=[UPDATE_LABELS,...] --clear-labels
      | --remove-labels=REMOVE_LABELS] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CodeToolsSetting resource - Identifier. Name of the resource.
Format:projects/{project}/locations/{location}/codeToolsSettings/{codeToolsSetting}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument code_tools_setting on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CODE_TOOLS_SETTING
     ID of the codeToolsSetting or fully qualified identifier for the
     codeToolsSetting.

     To set the code_tools_setting attribute:
     + provide the argument code_tools_setting on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the codeToolsSetting resource.

     To set the location attribute:
     + provide the argument code_tools_setting on the command line with
       a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes since the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To update the codeToolsSetting, run:

    $ gcloud gemini code-tools-settings update
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/code-tools-settings/update)

---

## `gcloud gemini code-tools-settings setting-bindings` — manage Setting Binding resources
### `gcloud gemini code-tools-settings setting-bindings create`

Create settingBindings

Create a settingBinding

**Synopsis:**
```
gcloud gemini code-tools-settings setting-bindings create
    (SETTING_BINDING
      : --code-tools-setting=CODE_TOOLS_SETTING --location=LOCATION)
    --target=TARGET [--async] [--labels=[LABELS,...]] [--product=PRODUCT]
    [--request-id=REQUEST_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SettingBinding resource - Identifier. Name of the resource.
Format:projects/{project}/locations/{location}/{settingType}/{setting}/settingBindings/{setting_binding}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument setting_binding on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SETTING_BINDING
     ID of the settingBinding or fully qualified identifier for the
     settingBinding.

     To set the setting_binding attribute:
     + provide the argument setting_binding on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --code-tools-setting=CODE_TOOLS_SETTING
     The codeToolsSetting id of the settingBinding resource.

     To set the code-tools-setting attribute:
     + provide the argument setting_binding on the command line with a
       fully specified name;
     + provide the argument --code-tools-setting on the command line.

  --location=LOCATION
     The location id of the settingBinding resource.

     To set the location attribute:
     + provide the argument setting_binding on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--target` | TARGET |  | Target of the binding. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--labels` | [LABELS,...] |  | Labels as key value pairs. KEY Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. VALUE Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Shorthand Example: --labels=string=string JSON Example: --labels='{"string": "string"}' File Example: --labels=path_to_file.(yaml\|json) |
| `--product` | one of: gemini-cloud-assist Gemini Cloud Assist |  | Product type of the setting binding. PRODUCT must be one of: gemini-cloud-assist Gemini Cloud Assist. gemini-code-assist Gemini Code Assist. gemini-in-bigquery Gemini in BigQuery. gemini-in-looker Gemini in Looker. |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes since the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To create the settingBinding, run:

    $ gcloud gemini code-tools-settings setting-bindings create
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/code-tools-settings/setting-bindings/create)

---
### `gcloud gemini code-tools-settings setting-bindings delete`

Delete settingBindings

Delete a settingBinding

**Synopsis:**
```
gcloud gemini code-tools-settings setting-bindings delete
    (SETTING_BINDING
      : --code-tools-setting=CODE_TOOLS_SETTING --location=LOCATION)
    [--async] [--request-id=REQUEST_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SettingBinding resource - Name of the resource. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument setting_binding on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SETTING_BINDING
     ID of the settingBinding or fully qualified identifier for the
     settingBinding.

     To set the setting_binding attribute:
     + provide the argument setting_binding on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --code-tools-setting=CODE_TOOLS_SETTING
     The codeToolsSetting id of the settingBinding resource.

     To set the code-tools-setting attribute:
     + provide the argument setting_binding on the command line with a
       fully specified name;
     + provide the argument --code-tools-setting on the command line.

  --location=LOCATION
     The location id of the settingBinding resource.

     To set the location attribute:
     + provide the argument setting_binding on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes after the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To delete the settingBinding, run:

    $ gcloud gemini code-tools-settings setting-bindings delete
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/code-tools-settings/setting-bindings/delete)

---
### `gcloud gemini code-tools-settings setting-bindings describe`

Describe settingBindings

Describe a settingBinding

**Synopsis:**
```
gcloud gemini code-tools-settings setting-bindings describe
    (SETTING_BINDING
      : --code-tools-setting=CODE_TOOLS_SETTING --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SettingBinding resource - Name of the resource. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument setting_binding on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SETTING_BINDING
     ID of the settingBinding or fully qualified identifier for the
     settingBinding.

     To set the setting_binding attribute:
     + provide the argument setting_binding on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --code-tools-setting=CODE_TOOLS_SETTING
     The codeToolsSetting id of the settingBinding resource.

     To set the code-tools-setting attribute:
     + provide the argument setting_binding on the command line with a
       fully specified name;
     + provide the argument --code-tools-setting on the command line.

  --location=LOCATION
     The location id of the settingBinding resource.

     To set the location attribute:
     + provide the argument setting_binding on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe the settingBinding, run:

    $ gcloud gemini code-tools-settings setting-bindings describe
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/code-tools-settings/setting-bindings/describe)

---
### `gcloud gemini code-tools-settings setting-bindings list`

List settingBindings

**Synopsis:**
```
gcloud gemini code-tools-settings setting-bindings list
    (--code-tools-setting=CODE_TOOLS_SETTING : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--code-tools-setting` | CODE_TOOLS_SETTING |  | _[This must be specified.]_ ID of the codeToolsSetting or fully qualified identifier for the codeToolsSetting. To set the code-tools-setting attribute: + provide the argument --code-tools-setting on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The location id of the codeToolsSetting resource. To set the location attribute: + provide the argument --code-tools-setting on the command line with a fully specified name; + provide the argument --location on the command line. |


**Examples:**
```bash
To list all settingBindings, run:

    $ gcloud gemini code-tools-settings setting-bindings list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/code-tools-settings/setting-bindings/list)

---
### `gcloud gemini code-tools-settings setting-bindings update`

Update settingBindings

Update a settingBinding

**Synopsis:**
```
gcloud gemini code-tools-settings setting-bindings update
    (SETTING_BINDING
      : --code-tools-setting=CODE_TOOLS_SETTING --location=LOCATION)
    [--async] [--product=PRODUCT] [--request-id=REQUEST_ID]
    [--target=TARGET]
    [--labels=[LABELS,...]
      | --update-labels=[UPDATE_LABELS,...] --clear-labels
      | --remove-labels=REMOVE_LABELS] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SettingBinding resource - Identifier. Name of the resource.
Format:projects/{project}/locations/{location}/{settingType}/{setting}/settingBindings/{setting_binding}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument setting_binding on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SETTING_BINDING
     ID of the settingBinding or fully qualified identifier for the
     settingBinding.

     To set the setting_binding attribute:
     + provide the argument setting_binding on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --code-tools-setting=CODE_TOOLS_SETTING
     The codeToolsSetting id of the settingBinding resource.

     To set the code-tools-setting attribute:
     + provide the argument setting_binding on the command line with a
       fully specified name;
     + provide the argument --code-tools-setting on the command line.

  --location=LOCATION
     The location id of the settingBinding resource.

     To set the location attribute:
     + provide the argument setting_binding on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--product` | one of: gemini-cloud-assist Gemini Cloud Assist |  | Product type of the setting binding. PRODUCT must be one of: gemini-cloud-assist Gemini Cloud Assist. gemini-code-assist Gemini Code Assist. gemini-in-bigquery Gemini in BigQuery. gemini-in-looker Gemini in Looker. |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes since the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |
| `--target` | TARGET |  | Target of the binding. |


**Examples:**
```bash
To update the settingBinding, run:

    $ gcloud gemini code-tools-settings setting-bindings update
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/code-tools-settings/setting-bindings/update)

---
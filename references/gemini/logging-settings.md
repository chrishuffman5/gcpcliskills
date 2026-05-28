# gcloud gemini logging-settings

manage Logging Setting resources

### `gcloud gemini logging-settings create`

Create loggingSettings

Create a loggingSetting

**Synopsis:**
```
gcloud gemini logging-settings create
    (LOGGING_SETTING : --location=LOCATION) [--labels=[LABELS,...]]
    [--log-metadata] [--log-prompts-and-responses]
    [--request-id=REQUEST_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
LoggingSetting resource - Identifier. Name of the resource.
Format:projects/{project}/locations/{location}/loggingsettings/{loggingsetting}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument logging_setting on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  LOGGING_SETTING
     ID of the loggingSetting or fully qualified identifier for the
     loggingSetting.

     To set the logging_setting attribute:
     + provide the argument logging_setting on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the loggingSetting resource.

     To set the location attribute:
     + provide the argument logging_setting on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--labels` | [LABELS,...] |  | Labels as key value pairs. KEY Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. VALUE Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Shorthand Example: --labels=string=string JSON Example: --labels='{"string": "string"}' File Example: --labels=path_to_file.(yaml\|json) |
| `--log-metadata` |  |  | Whether to log metadata. |
| `--log-prompts-and-responses` |  |  | Whether to log prompts and responses. |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes since the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To create the loggingSetting, run:

    $ gcloud gemini logging-settings create
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/logging-settings/create)

---
### `gcloud gemini logging-settings delete`

Delete loggingSettings

Delete a loggingSetting

**Synopsis:**
```
gcloud gemini logging-settings delete
    (LOGGING_SETTING : --location=LOCATION) [--request-id=REQUEST_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
LoggingSetting resource - Name of the resource. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument logging_setting on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  LOGGING_SETTING
     ID of the loggingSetting or fully qualified identifier for the
     loggingSetting.

     To set the logging_setting attribute:
     + provide the argument logging_setting on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the loggingSetting resource.

     To set the location attribute:
     + provide the argument logging_setting on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes after the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To delete the loggingSetting, run:

    $ gcloud gemini logging-settings delete
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/logging-settings/delete)

---
### `gcloud gemini logging-settings describe`

Describe loggingSettings

Describe a loggingSetting

**Synopsis:**
```
gcloud gemini logging-settings describe
    (LOGGING_SETTING : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
LoggingSetting resource - Name of the resource. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument logging_setting on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  LOGGING_SETTING
     ID of the loggingSetting or fully qualified identifier for the
     loggingSetting.

     To set the logging_setting attribute:
     + provide the argument logging_setting on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the loggingSetting resource.

     To set the location attribute:
     + provide the argument logging_setting on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe the loggingSetting, run:

    $ gcloud gemini logging-settings describe
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/logging-settings/describe)

---
### `gcloud gemini logging-settings list`

List loggingSettings

**Synopsis:**
```
gcloud gemini logging-settings list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all loggingSettings, run:

    $ gcloud gemini logging-settings list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/logging-settings/list)

---
### `gcloud gemini logging-settings update`

Update loggingSettings

Update a loggingSetting

**Synopsis:**
```
gcloud gemini logging-settings update
    (LOGGING_SETTING : --location=LOCATION) [--[no-]log-metadata]
    [--[no-]log-prompts-and-responses] [--request-id=REQUEST_ID]
    [--labels=[LABELS,...]
      | --update-labels=[UPDATE_LABELS,...] --clear-labels
      | --remove-labels=REMOVE_LABELS] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
LoggingSetting resource - Identifier. Name of the resource.
Format:projects/{project}/locations/{location}/loggingsettings/{loggingsetting}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument logging_setting on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  LOGGING_SETTING
     ID of the loggingSetting or fully qualified identifier for the
     loggingSetting.

     To set the logging_setting attribute:
     + provide the argument logging_setting on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the loggingSetting resource.

     To set the location attribute:
     + provide the argument logging_setting on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--[no-]log-metadata` |  |  | Whether to log metadata. Use --log-metadata to enable and --no-log-metadata to disable. |
| `--[no-]log-prompts-and-responses` |  |  | Whether to log prompts and responses. Use --log-prompts-and-responses to enable and --no-log-prompts-and-responses to disable. |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes since the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To update the loggingSetting, run:

    $ gcloud gemini logging-settings update
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/logging-settings/update)

---

## `gcloud gemini logging-settings setting-bindings` — manage Setting Binding resources
### `gcloud gemini logging-settings setting-bindings create`

Create settingBindings

Create a settingBinding

**Synopsis:**
```
gcloud gemini logging-settings setting-bindings create
    (SETTING_BINDING
      : --location=LOCATION --logging-setting=LOGGING_SETTING)
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

  --location=LOCATION
     The location id of the settingBinding resource.

     To set the location attribute:
     + provide the argument setting_binding on the command line with a
       fully specified name;
     + provide the argument --location on the command line.

  --logging-setting=LOGGING_SETTING
     The loggingSetting id of the settingBinding resource.

     To set the logging-setting attribute:
     + provide the argument setting_binding on the command line with a
       fully specified name;
     + provide the argument --logging-setting on the command line.
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

    $ gcloud gemini logging-settings setting-bindings create
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/logging-settings/setting-bindings/create)

---
### `gcloud gemini logging-settings setting-bindings delete`

Delete settingBindings

Delete a settingBinding

**Synopsis:**
```
gcloud gemini logging-settings setting-bindings delete
    (SETTING_BINDING
      : --location=LOCATION --logging-setting=LOGGING_SETTING) [--async]
    [--request-id=REQUEST_ID] [GCLOUD_WIDE_FLAG ...]
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

  --location=LOCATION
     The location id of the settingBinding resource.

     To set the location attribute:
     + provide the argument setting_binding on the command line with a
       fully specified name;
     + provide the argument --location on the command line.

  --logging-setting=LOGGING_SETTING
     The loggingSetting id of the settingBinding resource.

     To set the logging-setting attribute:
     + provide the argument setting_binding on the command line with a
       fully specified name;
     + provide the argument --logging-setting on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes after the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To delete the settingBinding, run:

    $ gcloud gemini logging-settings setting-bindings delete
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/logging-settings/setting-bindings/delete)

---
### `gcloud gemini logging-settings setting-bindings describe`

Describe settingBindings

Describe a settingBinding

**Synopsis:**
```
gcloud gemini logging-settings setting-bindings describe
    (SETTING_BINDING
      : --location=LOCATION --logging-setting=LOGGING_SETTING)
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

  --location=LOCATION
     The location id of the settingBinding resource.

     To set the location attribute:
     + provide the argument setting_binding on the command line with a
       fully specified name;
     + provide the argument --location on the command line.

  --logging-setting=LOGGING_SETTING
     The loggingSetting id of the settingBinding resource.

     To set the logging-setting attribute:
     + provide the argument setting_binding on the command line with a
       fully specified name;
     + provide the argument --logging-setting on the command line.
```

**Examples:**
```bash
To describe the settingBinding, run:

    $ gcloud gemini logging-settings setting-bindings describe
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/logging-settings/setting-bindings/describe)

---
### `gcloud gemini logging-settings setting-bindings list`

List settingBindings

**Synopsis:**
```
gcloud gemini logging-settings setting-bindings list
    (--logging-setting=LOGGING_SETTING : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--logging-setting` | LOGGING_SETTING |  | _[This must be specified.]_ ID of the loggingSetting or fully qualified identifier for the loggingSetting. To set the logging-setting attribute: + provide the argument --logging-setting on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The location id of the loggingSetting resource. To set the location attribute: + provide the argument --logging-setting on the command line with a fully specified name; + provide the argument --location on the command line. |


**Examples:**
```bash
To list all settingBindings, run:

    $ gcloud gemini logging-settings setting-bindings list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/logging-settings/setting-bindings/list)

---
### `gcloud gemini logging-settings setting-bindings update`

Update settingBindings

Update a settingBinding

**Synopsis:**
```
gcloud gemini logging-settings setting-bindings update
    (SETTING_BINDING
      : --location=LOCATION --logging-setting=LOGGING_SETTING) [--async]
    [--product=PRODUCT] [--request-id=REQUEST_ID] [--target=TARGET]
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

  --location=LOCATION
     The location id of the settingBinding resource.

     To set the location attribute:
     + provide the argument setting_binding on the command line with a
       fully specified name;
     + provide the argument --location on the command line.

  --logging-setting=LOGGING_SETTING
     The loggingSetting id of the settingBinding resource.

     To set the logging-setting attribute:
     + provide the argument setting_binding on the command line with a
       fully specified name;
     + provide the argument --logging-setting on the command line.
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

    $ gcloud gemini logging-settings setting-bindings update
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/logging-settings/setting-bindings/update)

---
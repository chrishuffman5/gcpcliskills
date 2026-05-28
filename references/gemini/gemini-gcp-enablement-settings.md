# gcloud gemini gemini-gcp-enablement-settings

manage Gemini Gcp Enablement Setting resources

### `gcloud gemini gemini-gcp-enablement-settings create`

Create geminiGcpEnablementSettings

Create a geminiGcpEnablementSetting

**Synopsis:**
```
gcloud gemini gemini-gcp-enablement-settings create
    (GEMINI_GCP_ENABLEMENT_SETTING : --location=LOCATION)
    [--disable-web-grounding] [--enable-customer-data-sharing]
    [--labels=[LABELS,...]] [--request-id=REQUEST_ID]
    [--web-grounding-type=WEB_GROUNDING_TYPE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
GeminiGcpEnablementSetting resource - Identifier. Name of the resource.
Format:projects/{project}/locations/{location}/geminiGcpEnablementSettings/{geminiGcpEnablementSetting}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument gemini_gcp_enablement_setting on the command
   line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GEMINI_GCP_ENABLEMENT_SETTING
     ID of the geminiGcpEnablementSetting or fully qualified identifier
     for the geminiGcpEnablementSetting.

     To set the gemini_gcp_enablement_setting attribute:
     + provide the argument gemini_gcp_enablement_setting on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the geminiGcpEnablementSetting resource.

     To set the location attribute:
     + provide the argument gemini_gcp_enablement_setting on the command
       line with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--disable-web-grounding` |  |  | Whether web grounding should be disabled. DEPRECATED: Use web_grounding_type instead. |
| `--enable-customer-data-sharing` |  |  | Not implemented. |
| `--labels` | [LABELS,...] |  | Labels as key value pairs. KEY Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. VALUE Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Shorthand Example: --labels=string=string JSON Example: --labels='{"string": "string"}' File Example: --labels=path_to_file.(yaml\|json) |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes since the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |
| `--web-grounding-type` | one of: grounding-with-google-search Grounding with Google Search |  | Web grounding type. WEB_GROUNDING_TYPE must be one of: grounding-with-google-search Grounding with Google Search. web-grounding-for-enterprise Grounding with Google Search for Enterprise. |


**Examples:**
```bash
To create the geminiGcpEnablementSetting, run:

    $ gcloud gemini gemini-gcp-enablement-settings create
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/gemini-gcp-enablement-settings/create)

---
### `gcloud gemini gemini-gcp-enablement-settings delete`

Delete geminiGcpEnablementSettings

Delete a geminiGcpEnablementSetting

**Synopsis:**
```
gcloud gemini gemini-gcp-enablement-settings delete
    (GEMINI_GCP_ENABLEMENT_SETTING : --location=LOCATION)
    [--request-id=REQUEST_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
GeminiGcpEnablementSetting resource - Name of the resource The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument gemini_gcp_enablement_setting on the command
   line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GEMINI_GCP_ENABLEMENT_SETTING
     ID of the geminiGcpEnablementSetting or fully qualified identifier
     for the geminiGcpEnablementSetting.

     To set the gemini_gcp_enablement_setting attribute:
     + provide the argument gemini_gcp_enablement_setting on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the geminiGcpEnablementSetting resource.

     To set the location attribute:
     + provide the argument gemini_gcp_enablement_setting on the command
       line with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes after the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To delete the geminiGcpEnablementSetting, run:

    $ gcloud gemini gemini-gcp-enablement-settings delete
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/gemini-gcp-enablement-settings/delete)

---
### `gcloud gemini gemini-gcp-enablement-settings describe`

Describe geminiGcpEnablementSettings

Describe a geminiGcpEnablementSetting

**Synopsis:**
```
gcloud gemini gemini-gcp-enablement-settings describe
    (GEMINI_GCP_ENABLEMENT_SETTING : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
GeminiGcpEnablementSetting resource - Name of the resource. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument gemini_gcp_enablement_setting on the command
   line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GEMINI_GCP_ENABLEMENT_SETTING
     ID of the geminiGcpEnablementSetting or fully qualified identifier
     for the geminiGcpEnablementSetting.

     To set the gemini_gcp_enablement_setting attribute:
     + provide the argument gemini_gcp_enablement_setting on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the geminiGcpEnablementSetting resource.

     To set the location attribute:
     + provide the argument gemini_gcp_enablement_setting on the command
       line with a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe the geminiGcpEnablementSetting, run:

    $ gcloud gemini gemini-gcp-enablement-settings describe
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/gemini-gcp-enablement-settings/describe)

---
### `gcloud gemini gemini-gcp-enablement-settings list`

List geminiGcpEnablementSettings

**Synopsis:**
```
gcloud gemini gemini-gcp-enablement-settings list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all geminiGcpEnablementSettings, run:

    $ gcloud gemini gemini-gcp-enablement-settings list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/gemini-gcp-enablement-settings/list)

---
### `gcloud gemini gemini-gcp-enablement-settings update`

Update geminiGcpEnablementSettings

Update a geminiGcpEnablementSetting

**Synopsis:**
```
gcloud gemini gemini-gcp-enablement-settings update
    (GEMINI_GCP_ENABLEMENT_SETTING : --location=LOCATION)
    [--[no-]disable-web-grounding] [--[no-]enable-customer-data-sharing]
    [--request-id=REQUEST_ID] [--web-grounding-type=WEB_GROUNDING_TYPE]
    [--labels=[LABELS,...]
      | --update-labels=[UPDATE_LABELS,...] --clear-labels
      | --remove-labels=REMOVE_LABELS] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
GeminiGcpEnablementSetting resource - Identifier. Name of the resource.
Format:projects/{project}/locations/{location}/geminiGcpEnablementSettings/{geminiGcpEnablementSetting}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument gemini_gcp_enablement_setting on the command
   line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GEMINI_GCP_ENABLEMENT_SETTING
     ID of the geminiGcpEnablementSetting or fully qualified identifier
     for the geminiGcpEnablementSetting.

     To set the gemini_gcp_enablement_setting attribute:
     + provide the argument gemini_gcp_enablement_setting on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the geminiGcpEnablementSetting resource.

     To set the location attribute:
     + provide the argument gemini_gcp_enablement_setting on the command
       line with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--[no-]disable-web-grounding` |  |  | Whether web grounding should be disabled. DEPRECATED: Use web_grounding_type instead. Use --disable-web-grounding to enable and --no-disable-web-grounding to disable. |
| `--[no-]enable-customer-data-sharing` |  |  | Not implemented. Use --enable-customer-data-sharing to enable and --no-enable-customer-data-sharing to disable. |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes since the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |
| `--web-grounding-type` | one of: grounding-with-google-search Grounding with Google Search |  | Web grounding type. WEB_GROUNDING_TYPE must be one of: grounding-with-google-search Grounding with Google Search. web-grounding-for-enterprise Grounding with Google Search for Enterprise. |


**Examples:**
```bash
To update the geminiGcpEnablementSetting, run:

    $ gcloud gemini gemini-gcp-enablement-settings update
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/gemini-gcp-enablement-settings/update)

---

## `gcloud gemini gemini-gcp-enablement-settings setting-bindings` — manage Setting Binding resources
### `gcloud gemini gemini-gcp-enablement-settings setting-bindings create`

Create settingBindings

Create a settingBinding

**Synopsis:**
```
gcloud gemini gemini-gcp-enablement-settings setting-bindings create
    (SETTING_BINDING
      : --gemini-gcp-enablement-setting=GEMINI_GCP_ENABLEMENT_SETTING
      --location=LOCATION) --target=TARGET [--async]
    [--labels=[LABELS,...]] [--product=PRODUCT] [--request-id=REQUEST_ID]
    [GCLOUD_WIDE_FLAG ...]
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

  --gemini-gcp-enablement-setting=GEMINI_GCP_ENABLEMENT_SETTING
     The geminiGcpEnablementSetting id of the settingBinding resource.

     To set the gemini-gcp-enablement-setting attribute:
     + provide the argument setting_binding on the command line with a
       fully specified name;
     + provide the argument --gemini-gcp-enablement-setting on the
       command line.

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

    $ gcloud gemini gemini-gcp-enablement-settings setting-bindings \
      create
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/gemini-gcp-enablement-settings/setting-bindings/create)

---
### `gcloud gemini gemini-gcp-enablement-settings setting-bindings delete`

Delete settingBindings

Delete a settingBinding

**Synopsis:**
```
gcloud gemini gemini-gcp-enablement-settings setting-bindings delete
    (SETTING_BINDING
      : --gemini-gcp-enablement-setting=GEMINI_GCP_ENABLEMENT_SETTING
      --location=LOCATION) [--async] [--request-id=REQUEST_ID]
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

  --gemini-gcp-enablement-setting=GEMINI_GCP_ENABLEMENT_SETTING
     The geminiGcpEnablementSetting id of the settingBinding resource.

     To set the gemini-gcp-enablement-setting attribute:
     + provide the argument setting_binding on the command line with a
       fully specified name;
     + provide the argument --gemini-gcp-enablement-setting on the
       command line.

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

    $ gcloud gemini gemini-gcp-enablement-settings setting-bindings \
      delete
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/gemini-gcp-enablement-settings/setting-bindings/delete)

---
### `gcloud gemini gemini-gcp-enablement-settings setting-bindings describe`

Describe settingBindings

Describe a settingBinding

**Synopsis:**
```
gcloud gemini gemini-gcp-enablement-settings setting-bindings describe
    (SETTING_BINDING
      : --gemini-gcp-enablement-setting=GEMINI_GCP_ENABLEMENT_SETTING
      --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
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

  --gemini-gcp-enablement-setting=GEMINI_GCP_ENABLEMENT_SETTING
     The geminiGcpEnablementSetting id of the settingBinding resource.

     To set the gemini-gcp-enablement-setting attribute:
     + provide the argument setting_binding on the command line with a
       fully specified name;
     + provide the argument --gemini-gcp-enablement-setting on the
       command line.

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

    $ gcloud gemini gemini-gcp-enablement-settings setting-bindings \
      describe
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/gemini-gcp-enablement-settings/setting-bindings/describe)

---
### `gcloud gemini gemini-gcp-enablement-settings setting-bindings list`

List settingBindings

**Synopsis:**
```
gcloud gemini gemini-gcp-enablement-settings setting-bindings list
    (--gemini-gcp-enablement-setting=GEMINI_GCP_ENABLEMENT_SETTING
      : --location=LOCATION) [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--gemini-gcp-enablement-setting` | GEMINI_GCP_ENABLEMENT_SETTING |  | _[This must be specified.]_ ID of the geminiGcpEnablementSetting or fully qualified identifier for the geminiGcpEnablementSetting. To set the gemini-gcp-enablement-setting attribute: + provide the argument --gemini-gcp-enablement-setting on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The location id of the geminiGcpEnablementSetting resource. To set the location attribute: + provide the argument --gemini-gcp-enablement-setting on the command line with a fully specified name; + provide the argument --location on the command line. |


**Examples:**
```bash
To list all settingBindings, run:

    $ gcloud gemini gemini-gcp-enablement-settings setting-bindings list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/gemini-gcp-enablement-settings/setting-bindings/list)

---
### `gcloud gemini gemini-gcp-enablement-settings setting-bindings update`

Update settingBindings

Update a settingBinding

**Synopsis:**
```
gcloud gemini gemini-gcp-enablement-settings setting-bindings update
    (SETTING_BINDING
      : --gemini-gcp-enablement-setting=GEMINI_GCP_ENABLEMENT_SETTING
      --location=LOCATION) [--async] [--product=PRODUCT]
    [--request-id=REQUEST_ID] [--target=TARGET]
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

  --gemini-gcp-enablement-setting=GEMINI_GCP_ENABLEMENT_SETTING
     The geminiGcpEnablementSetting id of the settingBinding resource.

     To set the gemini-gcp-enablement-setting attribute:
     + provide the argument setting_binding on the command line with a
       fully specified name;
     + provide the argument --gemini-gcp-enablement-setting on the
       command line.

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

    $ gcloud gemini gemini-gcp-enablement-settings setting-bindings \
      update
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/gemini-gcp-enablement-settings/setting-bindings/update)

---
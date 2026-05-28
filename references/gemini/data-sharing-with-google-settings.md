# gcloud gemini data-sharing-with-google-settings

manage Data Sharing With Google Setting resources

### `gcloud gemini data-sharing-with-google-settings create`

Create dataSharingWithGoogleSettings

Create a dataSharingWithGoogleSetting

**Synopsis:**
```
gcloud gemini data-sharing-with-google-settings create
    (DATA_SHARING_WITH_GOOGLE_SETTING : --location=LOCATION)
    [--enable-data-sharing] [--enable-preview-data-sharing]
    [--labels=[LABELS,...]] [--request-id=REQUEST_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DataSharingWithGoogleSetting resource - Identifier. Name of the resource.
Format:projects/{project}/locations/{location}/dataSharingWithGoogleSettings/{dataSharingWithGoogleSetting}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument data_sharing_with_google_setting on the command
   line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATA_SHARING_WITH_GOOGLE_SETTING
     ID of the dataSharingWithGoogleSetting or fully qualified identifier
     for the dataSharingWithGoogleSetting.

     To set the data_sharing_with_google_setting attribute:
     + provide the argument data_sharing_with_google_setting on the
       command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the dataSharingWithGoogleSetting resource.

     To set the location attribute:
     + provide the argument data_sharing_with_google_setting on the
       command line with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--enable-data-sharing` |  |  | Whether data sharing should be enabled in GA products. |
| `--enable-preview-data-sharing` |  |  | Whether data sharing should be enabled in Preview products. |
| `--labels` | [LABELS,...] |  | Labels as key value pairs. KEY Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. VALUE Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Shorthand Example: --labels=string=string JSON Example: --labels='{"string": "string"}' File Example: --labels=path_to_file.(yaml\|json) |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes since the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To create the dataSharingWithGoogleSetting, run:

    $ gcloud gemini data-sharing-with-google-settings create
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/data-sharing-with-google-settings/create)

---
### `gcloud gemini data-sharing-with-google-settings delete`

Delete dataSharingWithGoogleSettings

Delete a dataSharingWithGoogleSetting

**Synopsis:**
```
gcloud gemini data-sharing-with-google-settings delete
    (DATA_SHARING_WITH_GOOGLE_SETTING : --location=LOCATION)
    [--request-id=REQUEST_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DataSharingWithGoogleSetting resource - Name of the resource The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument data_sharing_with_google_setting on the command
   line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATA_SHARING_WITH_GOOGLE_SETTING
     ID of the dataSharingWithGoogleSetting or fully qualified identifier
     for the dataSharingWithGoogleSetting.

     To set the data_sharing_with_google_setting attribute:
     + provide the argument data_sharing_with_google_setting on the
       command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the dataSharingWithGoogleSetting resource.

     To set the location attribute:
     + provide the argument data_sharing_with_google_setting on the
       command line with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes after the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To delete the dataSharingWithGoogleSetting, run:

    $ gcloud gemini data-sharing-with-google-settings delete
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/data-sharing-with-google-settings/delete)

---
### `gcloud gemini data-sharing-with-google-settings describe`

Describe dataSharingWithGoogleSettings

Describe a dataSharingWithGoogleSetting

**Synopsis:**
```
gcloud gemini data-sharing-with-google-settings describe
    (DATA_SHARING_WITH_GOOGLE_SETTING : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DataSharingWithGoogleSetting resource - Name of the resource. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument data_sharing_with_google_setting on the command
   line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATA_SHARING_WITH_GOOGLE_SETTING
     ID of the dataSharingWithGoogleSetting or fully qualified identifier
     for the dataSharingWithGoogleSetting.

     To set the data_sharing_with_google_setting attribute:
     + provide the argument data_sharing_with_google_setting on the
       command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the dataSharingWithGoogleSetting resource.

     To set the location attribute:
     + provide the argument data_sharing_with_google_setting on the
       command line with a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe the dataSharingWithGoogleSetting, run:

    $ gcloud gemini data-sharing-with-google-settings describe
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/data-sharing-with-google-settings/describe)

---
### `gcloud gemini data-sharing-with-google-settings list`

List dataSharingWithGoogleSettings

**Synopsis:**
```
gcloud gemini data-sharing-with-google-settings list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all dataSharingWithGoogleSettings, run:

    $ gcloud gemini data-sharing-with-google-settings list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/data-sharing-with-google-settings/list)

---
### `gcloud gemini data-sharing-with-google-settings update`

Update dataSharingWithGoogleSettings

Update a dataSharingWithGoogleSetting

**Synopsis:**
```
gcloud gemini data-sharing-with-google-settings update
    (DATA_SHARING_WITH_GOOGLE_SETTING : --location=LOCATION)
    [--[no-]enable-data-sharing] [--[no-]enable-preview-data-sharing]
    [--request-id=REQUEST_ID]
    [--labels=[LABELS,...]
      | --update-labels=[UPDATE_LABELS,...] --clear-labels
      | --remove-labels=REMOVE_LABELS] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DataSharingWithGoogleSetting resource - Identifier. Name of the resource.
Format:projects/{project}/locations/{location}/dataSharingWithGoogleSettings/{dataSharingWithGoogleSetting}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument data_sharing_with_google_setting on the command
   line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATA_SHARING_WITH_GOOGLE_SETTING
     ID of the dataSharingWithGoogleSetting or fully qualified identifier
     for the dataSharingWithGoogleSetting.

     To set the data_sharing_with_google_setting attribute:
     + provide the argument data_sharing_with_google_setting on the
       command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the dataSharingWithGoogleSetting resource.

     To set the location attribute:
     + provide the argument data_sharing_with_google_setting on the
       command line with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--[no-]enable-data-sharing` |  |  | Whether data sharing should be enabled in GA products. Use --enable-data-sharing to enable and --no-enable-data-sharing to disable. |
| `--[no-]enable-preview-data-sharing` |  |  | Whether data sharing should be enabled in Preview products. Use --enable-preview-data-sharing to enable and --no-enable-preview-data-sharing to disable. |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes since the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To update the dataSharingWithGoogleSetting, run:

    $ gcloud gemini data-sharing-with-google-settings update
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/data-sharing-with-google-settings/update)

---

## `gcloud gemini data-sharing-with-google-settings setting-bindings` — manage Setting Binding resources
### `gcloud gemini data-sharing-with-google-settings setting-bindings create`

Create settingBindings

Create a settingBinding

**Synopsis:**
```
gcloud gemini data-sharing-with-google-settings setting-bindings create
    (SETTING_BINDING
      : --data-sharing-with-google-setting=DATA_SHARING_WITH_GOOGLE_SETTING
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

  --data-sharing-with-google-setting=DATA_SHARING_WITH_GOOGLE_SETTING
     The dataSharingWithGoogleSetting id of the settingBinding resource.

     To set the data-sharing-with-google-setting attribute:
     + provide the argument setting_binding on the command line with a
       fully specified name;
     + provide the argument --data-sharing-with-google-setting on the
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

    $ gcloud gemini data-sharing-with-google-settings setting-bindings \
      create
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/data-sharing-with-google-settings/setting-bindings/create)

---
### `gcloud gemini data-sharing-with-google-settings setting-bindings delete`

Delete settingBindings

Delete a settingBinding

**Synopsis:**
```
gcloud gemini data-sharing-with-google-settings setting-bindings delete
    (SETTING_BINDING
      : --data-sharing-with-google-setting=DATA_SHARING_WITH_GOOGLE_SETTING
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

  --data-sharing-with-google-setting=DATA_SHARING_WITH_GOOGLE_SETTING
     The dataSharingWithGoogleSetting id of the settingBinding resource.

     To set the data-sharing-with-google-setting attribute:
     + provide the argument setting_binding on the command line with a
       fully specified name;
     + provide the argument --data-sharing-with-google-setting on the
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

    $ gcloud gemini data-sharing-with-google-settings setting-bindings \
      delete
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/data-sharing-with-google-settings/setting-bindings/delete)

---
### `gcloud gemini data-sharing-with-google-settings setting-bindings describe`

Describe settingBindings

Describe a settingBinding

**Synopsis:**
```
gcloud gemini data-sharing-with-google-settings setting-bindings describe
    (SETTING_BINDING
      : --data-sharing-with-google-setting=DATA_SHARING_WITH_GOOGLE_SETTING
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

  --data-sharing-with-google-setting=DATA_SHARING_WITH_GOOGLE_SETTING
     The dataSharingWithGoogleSetting id of the settingBinding resource.

     To set the data-sharing-with-google-setting attribute:
     + provide the argument setting_binding on the command line with a
       fully specified name;
     + provide the argument --data-sharing-with-google-setting on the
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

    $ gcloud gemini data-sharing-with-google-settings setting-bindings \
      describe
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/data-sharing-with-google-settings/setting-bindings/describe)

---
### `gcloud gemini data-sharing-with-google-settings setting-bindings list`

List settingBindings

**Synopsis:**
```
gcloud gemini data-sharing-with-google-settings setting-bindings list
    (--data-sharing-with-google-setting=DATA_SHARING_WITH_GOOGLE_SETTING
      : --location=LOCATION) [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--data-sharing-with-google-setting` | DATA_SHARING_WITH_GOOGLE_SETTING |  | _[This must be specified.]_ ID of the dataSharingWithGoogleSetting or fully qualified identifier for the dataSharingWithGoogleSetting. To set the data-sharing-with-google-setting attribute: + provide the argument --data-sharing-with-google-setting on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The location id of the dataSharingWithGoogleSetting resource. To set the location attribute: + provide the argument --data-sharing-with-google-setting on the command line with a fully specified name; + provide the argument --location on the command line. |


**Examples:**
```bash
To list all settingBindings, run:

    $ gcloud gemini data-sharing-with-google-settings setting-bindings \
      list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/data-sharing-with-google-settings/setting-bindings/list)

---
### `gcloud gemini data-sharing-with-google-settings setting-bindings update`

Update settingBindings

Update a settingBinding

**Synopsis:**
```
gcloud gemini data-sharing-with-google-settings setting-bindings update
    (SETTING_BINDING
      : --data-sharing-with-google-setting=DATA_SHARING_WITH_GOOGLE_SETTING
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

  --data-sharing-with-google-setting=DATA_SHARING_WITH_GOOGLE_SETTING
     The dataSharingWithGoogleSetting id of the settingBinding resource.

     To set the data-sharing-with-google-setting attribute:
     + provide the argument setting_binding on the command line with a
       fully specified name;
     + provide the argument --data-sharing-with-google-setting on the
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

    $ gcloud gemini data-sharing-with-google-settings setting-bindings \
      update
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/data-sharing-with-google-settings/setting-bindings/update)

---
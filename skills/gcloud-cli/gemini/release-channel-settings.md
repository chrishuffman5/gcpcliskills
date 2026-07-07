# gcloud gemini release-channel-settings

manage Release Channel Setting resources

### `gcloud gemini release-channel-settings create`

Create releaseChannelSettings

Create a releaseChannelSetting

**Synopsis:**
```
gcloud gemini release-channel-settings create
    (RELEASE_CHANNEL_SETTING : --location=LOCATION) [--labels=[LABELS,...]]
    [--release-channel=RELEASE_CHANNEL] [--request-id=REQUEST_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ReleaseChannelSetting resource - Identifier. Name of the resource.
Format:projects/{project}/locations/{location}/releaseChannelSettings/{releaseChannelSetting}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument release_channel_setting on the command line with
   a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RELEASE_CHANNEL_SETTING
     ID of the releaseChannelSetting or fully qualified identifier for the
     releaseChannelSetting.

     To set the release_channel_setting attribute:
     + provide the argument release_channel_setting on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the releaseChannelSetting resource.

     To set the location attribute:
     + provide the argument release_channel_setting on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--labels` | [LABELS,...] |  | Labels as key value pairs. KEY Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. VALUE Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Shorthand Example: --labels=string=string JSON Example: --labels='{"string": "string"}' File Example: --labels=path_to_file.(yaml\|json) |
| `--release-channel` | one of: experimental Experimental release channel |  | Release channel to be used. RELEASE_CHANNEL must be one of: experimental Experimental release channel. stable Stable channel. |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes since the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To create the releaseChannelSetting, run:

    $ gcloud gemini release-channel-settings create
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/release-channel-settings/create)

---
### `gcloud gemini release-channel-settings delete`

Delete releaseChannelSettings

Delete a releaseChannelSetting

**Synopsis:**
```
gcloud gemini release-channel-settings delete
    (RELEASE_CHANNEL_SETTING : --location=LOCATION)
    [--request-id=REQUEST_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ReleaseChannelSetting resource - Name of the resource The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument release_channel_setting on the command line with
   a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RELEASE_CHANNEL_SETTING
     ID of the releaseChannelSetting or fully qualified identifier for the
     releaseChannelSetting.

     To set the release_channel_setting attribute:
     + provide the argument release_channel_setting on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the releaseChannelSetting resource.

     To set the location attribute:
     + provide the argument release_channel_setting on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes after the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To delete the releaseChannelSetting, run:

    $ gcloud gemini release-channel-settings delete
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/release-channel-settings/delete)

---
### `gcloud gemini release-channel-settings describe`

Describe releaseChannelSettings

Describe a releaseChannelSetting

**Synopsis:**
```
gcloud gemini release-channel-settings describe
    (RELEASE_CHANNEL_SETTING : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ReleaseChannelSetting resource - Name of the resource. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument release_channel_setting on the command line with
   a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RELEASE_CHANNEL_SETTING
     ID of the releaseChannelSetting or fully qualified identifier for the
     releaseChannelSetting.

     To set the release_channel_setting attribute:
     + provide the argument release_channel_setting on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the releaseChannelSetting resource.

     To set the location attribute:
     + provide the argument release_channel_setting on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe the releaseChannelSetting, run:

    $ gcloud gemini release-channel-settings describe
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/release-channel-settings/describe)

---
### `gcloud gemini release-channel-settings list`

List releaseChannelSettings

**Synopsis:**
```
gcloud gemini release-channel-settings list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all releaseChannelSettings, run:

    $ gcloud gemini release-channel-settings list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/release-channel-settings/list)

---
### `gcloud gemini release-channel-settings update`

Update releaseChannelSettings

Update a releaseChannelSetting

**Synopsis:**
```
gcloud gemini release-channel-settings update
    (RELEASE_CHANNEL_SETTING : --location=LOCATION)
    [--release-channel=RELEASE_CHANNEL] [--request-id=REQUEST_ID]
    [--labels=[LABELS,...]
      | --update-labels=[UPDATE_LABELS,...] --clear-labels
      | --remove-labels=REMOVE_LABELS] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ReleaseChannelSetting resource - Identifier. Name of the resource.
Format:projects/{project}/locations/{location}/releaseChannelSettings/{releaseChannelSetting}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument release_channel_setting on the command line with
   a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RELEASE_CHANNEL_SETTING
     ID of the releaseChannelSetting or fully qualified identifier for the
     releaseChannelSetting.

     To set the release_channel_setting attribute:
     + provide the argument release_channel_setting on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the releaseChannelSetting resource.

     To set the location attribute:
     + provide the argument release_channel_setting on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--release-channel` | one of: experimental Experimental release channel |  | Release channel to be used. RELEASE_CHANNEL must be one of: experimental Experimental release channel. stable Stable channel. |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes since the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To update the releaseChannelSetting, run:

    $ gcloud gemini release-channel-settings update
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/release-channel-settings/update)

---

## `gcloud gemini release-channel-settings setting-bindings` — manage Setting Binding resources
### `gcloud gemini release-channel-settings setting-bindings create`

Create settingBindings

Create a settingBinding

**Synopsis:**
```
gcloud gemini release-channel-settings setting-bindings create
    (SETTING_BINDING : --location=LOCATION
      --release-channel-setting=RELEASE_CHANNEL_SETTING) --target=TARGET
    [--async] [--labels=[LABELS,...]] [--product=PRODUCT]
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

  --release-channel-setting=RELEASE_CHANNEL_SETTING
     The releaseChannelSetting id of the settingBinding resource.

     To set the release-channel-setting attribute:
     + provide the argument setting_binding on the command line with a
       fully specified name;
     + provide the argument --release-channel-setting on the command
       line.
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

    $ gcloud gemini release-channel-settings setting-bindings create
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/release-channel-settings/setting-bindings/create)

---
### `gcloud gemini release-channel-settings setting-bindings delete`

Delete settingBindings

Delete a settingBinding

**Synopsis:**
```
gcloud gemini release-channel-settings setting-bindings delete
    (SETTING_BINDING : --location=LOCATION
      --release-channel-setting=RELEASE_CHANNEL_SETTING) [--async]
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

  --release-channel-setting=RELEASE_CHANNEL_SETTING
     The releaseChannelSetting id of the settingBinding resource.

     To set the release-channel-setting attribute:
     + provide the argument setting_binding on the command line with a
       fully specified name;
     + provide the argument --release-channel-setting on the command
       line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes after the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To delete the settingBinding, run:

    $ gcloud gemini release-channel-settings setting-bindings delete
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/release-channel-settings/setting-bindings/delete)

---
### `gcloud gemini release-channel-settings setting-bindings describe`

Describe settingBindings

Describe a settingBinding

**Synopsis:**
```
gcloud gemini release-channel-settings setting-bindings describe
    (SETTING_BINDING : --location=LOCATION
      --release-channel-setting=RELEASE_CHANNEL_SETTING)
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

  --release-channel-setting=RELEASE_CHANNEL_SETTING
     The releaseChannelSetting id of the settingBinding resource.

     To set the release-channel-setting attribute:
     + provide the argument setting_binding on the command line with a
       fully specified name;
     + provide the argument --release-channel-setting on the command
       line.
```

**Examples:**
```bash
To describe the settingBinding, run:

    $ gcloud gemini release-channel-settings setting-bindings describe
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/release-channel-settings/setting-bindings/describe)

---
### `gcloud gemini release-channel-settings setting-bindings list`

List settingBindings

**Synopsis:**
```
gcloud gemini release-channel-settings setting-bindings list
    (--release-channel-setting=RELEASE_CHANNEL_SETTING
      : --location=LOCATION) [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--release-channel-setting` | RELEASE_CHANNEL_SETTING |  | _[This must be specified.]_ ID of the releaseChannelSetting or fully qualified identifier for the releaseChannelSetting. To set the release-channel-setting attribute: + provide the argument --release-channel-setting on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The location id of the releaseChannelSetting resource. To set the location attribute: + provide the argument --release-channel-setting on the command line with a fully specified name; + provide the argument --location on the command line. |


**Examples:**
```bash
To list all settingBindings, run:

    $ gcloud gemini release-channel-settings setting-bindings list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/release-channel-settings/setting-bindings/list)

---
### `gcloud gemini release-channel-settings setting-bindings update`

Update settingBindings

Update a settingBinding

**Synopsis:**
```
gcloud gemini release-channel-settings setting-bindings update
    (SETTING_BINDING : --location=LOCATION
      --release-channel-setting=RELEASE_CHANNEL_SETTING) [--async]
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

  --release-channel-setting=RELEASE_CHANNEL_SETTING
     The releaseChannelSetting id of the settingBinding resource.

     To set the release-channel-setting attribute:
     + provide the argument setting_binding on the command line with a
       fully specified name;
     + provide the argument --release-channel-setting on the command
       line.
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

    $ gcloud gemini release-channel-settings setting-bindings update
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/release-channel-settings/setting-bindings/update)

---
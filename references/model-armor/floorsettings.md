# gcloud model-armor floorsettings

manage FloorSettings resources

### `gcloud model-armor floorsettings describe`

Describe the FloorSetting resource

Displays the floor setting resource with the given name.

**Synopsis:**
```
gcloud model-armor floorsettings describe [--full-uri=FULL_URI]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--full-uri` | FULL_URI |  | Full uri of the floor setting |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/model-armor/floorsettings/describe)

---
### `gcloud model-armor floorsettings update`

Update the FloorSetting resource

Updates the floor setting resource with the given name.

**Synopsis:**
```
gcloud model-armor floorsettings update --full-uri=FULL_URI
    [--enable-floor-setting-enforcement=ENABLE_FLOOR_SETTING_ENFORCEMENT]
    [--[no-]enable-multi-language-detection]
    [--malicious-uri-filter-settings-enforcement=MALICIOUS_URI_FILTER_SETTINGS_ENFORCEMENT]
    [--add-integrated-services=[INTEGRATED_SERVICE,...]
      | --clear-integrated-services
      | --remove-integrated-services=[INTEGRATED_SERVICE,...]]
    [--add-rai-settings-filters=confidenceLevel=CONFIDENCELEVEL],
      [filterType=FILTERTYPE] | --clear-rai-settings-filters
      | --rai-settings-filters=confidenceLevel=CONFIDENCELEVEL],
      [filterType=FILTERTYPE]
      | --remove-rai-settings-filters=confidenceLevel=CONFIDENCELEVEL],
      [filterType=FILTERTYPE]]
    [--advanced-config-deidentify-template=ADVANCED_CONFIG_DEIDENTIFY_TEMPLATE --advanced-config-inspect-template=ADVANCED_CONFIG_INSPECT_TEMPLATE --basic-config-filter-enforcement=BASIC_CONFIG_FILTER_ENFORCEMENT]
    [--[no-]enable-google-mcp-server-cloud-logging
      --google-mcp-server-enforcement-type=GOOGLE_MCP_SERVER_ENFORCEMENT_TYPE]
    [--[no-]enable-vertex-ai-cloud-logging
      --vertex-ai-enforcement-type=VERTEX_AI_ENFORCEMENT_TYPE]
    [--pi-and-jailbreak-filter-settings-confidence-level=PI_AND_JAILBREAK_FILTER_SETTINGS_CONFIDENCE_LEVEL --pi-and-jailbreak-filter-settings-enforcement=PI_AND_JAILBREAK_FILTER_SETTINGS_ENFORCEMENT]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--full-uri` | FULL_URI |  | Full uri of the floor setting |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--enable-floor-setting-enforcement` | ENABLE_FLOOR_SETTING_ENFORCEMENT |  | Enable or disable the floor setting enforcement. Set the value to "TRUE" to enable the floor setting enforcement, "FALSE" to disable it. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/model-armor/floorsettings/update)

---
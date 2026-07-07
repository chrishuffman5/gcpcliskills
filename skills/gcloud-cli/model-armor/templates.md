# gcloud model-armor templates

manage Template resources

### `gcloud model-armor templates create`

Create Model Armor Template

Creates a new Template in a given project and location.

**Synopsis:**
```
gcloud model-armor templates create (TEMPLATE : --location=LOCATION)
    (--malicious-uri-filter-settings-enforcement=MALICIOUS_URI_FILTER_SETTINGS_ENFORCEMENT --rai-settings-filters=[confidenceLevel=CONFIDENCELEVEL],
      [filterType=FILTERTYPE]
      --basic-config-filter-enforcement=BASIC_CONFIG_FILTER_ENFORCEMENT
      | --advanced-config-deidentify-template=ADVANCED_CONFIG_DEIDENTIFY_TEMPLATE --advanced-config-inspect-template=ADVANCED_CONFIG_INSPECT_TEMPLATE --pi-and-jailbreak-filter-settings-confidence-level=PI_AND_JAILBREAK_FILTER_SETTINGS_CONFIDENCE_LEVEL --pi-and-jailbreak-filter-settings-enforcement=PI_AND_JAILBREAK_FILTER_SETTINGS_ENFORCEMENT)
    [--labels=[LABELS,...]] [--request-id=REQUEST_ID]
    [--template-metadata-custom-llm-response-safety-error-code=TEMPLATE_METADATA_CUSTOM_LLM_RESPONSE_SAFETY_ERROR_CODE --template-metadata-custom-llm-response-safety-error-message=TEMPLATE_METADATA_CUSTOM_LLM_RESPONSE_SAFETY_ERROR_MESSAGE --template-metadata-custom-prompt-safety-error-code=TEMPLATE_METADATA_CUSTOM_PROMPT_SAFETY_ERROR_CODE --template-metadata-custom-prompt-safety-error-message=TEMPLATE_METADATA_CUSTOM_PROMPT_SAFETY_ERROR_MESSAGE --template-metadata-ignore-partial-invocation-failures --template-metadata-log-operations --template-metadata-log-sanitize-operations]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Template resource - Identifier. name of resource The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument template on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TEMPLATE
     ID of the template or fully qualified identifier for the template.

     To set the template attribute:
     + provide the argument template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the template resource.

     To set the location attribute:
     + provide the argument template on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--malicious-uri-filter-settings-enforcement` | MALICIOUS_URI_FILTER_SETTINGS_ENFORCEMENT |  | _[Malicious URI filter settings.]_ Tells whether the Malicious URI filter is enabled or disabled. MALICIOUS_URI_FILTER_SETTINGS_ENFORCEMENT must be one of: disabled Disabled enabled Enabled |
| `--rai-settings-filters` | [confidenceLevel=CONFIDENCELEVEL],[filterType=FILTERTYPE] |  | _[Responsible AI Filter settings.]_ Required, List of Responsible AI filters enabled for template. confidenceLevel Confidence level for this RAI filter. During data sanitization, if data is classified under this filter with a confidence level equal to or greater than the specified level, a positive match is reported. If the confidence level is unspecified (i.e., 0), the system will use a reasonable default level based on the filter_type. filterType Type of responsible AI filter. Shorthand Example: --rai-settings-filters=confidenceLevel=string,filterType=string --rai-settings-filters=confidenceLevel=string,filterType=string JSON Example: --rai-settings-filters='[{"confidenceLevel": "string", "filterType": "string"}]' File Example: --rai-settings-filters=path_to_file.(yaml\|json) |
| `--pi-and-jailbreak-filter-settings-confidence-level` | one of: high Low chance of false positives |  | _[Prompt injection and Jailbreak Filter settings.]_ Confidence level for this filter. Confidence level is used to determine the threshold for the filter. If detection confidence is equal to or greater than the specified level, a positive match is reported. Confidence level will only be used if the filter is enabled. PI_AND_JAILBREAK_FILTER_SETTINGS_CONFIDENCE_LEVEL must be one of: high Low chance of false positives. low-and-above Highest chance of a false positive. medium-and-above Some chance of false positives. |
| `--pi-and-jailbreak-filter-settings-enforcement` | PI_AND_JAILBREAK_FILTER_SETTINGS_ENFORCEMENT |  | _[Prompt injection and Jailbreak Filter settings.]_ Tells whether Prompt injection and Jailbreak filter is enabled or disabled. PI_AND_JAILBREAK_FILTER_SETTINGS_ENFORCEMENT must be one of: disabled Enabled enabled Enabled |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--labels` | [LABELS,...] |  | Labels as key value pairs. KEY Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. VALUE Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Shorthand Example: --labels=string=string JSON Example: --labels='{"string": "string"}' File Example: --labels=path_to_file.(yaml\|json) |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server stores the request ID for 60 minutes after the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To create a Template, run:        $ gcloud model-armor templates create my-template \
        --location=us-central1 \
        --malicious-uri-filter-settings-enforcement=enabled
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/model-armor/templates/create)

---
### `gcloud model-armor templates delete`

Delete Model Armor Template

Deletes a Template.

**Synopsis:**
```
gcloud model-armor templates delete (TEMPLATE : --location=LOCATION)
    [--request-id=REQUEST_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Template resource - Name of the resource The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument template on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TEMPLATE
     ID of the template or fully qualified identifier for the template.

     To set the template attribute:
     + provide the argument template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the template resource.

     To set the location attribute:
     + provide the argument template on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server stores the request ID for 60 minutes after the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To delete a Template, run:        $ gcloud model-armor templates delete my-template \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/model-armor/templates/delete)

---
### `gcloud model-armor templates describe`

Get Model Armor Template

Gets a Template.

**Synopsis:**
```
gcloud model-armor templates describe (TEMPLATE : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Template resource - Name of the resource The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument template on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TEMPLATE
     ID of the template or fully qualified identifier for the template.

     To set the template attribute:
     + provide the argument template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the template resource.

     To set the location attribute:
     + provide the argument template on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To get a Template, run:        $ gcloud model-armor templates describe my-template \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/model-armor/templates/describe)

---
### `gcloud model-armor templates list`

List Model Armor Templates

Lists Templates in a given project and location.

**Synopsis:**
```
gcloud model-armor templates list --location=LOCATION [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list Templates in a given project and location, run:        $ gcloud model-armor templates list list --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/model-armor/templates/list)

---
### `gcloud model-armor templates sanitize-model-response`

Sanitize Model Response

Sanitizes a model response.

**Synopsis:**
```
gcloud model-armor templates sanitize-model-response
    (TEMPLATE : --location=LOCATION) [--user-prompt=USER_PROMPT]
    [--model-response-data-text=MODEL_RESPONSE_DATA_TEXT
      | --model-response-data-byte-item-from-file=PATH_TO_FILE
      --model-response-data-byte-item-type=MODEL_RESPONSE_DATA_BYTE_ITEM_TYPE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Template resource - Represents resource name of template e.g.
name=projects/sample-project/locations/us-central1/templates/templ01 The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument template on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TEMPLATE
     ID of the template or fully qualified identifier for the template.

     To set the template attribute:
     + provide the argument template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the template resource.

     To set the location attribute:
     + provide the argument template on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--user-prompt` | USER_PROMPT |  | User Prompt associated with Model response. |


**Examples:**
```bash
To sanitize a model response, run:        $ gcloud model-armor templates sanitize-model-response my-template \
        --location=us-central1 \
        --model-response-data="test-model-response"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/model-armor/templates/sanitize-model-response)

---
### `gcloud model-armor templates sanitize-user-prompt`

Sanitize User Prompt

Sanitizes a user prompt.

**Synopsis:**
```
gcloud model-armor templates sanitize-user-prompt
    (TEMPLATE : --location=LOCATION)
    [--user-prompt-data-text=USER_PROMPT_DATA_TEXT
      | --byte-item-data-from-file=PATH_TO_FILE
      --byte-item-data-type=BYTE_ITEM_DATA_TYPE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Template resource - Represents resource name of template e.g.
name=projects/sample-project/locations/us-central1/templates/templ01 The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument template on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TEMPLATE
     ID of the template or fully qualified identifier for the template.

     To set the template attribute:
     + provide the argument template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the template resource.

     To set the location attribute:
     + provide the argument template on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--user-prompt-data-text` | USER_PROMPT_DATA_TEXT |  | _[At most one of these can be specified:]_ Plaintext string data for sanitization. |


**Examples:**
```bash
To sanitize a user prompt, run:        $ gcloud model-armor templates sanitize-user-prompt my-template \
        --location=us-central1 --user-prompt-data="test-user-prompt"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/model-armor/templates/sanitize-user-prompt)

---
### `gcloud model-armor templates update`

Update Model Armor Template

Updates a Template.

**Synopsis:**
```
gcloud model-armor templates update (TEMPLATE : --location=LOCATION)
    [--request-id=REQUEST_ID]
    [--clear-filter-config
      --malicious-uri-filter-settings-enforcement=MALICIOUS_URI_FILTER_SETTINGS_ENFORCEMENT --basic-config-filter-enforcement=BASIC_CONFIG_FILTER_ENFORCEMENT | --advanced-config-deidentify-template=ADVANCED_CONFIG_DEIDENTIFY_TEMPLATE --advanced-config-inspect-template=ADVANCED_CONFIG_INSPECT_TEMPLATE --pi-and-jailbreak-filter-settings-confidence-level=PI_AND_JAILBREAK_FILTER_SETTINGS_CONFIDENCE_LEVEL --pi-and-jailbreak-filter-settings-enforcement=PI_AND_JAILBREAK_FILTER_SETTINGS_ENFORCEMENT --rai-settings-filters=[confidenceLevel=CONFIDENCELEVEL],
      [filterType=FILTERTYPE]
      | --add-rai-settings-filters=[confidenceLevel=CONFIDENCELEVEL],
      [filterType=FILTERTYPE] --clear-rai-settings-filters
      | --remove-rai-settings-filters=[confidenceLevel=CONFIDENCELEVEL],
      [filterType=FILTERTYPE]]
    [--clear-template-metadata
      --template-metadata-custom-llm-response-safety-error-code=TEMPLATE_METADATA_CUSTOM_LLM_RESPONSE_SAFETY_ERROR_CODE --template-metadata-custom-llm-response-safety-error-message=TEMPLATE_METADATA_CUSTOM_LLM_RESPONSE_SAFETY_ERROR_MESSAGE --template-metadata-custom-prompt-safety-error-code=TEMPLATE_METADATA_CUSTOM_PROMPT_SAFETY_ERROR_CODE --template-metadata-custom-prompt-safety-error-message=TEMPLATE_METADATA_CUSTOM_PROMPT_SAFETY_ERROR_MESSAGE --[no-]template-metadata-ignore-partial-invocation-failures --[no-]template-metadata-log-operations --[no-]template-metadata-log-sanitize-operations]
    [--labels=[LABELS,...]
      | --update-labels=[UPDATE_LABELS,...] --clear-labels
      | --remove-labels=REMOVE_LABELS] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Template resource - Identifier. name of resource The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument template on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TEMPLATE
     ID of the template or fully qualified identifier for the template.

     To set the template attribute:
     + provide the argument template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the template resource.

     To set the location attribute:
     + provide the argument template on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server stores the request ID for 60 minutes after the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To update a Template, run:        $ gcloud model-armor templates update my-template \
        --location=us-central1 --clear-labels
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/model-armor/templates/update)

---
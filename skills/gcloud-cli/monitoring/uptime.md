# gcloud monitoring uptime

manage Cloud Monitoring uptime checks and synthetic monitors

### `gcloud monitoring uptime create`

Create a new uptime check or synthetic monitor

Create a new uptime check or synthetic monitor.

Flags only apply to uptime checks unless noted that they apply to synthetic
monitors.

For information about the JSON/YAML format of an uptime check:
https://cloud.google.com/monitoring/api/ref_v3/rest/v3/projects.uptimeCheckConfigs

**Synopsis:**
```
gcloud monitoring uptime create DISPLAY_NAME
    (--synthetic-target=SYNTHETIC_TARGET
      | [--group-id=GROUP_ID : --group-type=GROUP_TYPE]
      | [--resource-labels=[KEY=VALUE,...]
      : --resource-type=RESOURCE_TYPE])
    [--body=BODY --content-type=CONTENT_TYPE
      --custom-content-type=CUSTOM_CONTENT_TYPE --headers=[KEY=VALUE,...]
      --mask-headers=MASK_HEADERS --password=PASSWORD --path=PATH
      --pings-count=PINGS_COUNT --port=PORT --protocol=PROTOCOL
      --request-method=REQUEST_METHOD
      --service-agent-auth=SERVICE_AGENT_AUTH --username=USERNAME
      --validate-ssl=VALIDATE_SSL --status-classes=[status-class,...]
      | --status-codes=[status-code,...]]
    [--matcher-content=MATCHER_CONTENT
      : --matcher-type=MATCHER_TYPE [--json-path=JSON_PATH
      : --json-path-matcher-type=JSON_PATH_MATCHER_TYPE]]
    [--period=PERIOD --regions=[field,...]
      --timeout=TIMEOUT --user-labels=[KEY=VALUE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DISPLAY_NAME
   Display name for the uptime check or synthetic monitor.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--synthetic-target` | SYNTHETIC_TARGET |  | _[Exactly one of these must be specified:]_ The target of the Synthetic Monitor. This is the fully qualified GCFv2 resource name. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--body` | BODY |  | _[Uptime check protocol settings.]_ The request body associated with the HTTP POST request. Can only be set if --protocol is http or https. |
| `--content-type` | CONTENT_TYPE |  | _[Uptime check protocol settings.]_ The content type header to use for the check, defaults to unspecified. Can only be set if --protocol is http or https. CONTENT_TYPE must be one of: unspecified Not specified url-encoded URL encoded user-provided User provided |
| `--custom-content-type` | CUSTOM_CONTENT_TYPE |  | _[Uptime check protocol settings.]_ A user-provided content type header to use for the check. Can only be set if --protocol is http or https. |
| `--headers` | [KEY=VALUE,...] |  | _[Uptime check protocol settings.]_ The list of headers to send as part of the uptime check request. Can only be set if --protocol is http or https. |
| `--mask-headers` | MASK_HEADERS |  | _[Uptime check protocol settings.]_ Whether to encrypt the header information, defaults to false. Can only be set if --protocol is http or https. |
| `--password` | PASSWORD |  | _[Uptime check protocol settings.]_ The password to use when authenticating with the HTTP server. Can only be set if --protocol is http or https. |
| `--path` | PATH |  | _[Uptime check protocol settings.]_ The path to the page against which to run the check, defaults to /. Can only be set if --protocol is http or https. |
| `--pings-count` | PINGS_COUNT |  | _[Uptime check protocol settings.]_ Number of ICMP pings to send alongside the request. |
| `--port` | PORT |  | _[Uptime check protocol settings.]_ The port on the server against which to run the check. Defaults to 80 when --protocol is http. Defaults to 443 when --protocol is https. Required if --protocol is tcp. |
| `--protocol` | one of: http An HTTP check |  | _[Uptime check protocol settings.]_ The protocol of the request, defaults to http. PROTOCOL must be one of: http An HTTP check. https An HTTPS check. tcp A TCP check. |
| `--request-method` | REQUEST_METHOD |  | _[Uptime check protocol settings.]_ The HTTP request method to use, defaults to get. Can only be set if --protocol is http or https. REQUEST_METHOD must be one of: get HTTP GET method post HTTP POST method |
| `--username` | USERNAME |  | _[OIDC Token authentication]_ The username to use when authenticating with the HTTP server. Can only be set if --protocol is http or https. |
| `--validate-ssl` | VALIDATE_SSL |  | _[OIDC Token authentication]_ Whether to include SSL certificate validation as a part of the uptime check, defaults to false. Can only be set if --protocol is http or https. |
| `--matcher-content` | MATCHER_CONTENT |  | _[Uptime check matcher settings.]_ String, regex or JSON content to match. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--matcher-type` | MATCHER_TYPE |  | _[Uptime check matcher settings.]_ The type of content matcher that is applied to the server output, defaults to contains-string. MATCHER_TYPE must be one of: contains-string Response contains string matches-json-path Response matches at JSONPath matches-regex Response matches regex not-contains-string Response does not contain string not-matches-json-path Response does not match at JSONPath not-matches-regex Response does not match regex |
| `--period` | PERIOD |  | _[Settings.]_ The time between uptime check or synthetic monitor executions in minutes, defaults to 1. Can be set for synthetic monitors. PERIOD must be one of: 1 One minute 10 Ten minutes 15 Fifteen minutes 5 Five minutes |
| `--regions` | [field,...] |  | _[Settings.]_ The list of regions from which the check is run. At least 3 regions must be selected. Defaults to all available regions. field must be one of: asia-pacific asia-southeast1 europe europe-west1 south-america southamerica-east1 usa-iowa us-central1 usa-oregon us-west1 usa-virginia us-east4 |
| `--timeout` | TIMEOUT |  | _[Settings.]_ The maximum amount of time in seconds to wait for the request to complete, defaults to 60. Can be set for synthetic monitors. |
| `--user-labels` | [KEY=VALUE,...] |  | _[Settings.]_ List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To create an uptime check against a URL, run:

    $ gcloud monitoring uptime create DISPLAY_NAME \
        --resource-type=uptime-url \
        --resource-labels=host=google.com,project_id=PROJECT_ID

To create a synthetic monitor, run:

    $ gcloud monitoring uptime create SYNTHETIC_MONITOR_NAME \
        --synthetic-target=projects/PROJECT_ID/locations/REGION/\
    functions/FUNCTION_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/monitoring/uptime/create)

---
### `gcloud monitoring uptime delete`

Delete an uptime check or synthetic monitor

**Synopsis:**
```
gcloud monitoring uptime delete CHECK_ID [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Uptime check or synthetic monitor resource - The uptime check or synthetic
monitor to delete. This represents a Cloud resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument check_id on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CHECK_ID
     ID of the uptime check or synthetic monitor or fully qualified
     identifier for the uptime check or synthetic monitor.

     To set the check_id attribute:
     + provide the argument check_id on the command line.
```

**Examples:**
```bash
To delete an uptime check or synthetic monitor:

    $ gcloud monitoring uptime delete CHECK_ID

More information can be found at
https://cloud.google.com/monitoring/uptime-checks/manage#delete.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/monitoring/uptime/delete)

---
### `gcloud monitoring uptime describe`

Describe an uptime check or synthetic monitor

**Synopsis:**
```
gcloud monitoring uptime describe CHECK_ID [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Uptime check or synthetic monitor resource - The uptime check or synthetic
monitor to describe. This represents a Cloud resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument check_id on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CHECK_ID
     ID of the uptime check or synthetic monitor or fully qualified
     identifier for the uptime check or synthetic monitor.

     To set the check_id attribute:
     + provide the argument check_id on the command line.
```

**Examples:**
```bash
To describe an uptime check or synthetic monitor:

    $ gcloud monitoring uptime describe CHECK_ID

More information can be found at
https://cloud.google.com/monitoring/uptime-checks/manage#get.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/monitoring/uptime/describe)

---
### `gcloud monitoring uptime list-configs`

List uptime checks and synthetic monitors

List uptime checks and synthetic monitors.

**Synopsis:**
```
gcloud monitoring uptime list-configs [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To see all uptime checks and synthetic monitors:

    $ gcloud monitoring uptime list-configs

More information can be found at
https://cloud.google.com/monitoring/uptime-checks/using-uptime-checks
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/monitoring/uptime/list-configs)

---
### `gcloud monitoring uptime list-ips`

List uptime check server ips

List uptime check egress ips.

**Synopsis:**
```
gcloud monitoring uptime list-ips [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To see all uptime check servers ips:

    $ gcloud monitoring uptime list-ips

More information can be found at
https://cloud.google.com/monitoring/uptime-checks/using-uptime-checks
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/monitoring/uptime/list-ips)

---
### `gcloud monitoring uptime update`

Update an existing uptime check or synthetic monitor

Updates an existing uptime check or synthetic monitor.

Flags only apply to uptime checks unless noted that they apply to synthetic
monitors.

For information about the JSON/YAML format of an uptime check:
https://cloud.google.com/monitoring/api/ref_v3/rest/v3/projects.uptimeCheckConfigs

**Synopsis:**
```
gcloud monitoring uptime update CHECK_ID
    [--body=BODY --content-type=CONTENT_TYPE
      --custom-content-type=CUSTOM_CONTENT_TYPE --mask-headers=MASK_HEADERS
      --password=PASSWORD --path=PATH --pings-count=PINGS_COUNT --port=PORT
      --request-method=REQUEST_METHOD
      --service-agent-auth=SERVICE_AGENT_AUTH --username=USERNAME
      --validate-ssl=VALIDATE_SSL --add-status-classes=[status-class,...]
      | --clear-status-classes=CLEAR_STATUS_CLASSES
      | --remove-status-classes=[status-class,...]
      | --set-status-classes=[status-class,...]
      | --add-status-codes=[status-code,...]
      | --clear-status-codes=CLEAR_STATUS_CODES
      | --remove-status-codes=[status-code,...]
      | --set-status-codes=[status-code,...]
      --update-headers=[KEY=VALUE,...] --clear-headers=CLEAR_HEADERS
      | --remove-headers=[KEY,...]]
    [--display-name=DISPLAY_NAME
      --period=PERIOD --timeout=TIMEOUT --add-regions=[region,...]
      | --clear-regions=CLEAR_REGIONS | --remove-regions=[region,...]
      | --set-regions=[region,...]
      --update-user-labels=[KEY=VALUE,...] --clear-user-labels
      | --remove-user-labels=[KEY,...]]
    [--matcher-content=MATCHER_CONTENT
      : --matcher-type=MATCHER_TYPE [--json-path=JSON_PATH
      : --json-path-matcher-type=JSON_PATH_MATCHER_TYPE]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Uptime check or synthetic monitor resource - Name of the uptime check or
synthetic monitor to be updated. This represents a Cloud resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument check_id on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CHECK_ID
     ID of the uptime check or synthetic monitor or fully qualified
     identifier for the uptime check or synthetic monitor.

     To set the check_id attribute:
     + provide the argument check_id on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--body` | BODY |  | _[Uptime check protocol settings.]_ The request body associated with the HTTP POST request. Can only be set if --protocol is http or https. |
| `--content-type` | CONTENT_TYPE |  | _[Uptime check protocol settings.]_ The content type header to use for the check, defaults to unspecified. Can only be set if --protocol is http or https. CONTENT_TYPE must be one of: unspecified Not specified url-encoded URL encoded user-provided User provided |
| `--custom-content-type` | CUSTOM_CONTENT_TYPE |  | _[Uptime check protocol settings.]_ A user-provided content type header to use for the check. Can only be set if --protocol is http or https. |
| `--mask-headers` | MASK_HEADERS |  | _[Uptime check protocol settings.]_ Whether to encrypt the header information, defaults to false. Can only be set if --protocol is http or https. |
| `--password` | PASSWORD |  | _[Uptime check protocol settings.]_ The password to use when authenticating with the HTTP server. Can only be set if --protocol is http or https. |
| `--path` | PATH |  | _[Uptime check protocol settings.]_ The path to the page against which to run the check, defaults to /. Can only be set if --protocol is http or https. |
| `--pings-count` | PINGS_COUNT |  | _[Uptime check protocol settings.]_ Number of ICMP pings to send alongside the request. |
| `--port` | PORT |  | _[Uptime check protocol settings.]_ The port on the server against which to run the check. Defaults to 80 when --protocol is http. Defaults to 443 when --protocol is https. Required if --protocol is tcp. |
| `--request-method` | REQUEST_METHOD |  | _[Uptime check protocol settings.]_ The HTTP request method to use, defaults to get. Can only be set if --protocol is http or https. REQUEST_METHOD must be one of: get HTTP GET method post HTTP POST method |
| `--username` | USERNAME |  | _[OIDC Token authentication]_ The username to use when authenticating with the HTTP server. Can only be set if --protocol is http or https. |
| `--validate-ssl` | VALIDATE_SSL |  | _[OIDC Token authentication]_ Whether to include SSL certificate validation as a part of the uptime check, defaults to false. Can only be set if --protocol is http or https. |
| `--display-name` | DISPLAY_NAME |  | _[Settings.]_ The display name for the uptime check or synthetic monitor. |
| `--period` | PERIOD |  | _[Settings.]_ The time between uptime check or synthetic monitor executions in minutes, defaults to 1. Can be set for synthetic monitors. PERIOD must be one of: 1 One minute 10 Ten minutes 15 Fifteen minutes 5 Five minutes |
| `--timeout` | TIMEOUT |  | _[Settings.]_ The maximum amount of time in seconds to wait for the request to complete, defaults to 60. Can be set for synthetic monitors. |
| `--matcher-content` | MATCHER_CONTENT |  | _[Uptime check matcher settings.]_ String, regex or JSON content to match. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--matcher-type` | MATCHER_TYPE |  | _[Uptime check matcher settings.]_ The type of content matcher that is applied to the server output, defaults to contains-string. MATCHER_TYPE must be one of: contains-string Response contains string matches-json-path Response matches at JSONPath matches-regex Response matches regex not-contains-string Response does not contain string not-matches-json-path Response does not match at JSONPath not-matches-regex Response does not match regex |


**Examples:**
```bash
To update an uptime check or synthetic monitor, run:

    $ gcloud monitoring uptime update CHECK_ID --period=5 --timeout=30
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/monitoring/uptime/update)

---
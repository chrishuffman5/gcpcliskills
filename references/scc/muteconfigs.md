# gcloud scc muteconfigs

manage Cloud SCC (Security Command Center) mute configs

### `gcloud scc muteconfigs create`

Create a Security Command Center mute config

Create a Security Command Center mute config.

**Synopsis:**
```
gcloud scc muteconfigs create MUTE_CONFIG [--description=DESCRIPTION]
    [--expiry-time=EXPIRY_TIME] [--filter=FILTER]
    [--location=LOCATION; default="global"] [--type=TYPE; default="static"]
    [--folder=FOLDER | --organization=ORGANIZATION | --project=PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
MUTE_CONFIG
   ID of the mute config or the full resource name of the mute config.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | The text that will be used to describe a mute configuration. |
| `--expiry-time` | EXPIRY_TIME |  | The expiry of the mute config. Only applicable for dynamic configs. If the expiry is set, when the config expires, it is removed from all findings. See $ gcloud topic datetimes for information on supported time formats. |
| `--filter` | FILTER |  | The filter string which will applied to findings muted by a mute configuration. |
| `--location` | LOCATION | global | When data residency controls are enabled, this attribute specifies the location in which the resource is located and applicable. The location attribute can be provided as part of the fully specified resource name or with the --location argument on the command line. The default location is global. NOTE: If you override the endpoint to a regional endpoint (https://cloud.google.com/security-command-center/docs/reference/rest/index.html?rep_location=global#regional-service-endpoint) you must specify the correct data location (https://cloud.google.com/security-command-center/docs/data-residency-support#locations) using this flag. The default location on this command is unrelated to the default location that is specified when data residency controls are enabled for Security Command Center. NOTE: If no location is specified, the default location is global AND the request will be routed to the SCC V1 API. To use the SCC V2 API - please explicitly specify the flag. |
| `--type` | one of: static, dynamic | static | The mute configuration type. Immutable after creation. TYPE must be one of: static, dynamic. |


**Examples:**
```bash
To create a mute config test-mute-config given organization 123 with a
filter on category that equals to XSS_SCRIPTING, run:

    $ gcloud scc muteconfigs create test-mute-config \
        --organization=123 --description="This is a test mute config" \
        --filter="category=\"XSS_SCRIPTING\""

To create a mute config test-mute-config given folder 456 with a filter on
category that equals to XSS_SCRIPTING, run:

    $ gcloud scc muteconfigs create test-mute-config --folder=456 \
        --description="This is a test mute config" \
        --filter="category=\"XSS_SCRIPTING\""

To create a mute config test-mute-config given project 789 with a filter on
category that equals to XSS_SCRIPTING, run:

    $ gcloud scc muteconfigs create test-mute-config --project=789 \
        --description="This is a test mute config" \
        --filter="category=\"XSS_SCRIPTING\""

To create a mute config test-mute-config given organization 123,
location=eu with a filter on category that equals to XSS_SCRIPTING, run:

    $ gcloud scc muteconfigs create test-mute-config \
        --organization=123 --description="This is a test mute config" \
        --filter="category=\"XSS_SCRIPTING\"" --location=eu
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/muteconfigs/create)

---
### `gcloud scc muteconfigs delete`

Delete a Security Command Center mute config

Delete a Security Command Center mute config.

**Synopsis:**
```
gcloud scc muteconfigs delete MUTE_CONFIG
    [--location=LOCATION; default="global"]
    [--folder=FOLDER | --organization=ORGANIZATION | --project=PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
MUTE_CONFIG
   ID of the mute config or the full resource name of the mute config.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION | global | When data residency controls are enabled, this attribute specifies the location in which the resource is located and applicable. The location attribute can be provided as part of the fully specified resource name or with the --location argument on the command line. The default location is global. NOTE: If you override the endpoint to a regional endpoint (https://cloud.google.com/security-command-center/docs/reference/rest/index.html?rep_location=global#regional-service-endpoint) you must specify the correct data location (https://cloud.google.com/security-command-center/docs/data-residency-support#locations) using this flag. The default location on this command is unrelated to the default location that is specified when data residency controls are enabled for Security Command Center. NOTE: If no location is specified, the default location is global AND the request will be routed to the SCC V1 API. To use the SCC V2 API - please explicitly specify the flag. |


**Examples:**
```bash
To delete a mute config given organization 123 with id test-mute-config,
run:

    $ gcloud scc muteconfigs delete test-mute-config --organization=123

To delete a mute config given folder 456 with id test-mute-config, run:

    $ gcloud scc muteconfigs delete test-mute-config --folder=456

To delete a mute config given project 789 with id test-mute-config, run:

    $ gcloud scc muteconfigs delete test-mute-config --project=789

To delete a mute config given organization 123 with id test-mute-config and
location=eu, run:

    $ gcloud scc muteconfigs delete test-mute-config \
        --organization=123 --location=eu
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/muteconfigs/delete)

---
### `gcloud scc muteconfigs get`

Get a Security Command Center mute config

Get a Security Command Center mute config.

**Synopsis:**
```
gcloud scc muteconfigs get MUTE_CONFIG
    [--location=LOCATION; default="global"]
    [--folder=FOLDER | --organization=ORGANIZATION | --project=PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
MUTE_CONFIG
   ID of the mute config or the full resource name of the mute config.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION | global | When data residency controls are enabled, this attribute specifies the location in which the resource is located and applicable. The location attribute can be provided as part of the fully specified resource name or with the --location argument on the command line. The default location is global. NOTE: If you override the endpoint to a regional endpoint (https://cloud.google.com/security-command-center/docs/reference/rest/index.html?rep_location=global#regional-service-endpoint) you must specify the correct data location (https://cloud.google.com/security-command-center/docs/data-residency-support#locations) using this flag. The default location on this command is unrelated to the default location that is specified when data residency controls are enabled for Security Command Center. NOTE: If no location is specified, the default location is global AND the request will be routed to the SCC V1 API. To use the SCC V2 API - please explicitly specify the flag. |


**Examples:**
```bash
To get a mute config given organization 123 with id test-mute-config, run:

    $ gcloud scc muteconfigs get test-mute-config --organization=123

To get a mute config given folder 456 with id test-mute-config, run:

    $ gcloud scc muteconfigs get test-mute-config --folder=456

To get a mute config given project 789 with id test-mute-config, run:

    $ gcloud scc muteconfigs get test-mute-config --project=789

To get a mute config given organization 123 with id test-mute-config and
location=eu, run:

    $ gcloud scc muteconfigs get test-mute-config --organization=123 \
        --location=eu
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/muteconfigs/get)

---
### `gcloud scc muteconfigs list`

ListSecurity Command Center mute configs

List Security Command Center mute configs.

**Synopsis:**
```
gcloud scc muteconfigs list
    (--folder=FOLDER | --organization=ORGANIZATION | --project=PROJECT)
    [--location=LOCATION; default="global"] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER |  | _[Exactly one of these must be specified:]_ Folder where the mute config resides. Formatted as folders/456 or just 456. |
| `--organization` | ORGANIZATION |  | _[Exactly one of these must be specified:]_ Organization where the mute config resides. Formatted as organizations/123 or just 123. |
| `--project` | PROJECT |  | _[Exactly one of these must be specified:]_ Project (id or number) where the mute config resides. Formatted as projects/789 or just 789. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION | global | When data residency controls are enabled, this attribute specifies the location in which the resource is located and applicable. The location attribute can be provided as part of the fully specified resource name or with the --location argument on the command line. The default location is global. NOTE: If you override the endpoint to a regional endpoint (https://cloud.google.com/security-command-center/docs/reference/rest/index.html?rep_location=global#regional-service-endpoint) you must specify the correct data location (https://cloud.google.com/security-command-center/docs/data-residency-support#locations) using this flag. The default location on this command is unrelated to the default location that is specified when data residency controls are enabled for Security Command Center. NOTE: If no location is specified, the default location is global AND the request will be routed to the SCC V1 API. To use the SCC V2 API - please explicitly specify the flag. |


**Examples:**
```bash
List mute configs under organization 123:

    $ gcloud scc muteconfigs list --organization=123

List mute configs under folder 456:

    $ gcloud scc muteconfigs list --folder=456

List mute configs under project 789:

    $ gcloud scc muteconfigs list --project=789

    List mute configs under organization `_123_` and `location=eu`:

    $ gcloud scc muteconfigs list --organization=123 --location=eu
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/muteconfigs/list)

---
### `gcloud scc muteconfigs update`

Update a Security Command Center mute config

Update a Security Command Center mute config.

**Synopsis:**
```
gcloud scc muteconfigs update MUTE_CONFIG [--description=DESCRIPTION]
    [--expiry-time=EXPIRY_TIME] [--filter=FILTER]
    [--location=LOCATION; default="global"] [--update-mask=UPDATE_MASK]
    [--folder=FOLDER | --organization=ORGANIZATION | --project=PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
MUTE_CONFIG
   ID of the mute config or the full resource name of the mute config.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | The text that will be used to describe a mute configuration. |
| `--expiry-time` | EXPIRY_TIME |  | The expiry of the mute config. Only applicable for dynamic configs. If the expiry is set, when the config expires, it is removed from all findings. See $ gcloud topic datetimes for information on supported time formats. |
| `--filter` | FILTER |  | The filter string which will applied to findings muted by a mute configuration. |
| `--location` | LOCATION | global | When data residency controls are enabled, this attribute specifies the location in which the resource is located and applicable. The location attribute can be provided as part of the fully specified resource name or with the --location argument on the command line. The default location is global. NOTE: If you override the endpoint to a regional endpoint (https://cloud.google.com/security-command-center/docs/reference/rest/index.html?rep_location=global#regional-service-endpoint) you must specify the correct data location (https://cloud.google.com/security-command-center/docs/data-residency-support#locations) using this flag. The default location on this command is unrelated to the default location that is specified when data residency controls are enabled for Security Command Center. NOTE: If no location is specified, the default location is global AND the request will be routed to the SCC V1 API. To use the SCC V2 API - please explicitly specify the flag. |
| `--update-mask` | UPDATE_MASK |  | Optional: If left unspecified (default), an update-mask is automatically created using the flags specified in the command and only those values are updated. |


**Examples:**
```bash
Update a mute config with ID=test-mute-config under organization=123 with a
filter on category that equals to XSS_SCRIPTING:

    $ gcloud scc muteconfigs update test-mute-config \
        --organization=123 --description="This is a test mute config" \
        --filter="category=\"XSS_SCRIPTING\""

Update a mute config with ID=test-mute-config under folder=456 with a
filter on category that equals to XSS_SCRIPTING:

    $ gcloud scc muteconfigs update test-mute-config --folder=456 \
        --description="This is a test mute config" \
        --filter="category=\"XSS_SCRIPTING\""

Update a mute config with ID=test-mute-config under project=789 with a
filter on category that equals to XSS_SCRIPTING:

    $ gcloud scc muteconfigs update test-mute-config --project=789 \
        --description="This is a test mute config" \
        --filter="category=\"XSS_SCRIPTING\""

Update a mute config with ID=test-mute-config under organization=123
location=eu with a filter on category that equals to XSS_SCRIPTING:

    $ gcloud scc muteconfigs update test-mute-config \
        --organization=123 --description="This is a test mute config" \
        --filter="category=\"XSS_SCRIPTING\"" --location=eu
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/muteconfigs/update)

---
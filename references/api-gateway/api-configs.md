# gcloud api-gateway api-configs

manage Cloud API Gateway API Configs

### `gcloud api-gateway api-configs create`

Add a new config to an API

Add a new config to an API.

NOTE: If the specified API does not exist it will be created.

**Synopsis:**
```
gcloud api-gateway api-configs create (API_CONFIG : --api=API)
    (--grpc-files=[FILE,...] | --openapi-spec=[FILE,...]) [--async]
    [--backend-auth-service-account=BACKEND_AUTH_SERVICE_ACCOUNT]
    [--display-name=DISPLAY_NAME] [--labels=[KEY=VALUE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Api config resource - Name for API Config which will be created. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument api_config on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument api_config on the command line with a fully
   specified name;
 * Location for API and API Configs. Defaults to global.

This must be specified.

  API_CONFIG
     ID of the api-config or fully qualified identifier for the
     api-config.

     To set the api-config attribute:
     + provide the argument api_config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --api=API
     API ID.

     To set the api attribute:
     + provide the argument api_config on the command line with a fully
       specified name;
     + provide the argument --api on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--grpc-files` | [FILE,...] |  | _[Exactly one of these must be specified:]_ Files describing the GRPC service. Google Service Configuration files in JSON or YAML formats as well as Proto descriptors should be listed. |
| `--openapi-spec` | [FILE,...] |  | _[Exactly one of these must be specified:]_ The OpenAPI specifications containing service configuration information, and API specification for the gateway. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--backend-auth-service-account` | BACKEND_AUTH_SERVICE_ACCOUNT |  | Service account which will be used to sign tokens for backends with authentication configured. |
| `--display-name` | DISPLAY_NAME |  | Human readable name which can optionally be supplied. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To create an API config for the API 'my-api' with an OpenAPI spec, run:

    $ gcloud api-gateway api-configs create my-config --api=my-api \
        --openapi-spec=path/to/openapi_spec.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/api-gateway/api-configs/create)

---
### `gcloud api-gateway api-configs delete`

Deletes a config from an API

Deletes a config from an API.

**Synopsis:**
```
gcloud api-gateway api-configs delete (API_CONFIG : --api=API) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Api config resource - Name for API Config which will be deleted. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument api_config on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument api_config on the command line with a fully
   specified name;
 * Location for API and API Configs. Defaults to global.

This must be specified.

  API_CONFIG
     ID of the api-config or fully qualified identifier for the
     api-config.

     To set the api-config attribute:
     + provide the argument api_config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --api=API
     API ID.

     To set the api attribute:
     + provide the argument api_config on the command line with a fully
       specified name;
     + provide the argument --api on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete an API Config 'my-config' in 'my-api', run:

    $ gcloud api-gateway api-configs delete my-config --api=my-api
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/api-gateway/api-configs/delete)

---
### `gcloud api-gateway api-configs describe`

Show details about a specific API config

Show details about a specific API config.

**Synopsis:**
```
gcloud api-gateway api-configs describe (API_CONFIG : --api=API)
    [--view=VIEW; default="BASIC"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Api config resource - Name for API Config which will be created. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument api_config on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument api_config on the command line with a fully
   specified name;
 * Location for API and API Configs. Defaults to global.

This must be specified.

  API_CONFIG
     ID of the api-config or fully qualified identifier for the
     api-config.

     To set the api-config attribute:
     + provide the argument api_config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --api=API
     API ID.

     To set the api attribute:
     + provide the argument api_config on the command line with a fully
       specified name;
     + provide the argument --api on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--view` | one of: BASIC, FULL | BASIC | The API Configuration view to return. If 'FULL' is specified, the base64 encoded API Configuration's source file conent will be included in the response. VIEW must be one of: BASIC, FULL. |


**Examples:**
```bash
To show details about an API config, run:

    $ gcloud api-gateway api-configs describe my-config --api=my-api
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/api-gateway/api-configs/describe)

---
### `gcloud api-gateway api-configs list`

List configs for an API

List configs for an API.

**Synopsis:**
```
gcloud api-gateway api-configs list [--api=API] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--api` | API |  | _[* Location for API and API Configs. Defaults to global.]_ ID of the api or fully qualified identifier for the api. To set the api attribute: + provide the argument --api on the command line; + Defaults to wildcard for all APIs. |


**Examples:**
```bash
To list all API configs, run:

    $ gcloud api-gateway api-configs list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/api-gateway/api-configs/list)

---
### `gcloud api-gateway api-configs update`

Update an API Gateway API config

Update an API Gateway API config.

NOTE: Only the name and labels may be updated on an API config.

**Synopsis:**
```
gcloud api-gateway api-configs update (API_CONFIG : --api=API) [--async]
    [--display-name=DISPLAY_NAME] [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Api config resource - Name for API Config which will be updated. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument api_config on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument api_config on the command line with a fully
   specified name;
 * Location for API and API Configs. Defaults to global.

This must be specified.

  API_CONFIG
     ID of the api-config or fully qualified identifier for the
     api-config.

     To set the api-config attribute:
     + provide the argument api_config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --api=API
     API ID.

     To set the api attribute:
     + provide the argument api_config on the command line with a fully
       specified name;
     + provide the argument --api on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--display-name` | DISPLAY_NAME |  | Human readable name which can optionally be supplied. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update the display name of an API config, run:

    $ gcloud api-gateway api-configs update my-config --api=my-api \
        --display-name="New Display Name"

NOTE: Only the display name and labels attributes are mutable on an API
config.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/api-gateway/api-configs/update)

---
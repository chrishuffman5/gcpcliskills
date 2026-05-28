# gcloud developer-connect insights-configs

manage Insights Config resources

### `gcloud developer-connect insights-configs create`

Create an insight config

Create an insights config.

**Synopsis:**
```
gcloud developer-connect insights-configs create
    (INSIGHTS_CONFIG : --location=LOCATION)
    (--app-hub-application=APP_HUB_APPLICATION
      | --target-projects=[TARGET_PROJECTS,...])
    [--artifact-config=ARTIFACT_CONFIG_ITEM] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Insights config resource - The insights config to create. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument insights_config on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSIGHTS_CONFIG
     ID of the insights_config or fully qualified identifier for the
     insights_config.

     To set the insightsConfigs attribute:
     + provide the argument insights_config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The region of the insight config.

     To set the location attribute:
     + provide the argument insights_config on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--app-hub-application` | APP_HUB_APPLICATION |  | _[Exactly one of these must be specified:]_ The App Hub application to which the insight config is associated. |
| `--target-projects` | [TARGET_PROJECTS,...] |  | _[Exactly one of these must be specified:]_ A comma-separated list of target project IDs/numbers to which the insight config is associated. Format examples: --target-projects=123567890,my-project --target-projects=projects/1234567890,projects/my-project |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--artifact-config` | ARTIFACT_CONFIG_ITEM |  | Specifies a single artifact configuration. This flag can be repeated for multiple configurations. Each configuration can be provided in a key-value format. Format examples: --artifact-config=uri={REGION}-docker.pkg.dev/my-project/my-repo/my-image,buildProject=my-project --artifact-config=[uri={REGION}-docker.pkg.dev/my-project/my-repo/my-image,buildProject=my-project] Supported keys within a configuration: * buildProject: String, e.g., my-project * uri: String, e.g., {REGION}-docker.pkg.dev/my-project/my-repo/my-image |


**Examples:**
```bash
To create an insights config with an apphub application, run:

    $ gcloud developer-connect insights-configs create \
        insights-config-name \
        --app-hub-application=projects/my-project/locations/\
    us-central1/applications/my-app-hub-application

To create an insights config with projects, run:

    $ gcloud developer-connect insights-configs create \
        insights-config-name --target-projects=project1,project2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/developer-connect/insights-configs/create)

---
### `gcloud developer-connect insights-configs delete`

Delete insightsConfigs

Delete an insightsConfig

**Synopsis:**
```
gcloud developer-connect insights-configs delete
    (INSIGHTS_CONFIG : --location=LOCATION) [--async] [--etag=ETAG]
    [--request-id=REQUEST_ID] [--validate-only] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
InsightsConfig resource - Value for parent. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument insights_config on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSIGHTS_CONFIG
     ID of the insightsConfig or fully qualified identifier for the
     insightsConfig.

     To set the insights_config attribute:
     + provide the argument insights_config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the insightsConfig resource.

     To set the location attribute:
     + provide the argument insights_config on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--etag` | ETAG |  | This checksum is computed by the server based on the value of other fields, and may be sent on update and delete requests to ensure the client has an up-to-date value before proceeding. |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes after the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |
| `--validate-only` |  |  | If set, validate the request, but do not actually post it. |


**Examples:**
```bash
To delete the insightsConfig, run:

    $ gcloud developer-connect insights-configs delete
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/developer-connect/insights-configs/delete)

---
### `gcloud developer-connect insights-configs describe`

Describe insightsConfigs

Describe an insightsConfig

**Synopsis:**
```
gcloud developer-connect insights-configs describe
    (INSIGHTS_CONFIG : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
InsightsConfig resource - Name of the resource. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument insights_config on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSIGHTS_CONFIG
     ID of the insightsConfig or fully qualified identifier for the
     insightsConfig.

     To set the insights_config attribute:
     + provide the argument insights_config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the insightsConfig resource.

     To set the location attribute:
     + provide the argument insights_config on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe the insightsConfig, run:

    $ gcloud developer-connect insights-configs describe
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/developer-connect/insights-configs/describe)

---
### `gcloud developer-connect insights-configs list`

List insightsConfigs

**Synopsis:**
```
gcloud developer-connect insights-configs list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all insightsConfigs, run:

    $ gcloud developer-connect insights-configs list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/developer-connect/insights-configs/list)

---
### `gcloud developer-connect insights-configs update`

Update the configuration of an insight config

Update the configuration of an insights config.

**Synopsis:**
```
gcloud developer-connect insights-configs update
    (INSIGHTS_CONFIG : --location=LOCATION)
    (--run-discovery
      --artifact-uri=ARTIFACT_URI --build-project=BUILD_PROJECT)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Insights config resource - The insights config to update. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument insights_config on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSIGHTS_CONFIG
     ID of the insights_config or fully qualified identifier for the
     insights_config.

     To set the insightsConfigs attribute:
     + provide the argument insights_config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The region of the insight config.

     To set the location attribute:
     + provide the argument insights_config on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--run-discovery` |  |  | _[At least one of these must be specified:]_ Sets the state of the insight config to PENDING and kicks off the discovery flow. |
| `--artifact-uri` | ARTIFACT_URI |  | _[At least one of these must be specified:]_ Identifier for the specific artifact you want to update This flag argument must be specified if any of the other arguments in this group are specified. |
| `--build-project` | BUILD_PROJECT |  | _[At least one of these must be specified:]_ The project ID of the project to where the artifact is built. This flag argument must be specified if any of the other arguments in this group are specified. |


**Examples:**
```bash
To update the state of an insights config, run:

    $ gcloud developer-connect insights-configs update \
        insights-config-name --run-discovery

To update the Artifact Analysis project for an artifact in an insights
config, run:

    $ gcloud developer-connect insights-configs update \
        insights-config-name \
        --artifact-uri=us-{location}-docker.pkg.dev/my-project/\
    my-artifact-repo/my-image --build-project={build_project}
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/developer-connect/insights-configs/update)

---
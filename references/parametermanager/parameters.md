# gcloud parametermanager parameters

manage Parameter Manager parameter resources

### `gcloud parametermanager parameters create`

Creates a Parameter Manager parameter

Creates a parameter resource with the specified name and properties. If a
parameter of the given name already exists, this command will return an
error.

**Synopsis:**
```
gcloud parametermanager parameters create PARAMETER [--labels=[LABELS,...]]
    [--location=LOCATION] [--parameter-format=PARAMETER_FORMAT]
    [--request-id=REQUEST_ID] [--kms-key=KMS_KEY : --key-ring=KEY_RING]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Parameter resource - Identifier. [Output only] The resource name of the
Parameter in the format projects/*/locations/*/parameters/*. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument parameter on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument parameter on the command line with a fully
   specified name;
 * provide the argument --location on the command line.

This must be specified.

  PARAMETER
     ID of the parameter or fully qualified identifier for the parameter.

     To set the parameter attribute:
     + provide the argument parameter on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--labels` | [LABELS,...] |  | Labels as key value pairs. KEY Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. VALUE Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Shorthand Example: --labels=string=string JSON Example: --labels='{"string": "string"}' File Example: --labels=path_to_file.(yaml\|json) |
| `--location` | LOCATION |  | For resources [parameter, kms-key], provides fallback value for resource location attribute. When the resource's full URI path is not provided, location will fallback to this flag value. |
| `--parameter-format` | one of: json JSON format |  | Specifies the format of a Parameter. PARAMETER_FORMAT must be one of: json JSON format. unformatted Unformatted. yaml YAML format. |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes since the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To create a parameter my-parameter in location global run:

    $ gcloud parametermanager parameters create my-parameter \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/parametermanager/parameters/create)

---
### `gcloud parametermanager parameters delete`

Deletes a single Parameter Manager parameter resource

Deletes a parameter. This action is irreversible.

**Synopsis:**
```
gcloud parametermanager parameters delete (PARAMETER : --location=LOCATION)
    [--request-id=REQUEST_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Parameter resource - Name of the resource in the format
projects/*/locations/*/parameters/*. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument parameter on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PARAMETER
     ID of the parameter or fully qualified identifier for the parameter.

     To set the parameter attribute:
     + provide the argument parameter on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the parameter resource.

     To set the location attribute:
     + provide the argument parameter on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes after the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To delete a parameter my-parameter in location global run:

    $ gcloud parametermanager parameters delete my-parameter \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/parametermanager/parameters/delete)

---
### `gcloud parametermanager parameters describe`

Gets a single Parameter Manager parameter

Gets a single parameter resource.

**Synopsis:**
```
gcloud parametermanager parameters describe
    (PARAMETER : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Parameter resource - Name of the resource in the format
projects/*/locations/*/parameters/*. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument parameter on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PARAMETER
     ID of the parameter or fully qualified identifier for the parameter.

     To set the parameter attribute:
     + provide the argument parameter on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the parameter resource.

     To set the location attribute:
     + provide the argument parameter on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To get a single parameter my-parameter in location global run:

    $ gcloud parametermanager parameters describe my-parameter \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/parametermanager/parameters/describe)

---
### `gcloud parametermanager parameters list`

Lists Parameter Manager parameters

List all parameter names belonging to a location within a project.

**Synopsis:**
```
gcloud parametermanager parameters list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all parameters in location global run:

    $ gcloud parametermanager parameters list --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/parametermanager/parameters/list)

---
### `gcloud parametermanager parameters update`

Updates the metadata of an Parameter Manager parameter resource

Update the metadata of a parameter (e.g. labels). This command will return
an error if you specify a parameter that does not exist.

**Synopsis:**
```
gcloud parametermanager parameters update PARAMETER [--location=LOCATION]
    [--parameter-format=PARAMETER_FORMAT] [--request-id=REQUEST_ID]
    [--key-ring=KEY_RING --clear-kms-key | --kms-key=KMS_KEY]
    [--labels=[LABELS,...]
      | --update-labels=[UPDATE_LABELS,...] --clear-labels
      | --remove-labels=REMOVE_LABELS] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Parameter resource - Identifier. [Output only] The resource name of the
Parameter in the format projects/*/locations/*/parameters/*. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument parameter on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument parameter on the command line with a fully
   specified name;
 * provide the argument --location on the command line.

This must be specified.

  PARAMETER
     ID of the parameter or fully qualified identifier for the parameter.

     To set the parameter attribute:
     + provide the argument parameter on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | For resources [parameter, kms-key], provides fallback value for resource location attribute. When the resource's full URI path is not provided, location will fallback to this flag value. |
| `--parameter-format` | one of: json JSON format |  | Specifies the format of a Parameter. PARAMETER_FORMAT must be one of: json JSON format. unformatted Unformatted. yaml YAML format. |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes since the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To update a parameter my-parameter in location global run:

    $ gcloud parametermanager parameters update my-parameter \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/parametermanager/parameters/update)

---

## `gcloud parametermanager parameters versions` — manage Parameter Manager parameter version resources
### `gcloud parametermanager parameters versions create`

Creates an Parameter Manager parameter version

Creates a new parameter version using the provided parameter data.

**Synopsis:**
```
gcloud parametermanager parameters versions create
    (VERSION : --location=LOCATION --parameter=PARAMETER)
    ((--payload-data=PAYLOAD_DATA | --payload-data-from-file=PATH_TO_FILE))
    [--disabled] [--request-id=REQUEST_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Version resource - Identifier. [Output only] The resource name of the
ParameterVersion in the format
projects/*/locations/*/parameters/*/versions/*. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument version on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  VERSION
     ID of the version or fully qualified identifier for the version.

     To set the version attribute:
     + provide the argument version on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the version resource.

     To set the location attribute:
     + provide the argument version on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --parameter=PARAMETER
     The parameter id of the version resource.

     To set the parameter attribute:
     + provide the argument version on the command line with a fully
       specified name;
     + provide the argument --parameter on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--payload-data` | PAYLOAD_DATA |  | _[Exactly one of these must be specified:]_ bytes data for storing payload. |
| `--payload-data-from-file` | PATH_TO_FILE |  | _[Exactly one of these must be specified:]_ bytes data for storing payload. Use a full or relative path to a local file containing the value of payload_data. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--disabled` |  |  | Disabled boolean to determine if a ParameterVersion acts as a metadata only resource (payload is never returned if disabled is true). If true any calls will always default to BASIC view even if the user explicitly passes FULL view as part of the request. A render call on a disabled resource fails with an error. Default value is False. |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes since the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To create a parameter version my-parameter-version of parameter
my-parameter in location global run:

    $ gcloud parametermanager parameters versions create \
        my-parameter-version --parameter=my-parameter --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/parametermanager/parameters/versions/create)

---
### `gcloud parametermanager parameters versions delete`

Deletes a single Parameter Manager parameter version

Deletes a single parameter version along with its metadata. This action is
irreversible.

**Synopsis:**
```
gcloud parametermanager parameters versions delete
    (VERSION : --location=LOCATION --parameter=PARAMETER)
    [--request-id=REQUEST_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Version resource - Name of the resource in the format
projects/*/locations/*/parameters/*/versions/*. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument version on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  VERSION
     ID of the version or fully qualified identifier for the version.

     To set the version attribute:
     + provide the argument version on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the version resource.

     To set the location attribute:
     + provide the argument version on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --parameter=PARAMETER
     The parameter id of the version resource.

     To set the parameter attribute:
     + provide the argument version on the command line with a fully
       specified name;
     + provide the argument --parameter on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes after the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To delete a parameter version my-parameter-version of parameter
my-parameter in location global run:

    $ gcloud parametermanager parameters versions delete \
        my-parameter-version --parameter=my-parameter --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/parametermanager/parameters/versions/delete)

---
### `gcloud parametermanager parameters versions describe`

Gets a single Parameter Manager parameter version

Gets a single parameter version, along with payload supplied by the user at
the time of creation. If the payload contains any references to secrets,
these will not be rendered in the output.

**Synopsis:**
```
gcloud parametermanager parameters versions describe
    (VERSION : --location=LOCATION --parameter=PARAMETER) [--view=VIEW]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Version resource - Name of the resource in the format
projects/*/locations/*/parameters/*/versions/*. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument version on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  VERSION
     ID of the version or fully qualified identifier for the version.

     To set the version attribute:
     + provide the argument version on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the version resource.

     To set the location attribute:
     + provide the argument version on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --parameter=PARAMETER
     The parameter id of the version resource.

     To set the parameter attribute:
     + provide the argument version on the command line with a fully
       specified name;
     + provide the argument --parameter on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--view` | one of: basic Include only the metadata for the resource |  | View of the ParameterVersion. In the default FULL view, all metadata & payload associated with the ParameterVersion will be returned. VIEW must be one of: basic Include only the metadata for the resource. full Include metadata & other relevant payload data as well. This is the default view. |


**Examples:**
```bash
To get a single parameter version my-parameter-version of parameter
my-parameter in location global run:

    $ gcloud parametermanager parameters versions describe \
        my-parameter-version --parameter=my-parameter --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/parametermanager/parameters/versions/describe)

---
### `gcloud parametermanager parameters versions list`

List Parameter Manager parameter versions

List all parameter versions belonging to a parameter and their status.

**Synopsis:**
```
gcloud parametermanager parameters versions list
    (--parameter=PARAMETER : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--parameter` | PARAMETER |  | _[This must be specified.]_ ID of the parameter or fully qualified identifier for the parameter. To set the parameter attribute: + provide the argument --parameter on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The location id of the parameter resource. To set the location attribute: + provide the argument --parameter on the command line with a fully specified name; + provide the argument --location on the command line. |


**Examples:**
```bash
To list all parameter versions of a parameter my-parameter in location
global run:

    $ gcloud parametermanager parameters versions list \
        --parameter=my-parameter --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/parametermanager/parameters/versions/list)

---
### `gcloud parametermanager parameters versions render`

Gets a single Parameter Manager parameter version render

Gets a single parameter version render resource.

**Synopsis:**
```
gcloud parametermanager parameters versions render
    (VERSION : --location=LOCATION --parameter=PARAMETER)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Version resource - Name of the resource The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument version on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  VERSION
     ID of the version or fully qualified identifier for the version.

     To set the version attribute:
     + provide the argument version on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the version resource.

     To set the location attribute:
     + provide the argument version on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --parameter=PARAMETER
     The parameter id of the version resource.

     To set the parameter attribute:
     + provide the argument version on the command line with a fully
       specified name;
     + provide the argument --parameter on the command line.
```

**Examples:**
```bash
To get a single parameter version render my-parameter-version of a
parameter my-parameter in location global run:

    $ gcloud parametermanager parameters versions render \
        my-parameter-version --parameter=my-parameter --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/parametermanager/parameters/versions/render)

---
### `gcloud parametermanager parameters versions update`

Updates the properties of a single Parameter Manager parameter version

Updates the properties of a single parameter version, including status of
the parameter version (enabled/disabled).

**Synopsis:**
```
gcloud parametermanager parameters versions update
    (VERSION : --location=LOCATION --parameter=PARAMETER) [--[no-]disabled]
    [--request-id=REQUEST_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Version resource - Identifier. [Output only] The resource name of the
ParameterVersion in the format
projects/*/locations/*/parameters/*/versions/*. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument version on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  VERSION
     ID of the version or fully qualified identifier for the version.

     To set the version attribute:
     + provide the argument version on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the version resource.

     To set the location attribute:
     + provide the argument version on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --parameter=PARAMETER
     The parameter id of the version resource.

     To set the parameter attribute:
     + provide the argument version on the command line with a fully
       specified name;
     + provide the argument --parameter on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--[no-]disabled` |  |  | Disabled boolean to determine if a ParameterVersion acts as a metadata only resource (payload is never returned if disabled is true). If true any calls will always default to BASIC view even if the user explicitly passes FULL view as part of the request. A render call on a disabled resource fails with an error. Default value is False. Use --disabled to enable and --no-disabled to disable. |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes since the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To update a parameter version my-parameter-version of parameter
my-parameter in location global run:

    $ gcloud parametermanager parameters versions update \
        my-parameter-version --parameter=my-parameter --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/parametermanager/parameters/versions/update)

---
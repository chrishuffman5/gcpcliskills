# gcloud apihub apis

manage Api resources

This file also covers the nested groups `apis versions` (manage Version resources), `apis versions operations` (manage Api Operation resources), and `apis versions specs` (manage Spec resources).

### `gcloud apihub apis create`

Create apis

Create an api. Note: The positional argument for API ID is currently not supported. Please use the --api flag to specify the API ID.

**Synopsis:**
```
gcloud apihub apis create --display-name=DISPLAY_NAME [--api=API]
    [--attributes=[ATTRIBUTES,...]] [--description=DESCRIPTION]
    [--documentation-external-uri=DOCUMENTATION_EXTERNAL_URI]
    [--fingerprint=FINGERPRINT] [--location=LOCATION]
    [--selected-version=SELECTED_VERSION]
    [--api-functional-requirements-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      | --api-functional-requirements-json-values=[API_FUNCTIONAL_REQUIREMENTS_JSON_VALUES,...]
      | --api-functional-requirements-string-values=[API_FUNCTIONAL_REQUIREMENTS_STRING_VALUES,...]
      | --api-functional-requirements-uri-values=[API_FUNCTIONAL_REQUIREMENTS_URI_VALUES,...]]
    [--api-requirements-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      | --api-requirements-json-values=[API_REQUIREMENTS_JSON_VALUES,...]
      | --api-requirements-string-values=[API_REQUIREMENTS_STRING_VALUES,...]
      | --api-requirements-uri-values=[API_REQUIREMENTS_URI_VALUES,...]]
    [--api-style-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      | --api-style-json-values=[API_STYLE_JSON_VALUES,...]
      | --api-style-string-values=[API_STYLE_STRING_VALUES,...]
      | --api-style-uri-values=[API_STYLE_URI_VALUES,...]]
    [--api-technical-requirements-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      | --api-technical-requirements-json-values=[API_TECHNICAL_REQUIREMENTS_JSON_VALUES,...]
      | --api-technical-requirements-string-values=[API_TECHNICAL_REQUIREMENTS_STRING_VALUES,...]
      | --api-technical-requirements-uri-values=[API_TECHNICAL_REQUIREMENTS_URI_VALUES,...]]
    [--business-unit-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      | --business-unit-json-values=[BUSINESS_UNIT_JSON_VALUES,...]
      | --business-unit-string-values=[BUSINESS_UNIT_STRING_VALUES,...]
      | --business-unit-uri-values=[BUSINESS_UNIT_URI_VALUES,...]]
    [--maturity-level-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      | --maturity-level-json-values=[MATURITY_LEVEL_JSON_VALUES,...]
      | --maturity-level-string-values=[MATURITY_LEVEL_STRING_VALUES,...]
      | --maturity-level-uri-values=[MATURITY_LEVEL_URI_VALUES,...]]
    [--owner-email=OWNER_EMAIL : --owner-display-name=OWNER_DISPLAY_NAME]
    [--target-user-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      | --target-user-json-values=[TARGET_USER_JSON_VALUES,...]
      | --target-user-string-values=[TARGET_USER_STRING_VALUES,...]
      | --target-user-uri-values=[TARGET_USER_URI_VALUES,...]]
    [--team-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      | --team-json-values=[TEAM_JSON_VALUES,...]
      | --team-string-values=[TEAM_STRING_VALUES,...]
      | --team-uri-values=[TEAM_URI_VALUES,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | The display name of the API resource. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--api` | API |  | For resources [api, selected-version], provides fallback value for resource api attribute. When the resource's full URI path is not provided, api will fallback to this flag value. |
| `--attributes` | [ATTRIBUTES,...] |  | The list of user defined attributes associated with the API resource. The key is the attribute name. It will be of the format: projects/{project}/locations/{location}/attributes/{attribute}. The value is the attribute values associated with the resource. |
| `--description` | DESCRIPTION |  | The description of the API resource. |
| `--documentation-external-uri` | DOCUMENTATION_EXTERNAL_URI |  | The uri of the externally hosted documentation. |
| `--fingerprint` | FINGERPRINT |  | Fingerprint of the API resource. This must be unique for each API resource. It can neither be unset nor be updated to an existing fingerprint of another API resource. |
| `--location` | LOCATION |  | For resources [api, selected-version], provides fallback value for resource location attribute. When the resource's full URI path is not provided, location will fallback to this flag value. |
| `--selected-version` | SELECTED_VERSION |  | ID of the version or fully qualified identifier for the version. |
| `--api-functional-requirements-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | The attribute values in case attribute data type is enum. Keys: description (detailed description of the value), displayName (display name of the value), id (4-63 characters), immutable (boolean). Mutually exclusive with the corresponding -json-values, -string-values, and -uri-values flags. |
| `--api-functional-requirements-json-values` | [API_FUNCTIONAL_REQUIREMENTS_JSON_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--api-functional-requirements-string-values` | [API_FUNCTIONAL_REQUIREMENTS_STRING_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--api-functional-requirements-uri-values` | [API_FUNCTIONAL_REQUIREMENTS_URI_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--api-requirements-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | The attribute values in case attribute data type is enum. Keys: description, displayName, id (4-63 characters), immutable (boolean). Mutually exclusive with the corresponding -json-values, -string-values, and -uri-values flags. |
| `--api-requirements-json-values` | [API_REQUIREMENTS_JSON_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--api-requirements-string-values` | [API_REQUIREMENTS_STRING_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--api-requirements-uri-values` | [API_REQUIREMENTS_URI_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--api-style-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | The attribute values in case attribute data type is enum. Keys: description, displayName, id (4-63 characters), immutable (boolean). Mutually exclusive with the corresponding -json-values, -string-values, and -uri-values flags. |
| `--api-style-json-values` | [API_STYLE_JSON_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--api-style-string-values` | [API_STYLE_STRING_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--api-style-uri-values` | [API_STYLE_URI_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--api-technical-requirements-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | The attribute values in case attribute data type is enum. Keys: description, displayName, id (4-63 characters), immutable (boolean). Mutually exclusive with the corresponding -json-values, -string-values, and -uri-values flags. |
| `--api-technical-requirements-json-values` | [API_TECHNICAL_REQUIREMENTS_JSON_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--api-technical-requirements-string-values` | [API_TECHNICAL_REQUIREMENTS_STRING_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--api-technical-requirements-uri-values` | [API_TECHNICAL_REQUIREMENTS_URI_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--business-unit-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | The attribute values in case attribute data type is enum. Keys: description, displayName, id (4-63 characters), immutable (boolean). Mutually exclusive with the corresponding -json-values, -string-values, and -uri-values flags. |
| `--business-unit-json-values` | [BUSINESS_UNIT_JSON_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--business-unit-string-values` | [BUSINESS_UNIT_STRING_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--business-unit-uri-values` | [BUSINESS_UNIT_URI_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--maturity-level-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | The attribute values in case attribute data type is enum. Keys: description, displayName, id (4-63 characters), immutable (boolean). Mutually exclusive with the corresponding -json-values, -string-values, and -uri-values flags. |
| `--maturity-level-json-values` | [MATURITY_LEVEL_JSON_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--maturity-level-string-values` | [MATURITY_LEVEL_STRING_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--maturity-level-uri-values` | [MATURITY_LEVEL_URI_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--owner-email` | OWNER_EMAIL |  | The email of the owner. This flag must be specified if any of the other owner arguments are specified. |
| `--owner-display-name` | OWNER_DISPLAY_NAME |  | The name of the owner. |
| `--target-user-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | The attribute values in case attribute data type is enum. Keys: description, displayName, id (4-63 characters), immutable (boolean). Mutually exclusive with the corresponding -json-values, -string-values, and -uri-values flags. |
| `--target-user-json-values` | [TARGET_USER_JSON_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--target-user-string-values` | [TARGET_USER_STRING_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--target-user-uri-values` | [TARGET_USER_URI_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--team-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | The attribute values in case attribute data type is enum. Keys: description, displayName, id (4-63 characters), immutable (boolean). Mutually exclusive with the corresponding -json-values, -string-values, and -uri-values flags. |
| `--team-json-values` | [TEAM_JSON_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--team-string-values` | [TEAM_STRING_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--team-uri-values` | [TEAM_URI_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |

**Examples:**
```bash
To create an API with the ID my-api, run:

    $ gcloud apihub apis create --api=my-api --display-name="My API" \
        --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/apis/create)

---
### `gcloud apihub apis delete`

Delete an Api

Delete an api.

**Synopsis:**
```
gcloud apihub apis delete ([API] : --location=LOCATION) [--force]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Api resource - The name of the API resource to delete. Format:
projects/{project}/locations/{location}/apis/{api}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument api on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  [API]
     ID of the api or fully qualified identifier for the api.

     To set the api attribute:
     + provide the argument api on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the api resource.

     To set the location attribute:
     + provide the argument api on the command line with a fully specified
       name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--force` |  |  | If set to true, any versions from this API will also be deleted. Otherwise, the request will only work if the API has no versions. |

**Examples:**
```bash
To delete an API with the ID my-api, run:

    $ gcloud apihub apis delete my-api --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/apis/delete)

---
### `gcloud apihub apis describe`

Describe an Api

Describe an api.

**Synopsis:**
```
gcloud apihub apis describe ([API] : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Api resource - The name of the API resource to retrieve. Format:
projects/{project}/locations/{location}/apis/{api}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument api on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  [API]
     ID of the api or fully qualified identifier for the api.

     To set the api attribute:
     + provide the argument api on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the api resource.

     To set the location attribute:
     + provide the argument api on the command line with a fully specified
       name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe an API with the ID my-api, run:

    $ gcloud apihub apis describe my-api --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/apis/describe)

---
### `gcloud apihub apis list`

List Apis

List apis.

**Synopsis:**
```
gcloud apihub apis list --location=LOCATION [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | ID of the location or fully qualified identifier for the location. Format: projects/{project}/locations/{location}. To set the location attribute, provide the argument --location on the command line. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--filter` | EXPRESSION |  | Apply a Boolean filter EXPRESSION to each resource item to be listed. If the expression evaluates True, then that item is listed. |
| `--limit` | LIMIT | unlimited | Maximum number of resources to list. The default is unlimited. |
| `--page-size` | PAGE_SIZE |  | Specifies the maximum number of resources per page. The default is determined by the service if it supports paging, otherwise it is unlimited (no paging). |
| `--sort-by` | [FIELD,...] |  | Comma-separated list of resource field key names to sort by. The default order is ascending. Prefix a field with "~" for descending order on that field. |
| `--uri` |  |  | Print a list of resource URIs instead of the default output, and change the command output to a list of URIs. |

**Examples:**
```bash
To list all APIs in project my-project and location us-central1, run:

    $ gcloud apihub apis list --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/apis/list)

---
### `gcloud apihub apis update`

Update apis

Update an api. Note: The positional argument for API ID is currently not supported. Please use the --api flag to specify the API ID.

**Synopsis:**
```
gcloud apihub apis update [--api=API] [--description=DESCRIPTION]
    [--display-name=DISPLAY_NAME] [--fingerprint=FINGERPRINT]
    [--location=LOCATION]
    [--attributes=[ATTRIBUTES,...]
      | --update-attributes=[UPDATE_ATTRIBUTES,...]
      --clear-attributes | --remove-attributes=REMOVE_ATTRIBUTES]
    [--clear-api-functional-requirements
      --api-functional-requirements-json-values=[API_FUNCTIONAL_REQUIREMENTS_JSON_VALUES,...]
      | --api-functional-requirements-string-values=[API_FUNCTIONAL_REQUIREMENTS_STRING_VALUES,...]
      | --api-functional-requirements-uri-values=[API_FUNCTIONAL_REQUIREMENTS_URI_VALUES,...]
      | --api-functional-requirements-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      | --add-api-functional-requirements-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      --clear-api-functional-requirements-enum-values
      | --remove-api-functional-requirements-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]]
    [--clear-api-requirements
      --api-requirements-json-values=[API_REQUIREMENTS_JSON_VALUES,...]
      | --api-requirements-string-values=[API_REQUIREMENTS_STRING_VALUES,...]
      | --api-requirements-uri-values=[API_REQUIREMENTS_URI_VALUES,...]
      | --api-requirements-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      | --add-api-requirements-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      --clear-api-requirements-enum-values
      | --remove-api-requirements-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]]
    [--clear-api-style
      --api-style-json-values=[API_STYLE_JSON_VALUES,...]
      | --api-style-string-values=[API_STYLE_STRING_VALUES,...]
      | --api-style-uri-values=[API_STYLE_URI_VALUES,...]
      | --api-style-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      | --add-api-style-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      --clear-api-style-enum-values
      | --remove-api-style-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]]
    [--clear-api-technical-requirements
      --api-technical-requirements-json-values=[API_TECHNICAL_REQUIREMENTS_JSON_VALUES,...]
      | --api-technical-requirements-string-values=[API_TECHNICAL_REQUIREMENTS_STRING_VALUES,...]
      | --api-technical-requirements-uri-values=[API_TECHNICAL_REQUIREMENTS_URI_VALUES,...]
      | --api-technical-requirements-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      | --add-api-technical-requirements-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      --clear-api-technical-requirements-enum-values
      | --remove-api-technical-requirements-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]]
    [--clear-business-unit
      --business-unit-json-values=[BUSINESS_UNIT_JSON_VALUES,...]
      | --business-unit-string-values=[BUSINESS_UNIT_STRING_VALUES,...]
      | --business-unit-uri-values=[BUSINESS_UNIT_URI_VALUES,...]
      | --business-unit-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      | --add-business-unit-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      --clear-business-unit-enum-values
      | --remove-business-unit-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]]
    [--clear-documentation
      --documentation-external-uri=DOCUMENTATION_EXTERNAL_URI]
    [--clear-maturity-level
      --maturity-level-json-values=[MATURITY_LEVEL_JSON_VALUES,...]
      | --maturity-level-string-values=[MATURITY_LEVEL_STRING_VALUES,...]
      | --maturity-level-uri-values=[MATURITY_LEVEL_URI_VALUES,...]
      | --maturity-level-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      | --add-maturity-level-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      --clear-maturity-level-enum-values
      | --remove-maturity-level-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]]
    [--clear-owner --owner-display-name=OWNER_DISPLAY_NAME
      --owner-email=OWNER_EMAIL]
    [--clear-selected-version | --selected-version=SELECTED_VERSION]
    [--clear-target-user
      --target-user-json-values=[TARGET_USER_JSON_VALUES,...]
      | --target-user-string-values=[TARGET_USER_STRING_VALUES,...]
      | --target-user-uri-values=[TARGET_USER_URI_VALUES,...]
      | --target-user-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      | --add-target-user-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      --clear-target-user-enum-values
      | --remove-target-user-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]]
    [--clear-team
      --team-json-values=[TEAM_JSON_VALUES,...]
      | --team-string-values=[TEAM_STRING_VALUES,...]
      | --team-uri-values=[TEAM_URI_VALUES,...]
      | --team-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      | --add-team-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      --clear-team-enum-values
      | --remove-team-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--api` | API |  | Provides fallback value for resource api attribute. When the resource's full URI path is not provided, api will fallback to this flag value. |
| `--description` | DESCRIPTION |  | The description of the API resource. |
| `--display-name` | DISPLAY_NAME |  | The display name of the API resource. |
| `--fingerprint` | FINGERPRINT |  | Fingerprint of the API resource. This must be unique for each API resource; it can neither be unset nor be updated to an existing fingerprint of another API resource. |
| `--location` | LOCATION |  | Provides fallback value for resource location attribute. When the resource's full URI path is not provided, location will fallback to this flag value. |
| `--attributes` | [ATTRIBUTES,...] |  | Set attributes to new value. The list of user defined attributes associated with the API resource. |
| `--update-attributes` | [UPDATE_ATTRIBUTES,...] |  | Update attributes value or add key value pair to the API resource. |
| `--clear-attributes` |  |  | Clear attributes value and set to empty map. |
| `--remove-attributes` | REMOVE_ATTRIBUTES |  | Remove existing value from map attributes. |
| `--clear-api-functional-requirements` |  |  | Set googleCloudApihubV1Api.apiFunctionalRequirements back to default value. |
| `--api-functional-requirements-json-values` | [API_FUNCTIONAL_REQUIREMENTS_JSON_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--api-functional-requirements-string-values` | [API_FUNCTIONAL_REQUIREMENTS_STRING_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--api-functional-requirements-uri-values` | [API_FUNCTIONAL_REQUIREMENTS_URI_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--api-functional-requirements-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Set enum values to new value. The attribute values in case attribute data type is enum. |
| `--add-api-functional-requirements-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Add new value to api_functional_requirements_enum_values list. |
| `--clear-api-functional-requirements-enum-values` |  |  | Clear enum values and set to empty list. |
| `--remove-api-functional-requirements-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Remove existing value from enum values list. |
| `--clear-api-requirements` |  |  | Set googleCloudApihubV1Api.apiRequirements back to default value. |
| `--api-requirements-json-values` | [API_REQUIREMENTS_JSON_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--api-requirements-string-values` | [API_REQUIREMENTS_STRING_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--api-requirements-uri-values` | [API_REQUIREMENTS_URI_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--api-requirements-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Set enum values to new value. The attribute values in case attribute data type is enum. |
| `--add-api-requirements-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Add new value to api_requirements_enum_values list. |
| `--clear-api-requirements-enum-values` |  |  | Clear enum values and set to empty list. |
| `--remove-api-requirements-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Remove existing value from enum values list. |
| `--clear-api-style` |  |  | Set googleCloudApihubV1Api.apiStyle back to default value. |
| `--api-style-json-values` | [API_STYLE_JSON_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--api-style-string-values` | [API_STYLE_STRING_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--api-style-uri-values` | [API_STYLE_URI_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--api-style-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Set enum values to new value. The attribute values in case attribute data type is enum. |
| `--add-api-style-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Add new value to api_style_enum_values list. |
| `--clear-api-style-enum-values` |  |  | Clear enum values and set to empty list. |
| `--remove-api-style-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Remove existing value from enum values list. |
| `--clear-api-technical-requirements` |  |  | Set googleCloudApihubV1Api.apiTechnicalRequirements back to default value. |
| `--api-technical-requirements-json-values` | [API_TECHNICAL_REQUIREMENTS_JSON_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--api-technical-requirements-string-values` | [API_TECHNICAL_REQUIREMENTS_STRING_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--api-technical-requirements-uri-values` | [API_TECHNICAL_REQUIREMENTS_URI_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--api-technical-requirements-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Set enum values to new value. The attribute values in case attribute data type is enum. |
| `--add-api-technical-requirements-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Add new value to api_technical_requirements_enum_values list. |
| `--clear-api-technical-requirements-enum-values` |  |  | Clear enum values and set to empty list. |
| `--remove-api-technical-requirements-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Remove existing value from enum values list. |
| `--clear-business-unit` |  |  | Set googleCloudApihubV1Api.businessUnit back to default value. |
| `--business-unit-json-values` | [BUSINESS_UNIT_JSON_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--business-unit-string-values` | [BUSINESS_UNIT_STRING_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--business-unit-uri-values` | [BUSINESS_UNIT_URI_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--business-unit-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Set enum values to new value. The attribute values in case attribute data type is enum. |
| `--add-business-unit-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Add new value to business_unit_enum_values list. |
| `--clear-business-unit-enum-values` |  |  | Clear enum values and set to empty list. |
| `--remove-business-unit-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Remove existing value from enum values list. |
| `--clear-documentation` |  |  | Set googleCloudApihubV1Api.documentation back to default value. |
| `--documentation-external-uri` | DOCUMENTATION_EXTERNAL_URI |  | The uri of the externally hosted documentation. |
| `--clear-maturity-level` |  |  | Set googleCloudApihubV1Api.maturityLevel back to default value. |
| `--maturity-level-json-values` | [MATURITY_LEVEL_JSON_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--maturity-level-string-values` | [MATURITY_LEVEL_STRING_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--maturity-level-uri-values` | [MATURITY_LEVEL_URI_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--maturity-level-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Set enum values to new value. The attribute values in case attribute data type is enum. |
| `--add-maturity-level-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Add new value to maturity_level_enum_values list. |
| `--clear-maturity-level-enum-values` |  |  | Clear enum values and set to empty list. |
| `--remove-maturity-level-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Remove existing value from enum values list. |
| `--clear-owner` |  |  | Set googleCloudApihubV1Api.owner back to default value. |
| `--owner-display-name` | OWNER_DISPLAY_NAME |  | The name of the owner. |
| `--owner-email` | OWNER_EMAIL |  | The email of the owner. |
| `--clear-selected-version` |  |  | Clear selected_version value and set to null. |
| `--selected-version` | SELECTED_VERSION |  | ID of the version or fully qualified identifier for the version. Format: projects/{project}/locations/{location}/apis/{api}/versions/{version}. |
| `--clear-target-user` |  |  | Set googleCloudApihubV1Api.targetUser back to default value. |
| `--target-user-json-values` | [TARGET_USER_JSON_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--target-user-string-values` | [TARGET_USER_STRING_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--target-user-uri-values` | [TARGET_USER_URI_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--target-user-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Set enum values to new value. The attribute values in case attribute data type is enum. |
| `--add-target-user-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Add new value to target_user_enum_values list. |
| `--clear-target-user-enum-values` |  |  | Clear enum values and set to empty list. |
| `--remove-target-user-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Remove existing value from enum values list. |
| `--clear-team` |  |  | Set googleCloudApihubV1Api.team back to default value. |
| `--team-json-values` | [TEAM_JSON_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--team-string-values` | [TEAM_STRING_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--team-uri-values` | [TEAM_URI_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--team-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Set enum values to new value. The attribute values in case attribute data type is enum. |
| `--add-team-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Add new value to team_enum_values list. |
| `--clear-team-enum-values` |  |  | Clear enum values and set to empty list. |
| `--remove-team-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Remove existing value from enum values list. |

**Examples:**
```bash
To update an API with the ID my-api, run:

    $ gcloud apihub apis update --api=my-api --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/apis/update)

---
### `gcloud apihub apis versions create`

Create a Version

Create a version.

**Synopsis:**
```
gcloud apihub apis versions create ([VERSION] : --api=API)
    --display-name=DISPLAY_NAME [--attributes=[ATTRIBUTES,...]]
    [--deployments=[DEPLOYMENTS,...]] [--description=DESCRIPTION]
    [--documentation-external-uri=DOCUMENTATION_EXTERNAL_URI]
    [--location=LOCATION] [--selected-deployment=SELECTED_DEPLOYMENT]
    [--accreditation-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      | --accreditation-json-values=[ACCREDITATION_JSON_VALUES,...]
      | --accreditation-string-values=[ACCREDITATION_STRING_VALUES,...]
      | --accreditation-uri-values=[ACCREDITATION_URI_VALUES,...]]
    [--compliance-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      | --compliance-json-values=[COMPLIANCE_JSON_VALUES,...]
      | --compliance-string-values=[COMPLIANCE_STRING_VALUES,...]
      | --compliance-uri-values=[COMPLIANCE_URI_VALUES,...]]
    [--lifecycle-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      | --lifecycle-json-values=[LIFECYCLE_JSON_VALUES,...]
      | --lifecycle-string-values=[LIFECYCLE_STRING_VALUES,...]
      | --lifecycle-uri-values=[LIFECYCLE_URI_VALUES,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Version resource - Identifier. The name of the version. Format:
projects/{project}/locations/{location}/apis/{api}/versions/{version}

To set the project attribute:
 * provide the argument version on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  [VERSION]
     ID of the version or fully qualified identifier for the version.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --api=API
     The api id of the version resource.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | The display name of the version. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attributes` | [ATTRIBUTES,...] |  | The list of user defined attributes associated with the Version resource. |
| `--deployments` | [DEPLOYMENTS,...] |  | IDs of the deployments or fully qualified identifiers for the deployments. |
| `--description` | DESCRIPTION |  | The description of the version. |
| `--documentation-external-uri` | DOCUMENTATION_EXTERNAL_URI |  | The uri of the externally hosted documentation. |
| `--location` | LOCATION |  | For resources [version, deployments, selected-deployment], provides fallback value for resource location attribute. |
| `--selected-deployment` | SELECTED_DEPLOYMENT |  | ID of the deployment or fully qualified identifier for the deployment. |
| `--accreditation-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | The attribute values in case attribute data type is enum. Mutually exclusive with the corresponding -json-values, -string-values, and -uri-values flags. |
| `--accreditation-json-values` | [ACCREDITATION_JSON_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--accreditation-string-values` | [ACCREDITATION_STRING_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--accreditation-uri-values` | [ACCREDITATION_URI_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--compliance-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | The attribute values in case attribute data type is enum. Mutually exclusive with the corresponding -json-values, -string-values, and -uri-values flags. |
| `--compliance-json-values` | [COMPLIANCE_JSON_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--compliance-string-values` | [COMPLIANCE_STRING_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--compliance-uri-values` | [COMPLIANCE_URI_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--lifecycle-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | The attribute values in case attribute data type is enum. Mutually exclusive with the corresponding -json-values, -string-values, and -uri-values flags. |
| `--lifecycle-json-values` | [LIFECYCLE_JSON_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--lifecycle-string-values` | [LIFECYCLE_STRING_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--lifecycle-uri-values` | [LIFECYCLE_URI_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |

**Examples:**
```bash
To create a version with the ID my-version for API my-api, run:

    $ gcloud apihub apis versions create --version=my-version \
        --api=my-api --display-name="My Version" --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/apis/versions/create)

---
### `gcloud apihub apis versions delete`

Delete a Version

Delete a version.

**Synopsis:**
```
gcloud apihub apis versions delete
    ([VERSION] : --api=API --location=LOCATION) [--force]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Version resource - The name of the version to delete. Format:
projects/{project}/locations/{location}/apis/{api}/versions/{version}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument version on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  [VERSION]
     ID of the version or fully qualified identifier for the version.

     To set the version attribute:
     + provide the argument version on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --api=API
     The api id of the version resource.

  --location=LOCATION
     The location id of the version resource.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--force` |  |  | If set to true, any specs from this version will also be deleted. Otherwise, the request will only work if the version has no specs. |

**Examples:**
```bash
To delete a version with the ID my-version for API my-api, run:

    $ gcloud apihub apis versions delete my-version --api=my-api \
        --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/apis/versions/delete)

---
### `gcloud apihub apis versions describe`

Describe a Version

Describe a version.

**Synopsis:**
```
gcloud apihub apis versions describe
    ([VERSION] : --api=API --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Version resource - The name of the API version to retrieve. Format:
projects/{project}/locations/{location}/apis/{api}/versions/{version}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument version on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  [VERSION]
     ID of the version or fully qualified identifier for the version.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --api=API
     The api id of the version resource.

  --location=LOCATION
     The location id of the version resource.
```

**Examples:**
```bash
To describe a version with the ID my-version for API my-api, run:

    $ gcloud apihub apis versions describe my-version --api=my-api \
        --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/apis/versions/describe)

---
### `gcloud apihub apis versions list`

List Versions

List versions.

**Synopsis:**
```
gcloud apihub apis versions list (--api=API : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--api` | API |  | ID of the api or fully qualified identifier for the api. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | The location id of the api resource. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--filter` | EXPRESSION |  | Apply a Boolean filter EXPRESSION to each resource item to be listed. If the expression evaluates True, then that item is listed. |
| `--limit` | LIMIT | unlimited | Maximum number of resources to list. The default is unlimited. |
| `--page-size` | PAGE_SIZE |  | Specifies the maximum number of resources per page. The default is determined by the service if it supports paging, otherwise it is unlimited (no paging). |
| `--sort-by` | [FIELD,...] |  | Comma-separated list of resource field key names to sort by. The default order is ascending. Prefix a field with "~" for descending order on that field. |
| `--uri` |  |  | Print a list of resource URIs instead of the default output. |

**Examples:**
```bash
To list all versions for API my-api, run:

    $ gcloud apihub apis versions list --api=my-api --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/apis/versions/list)

---
### `gcloud apihub apis versions update`

Update versions

Update a version.

**Synopsis:**
```
gcloud apihub apis versions update ([VERSION] : --api=API)
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [--location=LOCATION]
    [--attributes=[ATTRIBUTES,...]
      | --update-attributes=[UPDATE_ATTRIBUTES,...]
      --clear-attributes | --remove-attributes=REMOVE_ATTRIBUTES]
    [--clear-accreditation
      --accreditation-json-values=[ACCREDITATION_JSON_VALUES,...]
      | --accreditation-string-values=[ACCREDITATION_STRING_VALUES,...]
      | --accreditation-uri-values=[ACCREDITATION_URI_VALUES,...]
      | --accreditation-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      | --add-accreditation-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      --clear-accreditation-enum-values
      | --remove-accreditation-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]]
    [--clear-compliance
      --compliance-json-values=[COMPLIANCE_JSON_VALUES,...]
      | --compliance-string-values=[COMPLIANCE_STRING_VALUES,...]
      | --compliance-uri-values=[COMPLIANCE_URI_VALUES,...]
      | --compliance-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      | --add-compliance-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      --clear-compliance-enum-values
      | --remove-compliance-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]]
    [--clear-documentation
      --documentation-external-uri=DOCUMENTATION_EXTERNAL_URI]
    [--clear-lifecycle
      --lifecycle-json-values=[LIFECYCLE_JSON_VALUES,...]
      | --lifecycle-string-values=[LIFECYCLE_STRING_VALUES,...]
      | --lifecycle-uri-values=[LIFECYCLE_URI_VALUES,...]
      | --lifecycle-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      | --add-lifecycle-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      --clear-lifecycle-enum-values
      | --remove-lifecycle-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]]
    [--clear-selected-deployment | --selected-deployment=SELECTED_DEPLOYMENT]
    [--deployments=[DEPLOYMENTS,...]
      | --add-deployments=[ADD_DEPLOYMENTS,...]
      --clear-deployments | --remove-deployments=[REMOVE_DEPLOYMENTS,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Version resource - Identifier. The name of the version. Format:
projects/{project}/locations/{location}/apis/{api}/versions/{version}

To set the project attribute:
 * provide the argument version on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  [VERSION]
     ID of the version or fully qualified identifier for the version.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --api=API
     The api id of the version resource.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | The description of the version. |
| `--display-name` | DISPLAY_NAME |  | The display name of the version. |
| `--location` | LOCATION |  | For resources [version, deployments, selected-deployment], provides fallback value for resource location attribute. |
| `--attributes` | [ATTRIBUTES,...] |  | Set attributes to new value. The list of user defined attributes associated with the Version resource. |
| `--update-attributes` | [UPDATE_ATTRIBUTES,...] |  | Update attributes value or add key value pair. The list of user defined attributes. |
| `--clear-attributes` |  |  | Clear attributes value and set to empty map. |
| `--remove-attributes` | REMOVE_ATTRIBUTES |  | Remove existing value from map attributes. |
| `--clear-accreditation` |  |  | Set accreditation back to default value. |
| `--accreditation-json-values` | [ACCREDITATION_JSON_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--accreditation-string-values` | [ACCREDITATION_STRING_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--accreditation-uri-values` | [ACCREDITATION_URI_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--accreditation-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Set accreditation enum values to new value. The attribute values in case attribute data type is enum. |
| `--add-accreditation-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Add new value to accreditation enum values list. |
| `--clear-accreditation-enum-values` |  |  | Clear accreditation enum values and set to empty list. |
| `--remove-accreditation-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Remove existing value from accreditation enum values list. |
| `--clear-compliance` |  |  | Set compliance back to default value. |
| `--compliance-json-values` | [COMPLIANCE_JSON_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--compliance-string-values` | [COMPLIANCE_STRING_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--compliance-uri-values` | [COMPLIANCE_URI_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--compliance-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Set compliance enum values to new value. The attribute values in case attribute data type is enum. |
| `--add-compliance-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Add new value to compliance enum values list. |
| `--clear-compliance-enum-values` |  |  | Clear compliance enum values and set to empty list. |
| `--remove-compliance-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Remove existing value from compliance enum values list. |
| `--clear-documentation` |  |  | Set documentation back to default value. |
| `--documentation-external-uri` | DOCUMENTATION_EXTERNAL_URI |  | The uri of the externally hosted documentation. |
| `--clear-lifecycle` |  |  | Set lifecycle back to default value. |
| `--lifecycle-json-values` | [LIFECYCLE_JSON_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--lifecycle-string-values` | [LIFECYCLE_STRING_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--lifecycle-uri-values` | [LIFECYCLE_URI_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--lifecycle-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Set lifecycle enum values to new value. The attribute values in case attribute data type is enum. |
| `--add-lifecycle-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Add new value to lifecycle enum values list. |
| `--clear-lifecycle-enum-values` |  |  | Clear lifecycle enum values and set to empty list. |
| `--remove-lifecycle-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Remove existing value from lifecycle enum values list. |
| `--clear-selected-deployment` |  |  | Clear selected deployment value and set to null. |
| `--selected-deployment` | SELECTED_DEPLOYMENT |  | ID of the deployment or fully qualified identifier for the deployment. Format: projects/{project}/locations/{location}/deployments/{deployment}. |
| `--deployments` | [DEPLOYMENTS,...] |  | IDs of the deployments or fully qualified identifiers for the deployments. The deployments linked to this API version. |
| `--add-deployments` | [ADD_DEPLOYMENTS,...] |  | IDs of the deployments to add. The deployments linked to this API version. |
| `--clear-deployments` |  |  | Clear deployments value and set to empty list. |
| `--remove-deployments` | [REMOVE_DEPLOYMENTS,...] |  | IDs of the deployments to remove. The deployments linked to this API version. |

**Examples:**
```bash
To update a version with the ID my-version for API my-api, run:

    $ gcloud apihub apis versions update my-version --api=my-api \
        --display-name="New Display Name" --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/apis/versions/update)

---
### `gcloud apihub apis versions operations create`

Create apiOperations

Create an apiOperation.

**Synopsis:**
```
gcloud apihub apis versions operations create
    ([OPERATION] : --api=API --location=LOCATION --version=VERSION)
    [--attributes=[ATTRIBUTES,...]]
    [--details-deprecated --details-description=DETAILS_DESCRIPTION
      --documentation-external-uri=DOCUMENTATION_EXTERNAL_URI
      --http-operation-method=HTTP_OPERATION_METHOD
      --http-operation-path=HTTP_OPERATION_PATH
      --http-operation-path-description=HTTP_OPERATION_PATH_DESCRIPTION
      | --mcp-tool-name=MCP_TOOL_NAME
      : --mcp-tool-description=MCP_TOOL_DESCRIPTION
      --mcp-tool-input-schema-json=MCP_TOOL_INPUT_SCHEMA_JSON
      --mcp-tool-output-schema-json=MCP_TOOL_OUTPUT_SCHEMA_JSON
      --mcp-tool-title=MCP_TOOL_TITLE
      --mcp-tool-annotations-additional-hints=[MCP_TOOL_ANNOTATIONS_ADDITIONAL_HINTS,...]
      --mcp-tool-annotations-destructive-hint
      --mcp-tool-annotations-idempotent-hint
      --mcp-tool-annotations-open-world-hint
      --mcp-tool-annotations-read-only-hint
      --mcp-tool-annotations-title=MCP_TOOL_ANNOTATIONS_TITLE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - Identifier. The name of the operation. Format:
projects/{project}/locations/{location}/apis/{api}/versions/{version}/operations/{operation}

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  [OPERATION]
     ID of the operation or fully qualified identifier for the operation.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --api=API
     The api id of the operation resource.

  --location=LOCATION
     The location id of the operation resource.

  --version=VERSION
     The version id of the operation resource.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attributes` | [ATTRIBUTES,...] |  | The list of user defined attributes associated with the API operation resource. The key is the attribute name; format: projects/{project}/locations/{location}/attributes/{attribute}. |
| `--details-deprecated` |  |  | For OpenAPI spec, this will be set if operation.deprecated is marked as true in the spec. |
| `--details-description` | DETAILS_DESCRIPTION |  | Description of the operation behavior. For OpenAPI spec, this will map to operation.description in the spec, in case description is empty, operation.summary will be used. |
| `--documentation-external-uri` | DOCUMENTATION_EXTERNAL_URI |  | The uri of the externally hosted documentation. |
| `--http-operation-method` | HTTP_OPERATION_METHOD |  | Operation method. Even though this field is optional, it is required for CreateApiOperation API and it is recommended to be set. CHOICES: delete, get, head, options, patch, post, put, trace. |
| `--http-operation-path` | HTTP_OPERATION_PATH |  | Complete path relative to server endpoint. Even though this field is optional, it is required for CreateApiOperation API and it is recommended to be set. |
| `--http-operation-path-description` | HTTP_OPERATION_PATH_DESCRIPTION |  | A short description for the path applicable to all operations. |
| `--mcp-tool-name` | MCP_TOOL_NAME |  | The name of the tool, unique within its parent scope (version). This flag must be specified if any of the other mcp-tool arguments are specified. |
| `--mcp-tool-description` | MCP_TOOL_DESCRIPTION |  | The description of what the tool does. |
| `--mcp-tool-input-schema-json` | MCP_TOOL_INPUT_SCHEMA_JSON |  | The JSON schema for input. Should be valid JSON; semantic validation is not supported. |
| `--mcp-tool-output-schema-json` | MCP_TOOL_OUTPUT_SCHEMA_JSON |  | The JSON schema for output. Should be valid JSON; semantic validation is not supported. |
| `--mcp-tool-title` | MCP_TOOL_TITLE |  | The optional title of the tool. |
| `--mcp-tool-annotations-additional-hints` | [MCP_TOOL_ANNOTATIONS_ADDITIONAL_HINTS,...] |  | Additional hints which are not covered in the defaults. The key is the hint name and the value is the hint value. |
| `--mcp-tool-annotations-destructive-hint` |  |  | Hint indicating if the tool may have destructive side effects. |
| `--mcp-tool-annotations-idempotent-hint` |  |  | Hint indicating if the tool is idempotent. |
| `--mcp-tool-annotations-open-world-hint` |  |  | Hint indicating if the tool interacts with an open world (e.g., the internet). |
| `--mcp-tool-annotations-read-only-hint` |  |  | Hint indicating if the tool is read-only. |
| `--mcp-tool-annotations-title` | MCP_TOOL_ANNOTATIONS_TITLE |  | Human-readable title for the tool, if different from Tool.title. |

**Examples:**
```bash
To create the apiOperation, run:

    $ gcloud apihub apis versions operations create
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/apis/versions/operations/create)

---
### `gcloud apihub apis versions operations delete`

Delete apiOperations

Delete an apiOperation.

**Synopsis:**
```
gcloud apihub apis versions operations delete
    ([OPERATION] : --api=API --location=LOCATION --version=VERSION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The name of the operation resource to delete. Format:
projects/{project}/locations/{location}/apis/{api}/versions/{version}/operations/{operation}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  [OPERATION]
     ID of the operation or fully qualified identifier for the operation.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --api=API
     The api id of the operation resource.

  --location=LOCATION
     The location id of the operation resource.

  --version=VERSION
     The version id of the operation resource.
```

**Examples:**
```bash
To delete the apiOperation, run:

    $ gcloud apihub apis versions operations delete
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/apis/versions/operations/delete)

---
### `gcloud apihub apis versions operations describe`

Describe apiOperations

Describe an apiOperation.

**Synopsis:**
```
gcloud apihub apis versions operations describe
    ([OPERATION] : --api=API --location=LOCATION --version=VERSION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The name of the operation to retrieve. Format:
projects/{project}/locations/{location}/apis/{api}/versions/{version}/operations/{operation}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  [OPERATION]
     ID of the operation or fully qualified identifier for the operation.

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --api=API
     The api id of the operation resource.

  --location=LOCATION
     The location id of the operation resource.

  --version=VERSION
     The version id of the operation resource.
```

**Examples:**
```bash
To describe the apiOperation, run:

    $ gcloud apihub apis versions operations describe
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/apis/versions/operations/describe)

---
### `gcloud apihub apis versions operations list`

List apiOperations

List apiOperations.

**Synopsis:**
```
gcloud apihub apis versions operations list
    (--version=VERSION : --api=API --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--version` | VERSION |  | ID of the version or fully qualified identifier for the version. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--api` | API |  | The api id of the version resource. |
| `--location` | LOCATION |  | The location id of the version resource. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--filter` | EXPRESSION |  | Apply a Boolean filter EXPRESSION to each resource item to be listed. If the expression evaluates True, then that item is listed. |
| `--limit` | LIMIT | unlimited | Maximum number of resources to list. The default is unlimited. |
| `--page-size` | PAGE_SIZE |  | Specifies the maximum number of resources per page. The default is determined by the service if it supports paging, otherwise it is unlimited (no paging). |
| `--sort-by` | [FIELD,...] |  | Comma-separated list of resource field key names to sort by. The default order is ascending. Prefix a field with "~" for descending order on that field. |
| `--uri` |  |  | Print a list of resource URIs instead of the default output, and change the command output to a list of URIs. |

**Examples:**
```bash
To list all apiOperations, run:

    $ gcloud apihub apis versions operations list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/apis/versions/operations/list)

---
### `gcloud apihub apis versions operations update`

Update apiOperations

Update an apiOperation.

**Synopsis:**
```
gcloud apihub apis versions operations update
    ([OPERATION] : --api=API --location=LOCATION --version=VERSION)
    [--attributes=[ATTRIBUTES,...]
      | --update-attributes=[UPDATE_ATTRIBUTES,...]
      --clear-attributes | --remove-attributes=REMOVE_ATTRIBUTES]
    [--clear-details --[no-]details-deprecated
      --details-description=DETAILS_DESCRIPTION
      --documentation-external-uri=DOCUMENTATION_EXTERNAL_URI
      --http-operation-method=HTTP_OPERATION_METHOD
      --http-operation-path=HTTP_OPERATION_PATH
      --http-operation-path-description=HTTP_OPERATION_PATH_DESCRIPTION
      | --mcp-tool-description=MCP_TOOL_DESCRIPTION
      --mcp-tool-input-schema-json=MCP_TOOL_INPUT_SCHEMA_JSON
      --mcp-tool-name=MCP_TOOL_NAME
      --mcp-tool-output-schema-json=MCP_TOOL_OUTPUT_SCHEMA_JSON
      --mcp-tool-title=MCP_TOOL_TITLE
      --[no-]mcp-tool-annotations-destructive-hint
      --[no-]mcp-tool-annotations-idempotent-hint
      --[no-]mcp-tool-annotations-open-world-hint
      --[no-]mcp-tool-annotations-read-only-hint
      --mcp-tool-annotations-title=MCP_TOOL_ANNOTATIONS_TITLE
      --mcp-tool-annotations-additional-hints=[MCP_TOOL_ANNOTATIONS_ADDITIONAL_HINTS,...]
      | --update-mcp-tool-annotations-additional-hints=[UPDATE_MCP_TOOL_ANNOTATIONS_ADDITIONAL_HINTS,...]
      --clear-mcp-tool-annotations-additional-hints
      | --remove-mcp-tool-annotations-additional-hints=REMOVE_MCP_TOOL_ANNOTATIONS_ADDITIONAL_HINTS]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - Identifier. The name of the operation. Format:
projects/{project}/locations/{location}/apis/{api}/versions/{version}/operations/{operation}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  [OPERATION]
     ID of the operation or fully qualified identifier for the operation.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --api=API
     The api id of the operation resource.

  --location=LOCATION
     The location id of the operation resource.

  --version=VERSION
     The version id of the operation resource.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attributes` | [ATTRIBUTES,...] |  | Set attributes to new value. The list of user defined attributes associated with the API operation resource. |
| `--update-attributes` | [UPDATE_ATTRIBUTES,...] |  | Update attributes value or add key value pair. |
| `--clear-attributes` |  |  | Clear attributes value and set to empty map. |
| `--remove-attributes` | REMOVE_ATTRIBUTES |  | Remove existing values from map attributes. |
| `--clear-details` |  |  | Set operation details back to default value. |
| `--[no-]details-deprecated` |  |  | For OpenAPI spec, this will be set if operation.deprecated is marked as true in the spec. |
| `--details-description` | DETAILS_DESCRIPTION |  | Description of the operation behavior. |
| `--documentation-external-uri` | DOCUMENTATION_EXTERNAL_URI |  | The uri of the externally hosted documentation. |
| `--http-operation-method` | HTTP_OPERATION_METHOD |  | Operation method. CHOICES: delete, get, head, options, patch, post, put, trace. |
| `--http-operation-path` | HTTP_OPERATION_PATH |  | Complete path relative to server endpoint. |
| `--http-operation-path-description` | HTTP_OPERATION_PATH_DESCRIPTION |  | A short description for the path applicable to all operations. |
| `--mcp-tool-description` | MCP_TOOL_DESCRIPTION |  | The description of what the tool does. |
| `--mcp-tool-name` | MCP_TOOL_NAME |  | The name of the tool, unique within its parent scope (version). |
| `--mcp-tool-title` | MCP_TOOL_TITLE |  | The optional title of the tool. |
| `--mcp-tool-input-schema-json` | MCP_TOOL_INPUT_SCHEMA_JSON |  | The JSON schema for tool input. |
| `--mcp-tool-output-schema-json` | MCP_TOOL_OUTPUT_SCHEMA_JSON |  | The JSON schema for tool output. |
| `--[no-]mcp-tool-annotations-destructive-hint` |  |  | Hint indicating if the tool may have destructive side effects. |
| `--[no-]mcp-tool-annotations-idempotent-hint` |  |  | Hint indicating if the tool is idempotent. |
| `--[no-]mcp-tool-annotations-open-world-hint` |  |  | Hint indicating if the tool interacts with an open world. |
| `--[no-]mcp-tool-annotations-read-only-hint` |  |  | Hint indicating if the tool is read-only. |
| `--mcp-tool-annotations-title` | MCP_TOOL_ANNOTATIONS_TITLE |  | Human-readable title for the tool. |
| `--mcp-tool-annotations-additional-hints` | [MCP_TOOL_ANNOTATIONS_ADDITIONAL_HINTS,...] |  | Set additional hints to new value. |
| `--update-mcp-tool-annotations-additional-hints` | [UPDATE_MCP_TOOL_ANNOTATIONS_ADDITIONAL_HINTS,...] |  | Update additional hints value or add key value pair. |
| `--clear-mcp-tool-annotations-additional-hints` |  |  | Clear additional hints value and set to empty map. |
| `--remove-mcp-tool-annotations-additional-hints` | REMOVE_MCP_TOOL_ANNOTATIONS_ADDITIONAL_HINTS |  | Remove existing values from map additional hints. |

**Examples:**
```bash
To update an operation with the ID my-operation for version my-version
and API my-api, run:

    $ gcloud apihub apis versions operations update my-operation \
        --version=my-version --api=my-api \
        --details-description="New Description" --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/apis/versions/operations/update)

---
### `gcloud apihub apis versions specs create`

Create a Spec

Create a spec.

**Synopsis:**
```
gcloud apihub apis versions specs create
    ([SPEC] : --api=API --location=LOCATION --version=VERSION)
    --display-name=DISPLAY_NAME
    (--spec-type-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      | --spec-type-json-values=[SPEC_TYPE_JSON_VALUES,...]
      | --spec-type-string-values=[SPEC_TYPE_STRING_VALUES,...]
      | --spec-type-uri-values=[SPEC_TYPE_URI_VALUES,...])
    [--attributes=[ATTRIBUTES,...]]
    [--documentation-external-uri=DOCUMENTATION_EXTERNAL_URI]
    [--parsing-mode=PARSING_MODE] [--source-uri=SOURCE_URI]
    [--contents=CONTENTS --contents-mime-type=CONTENTS_MIME_TYPE]
    [--lint-response-create-time=LINT_RESPONSE_CREATE_TIME
      --lint-response-linter=LINT_RESPONSE_LINTER
      --lint-response-source=LINT_RESPONSE_SOURCE
      --lint-response-state=LINT_RESPONSE_STATE
      : --lint-response-issues=[code=CODE],[message=MESSAGE],[path=PATH],[range=RANGE],[severity=SEVERITY]
      --lint-response-summary=[count=COUNT],[severity=SEVERITY]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Spec resource - Identifier. The name of the spec. Format:
projects/{project}/locations/{location}/apis/{api}/versions/{version}/specs/{spec}

To set the project attribute:
 * provide the argument spec on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  [SPEC]
     ID of the spec or fully qualified identifier for the spec.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --api=API
     The api id of the spec resource.

  --location=LOCATION
     The location id of the spec resource.

  --version=VERSION
     The version id of the spec resource.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | The display name of the spec. This can contain the file name of the spec. |
| `--spec-type-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | The attribute values in case attribute data type is enum. Exactly one of the spec-type flags must be specified. |
| `--spec-type-json-values` | [SPEC_TYPE_JSON_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. Exactly one of the spec-type flags must be specified. |
| `--spec-type-string-values` | [SPEC_TYPE_STRING_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. Exactly one of the spec-type flags must be specified. |
| `--spec-type-uri-values` | [SPEC_TYPE_URI_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. Exactly one of the spec-type flags must be specified. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attributes` | [ATTRIBUTES,...] |  | The list of user defined attributes associated with the spec. The key is the attribute name. |
| `--documentation-external-uri` | DOCUMENTATION_EXTERNAL_URI |  | The uri of the externally hosted documentation. |
| `--parsing-mode` | PARSING_MODE |  | Specifies the parsing mode for the OpenAPI Specification. CHOICES: relaxed (parsing errors in the specification will not fail the API call), strict (parsing errors in the specification will fail the API call). |
| `--source-uri` | SOURCE_URI |  | The URI of the spec source in case file is uploaded from an external version control system. |
| `--contents` | CONTENTS |  | The contents of the spec. |
| `--contents-mime-type` | CONTENTS_MIME_TYPE |  | The mime type of the content for example application/json, application/yaml, application/wsdl etc. |
| `--lint-response-create-time` | LINT_RESPONSE_CREATE_TIME |  | Timestamp when the linting response was generated. |
| `--lint-response-linter` | LINT_RESPONSE_LINTER |  | Name of the linter used. CHOICES: other, spectral. |
| `--lint-response-source` | LINT_RESPONSE_SOURCE |  | Name of the linting application. |
| `--lint-response-state` | LINT_RESPONSE_STATE |  | Lint state represents success or failure for linting. CHOICES: lint-state-error, lint-state-success. |
| `--lint-response-issues` | [code=CODE],[message=MESSAGE],[path=PATH],[range=RANGE],[severity=SEVERITY] |  | Array of issues found in the analyzed document. |
| `--lint-response-summary` | [count=COUNT],[severity=SEVERITY] |  | Summary of all issue types and counts for each severity level. |

**Examples:**
```bash
To create a spec, run:

    $ gcloud apihub apis versions specs create --spec=my-spec \
        --version=my-version --api=my-api --display-name="My Spec" \
        --spec-type=openapi --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/apis/versions/specs/create)

---
### `gcloud apihub apis versions specs delete`

Delete a Spec

Delete a spec.

**Synopsis:**
```
gcloud apihub apis versions specs delete
    ([SPEC] : --api=API --location=LOCATION --version=VERSION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Spec resource - The name of the spec to delete. Format:
projects/{project}/locations/{location}/apis/{api}/versions/{version}/specs/{spec}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument spec on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  [SPEC]
     ID of the spec or fully qualified identifier for the spec.

     To set the spec attribute:
     + provide the argument spec on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --api=API
     The api id of the spec resource.

  --location=LOCATION
     The location id of the spec resource.

  --version=VERSION
     The version id of the spec resource.
```

**Examples:**
```bash
To delete a spec with the ID my-spec for version my-version and API
my-api, run:

    $ gcloud apihub apis versions specs delete my-spec \
        --version=my-version --api=my-api --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/apis/versions/specs/delete)

---
### `gcloud apihub apis versions specs describe`

Describe a Spec

Describe a spec.

**Synopsis:**
```
gcloud apihub apis versions specs describe
    ([SPEC] : --api=API --location=LOCATION --version=VERSION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Spec resource - The name of the spec to retrieve. Format:
projects/{project}/locations/{location}/apis/{api}/versions/{version}/specs/{spec}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument spec on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  [SPEC]
     ID of the spec or fully qualified identifier for the spec.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --api=API
     The api id of the spec resource.

  --location=LOCATION
     The location id of the spec resource.

  --version=VERSION
     The version id of the spec resource.
```

**Examples:**
```bash
To describe a spec with the ID my-spec for version my-version and API
my-api, run:

    $ gcloud apihub apis versions specs describe my-spec \
        --version=my-version --api=my-api --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/apis/versions/specs/describe)

---
### `gcloud apihub apis versions specs get-contents`

Get the contents of a spec

Get the contents of a spec.

**Synopsis:**
```
gcloud apihub apis versions specs get-contents [SPEC] --api=API
    --location=LOCATION --version=VERSION [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
  [SPEC]
     The spec ID.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--api` | API |  | The API ID. |
| `--location` | LOCATION |  | The location ID. |
| `--version` | VERSION |  | The version ID. |

**Examples:**
```bash
To get the contents of a spec, run:

    $ gcloud apihub apis versions specs get-contents SPEC --api=API \
        --version=VERSION --location=LOCATION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/apis/versions/specs/get-contents)

---
### `gcloud apihub apis versions specs lint`

Lint a Spec

Lint a spec.

**Synopsis:**
```
gcloud apihub apis versions specs lint
    ([SPEC] : --api=API --location=LOCATION --version=VERSION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Spec resource - The name of the spec to be linted. Format:
projects/{project}/locations/{location}/apis/{api}/versions/{version}/specs/{spec}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument spec on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  [SPEC]
     ID of the spec or fully qualified identifier for the spec.

     To set the spec attribute:
     + provide the argument spec on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --api=API
     The api id of the spec resource.

  --location=LOCATION
     The location id of the spec resource.

  --version=VERSION
     The version id of the spec resource.
```

**Examples:**
```bash
To lint a spec with the ID my-spec for version my-version and API my-api,
run:

    $ gcloud apihub apis versions specs lint my-spec \
        --version=my-version --api=my-api --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/apis/versions/specs/lint)

---
### `gcloud apihub apis versions specs list`

List Specs

List specs.

**Synopsis:**
```
gcloud apihub apis versions specs list
    (--version=VERSION : --api=API --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--version` | VERSION |  | ID of the version or fully qualified identifier for the version. The parent, which owns this collection of specs, is of format: projects/{project}/locations/{location}/apis/{api}/versions/{version}. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--api` | API |  | The api id of the version resource. |
| `--location` | LOCATION |  | The location id of the version resource. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--filter` | EXPRESSION |  | Apply a Boolean filter EXPRESSION to each resource item to be listed. If the expression evaluates True, then that item is listed. |
| `--limit` | LIMIT | unlimited | Maximum number of resources to list. The default is unlimited. |
| `--page-size` | PAGE_SIZE |  | Specifies the maximum number of resources per page. The default is determined by the service if it supports paging, otherwise it is unlimited (no paging). |
| `--sort-by` | [FIELD,...] |  | Comma-separated list of resource field key names to sort by. The default order is ascending. Prefix a field with "~" for descending order on that field. |
| `--uri` |  |  | Print a list of resource URIs instead of the default output. |

**Examples:**
```bash
To list all specs for version my-version and API my-api, run:

    $ gcloud apihub apis versions specs list --version=my-version \
        --api=my-api --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/apis/versions/specs/list)

---
### `gcloud apihub apis versions specs update`

Update specs

Update a spec.

**Synopsis:**
```
gcloud apihub apis versions specs update
    ([SPEC] : --api=API --location=LOCATION --version=VERSION)
    [--display-name=DISPLAY_NAME] [--parsing-mode=PARSING_MODE]
    [--source-uri=SOURCE_URI]
    [--attributes=[ATTRIBUTES,...]
      | --update-attributes=[UPDATE_ATTRIBUTES,...]
      --clear-attributes | --remove-attributes=REMOVE_ATTRIBUTES]
    [--clear-contents --contents=CONTENTS
      --contents-mime-type=CONTENTS_MIME_TYPE]
    [--clear-documentation
      --documentation-external-uri=DOCUMENTATION_EXTERNAL_URI]
    [--clear-lint-response
      --lint-response-create-time=LINT_RESPONSE_CREATE_TIME
      --lint-response-linter=LINT_RESPONSE_LINTER
      --lint-response-source=LINT_RESPONSE_SOURCE
      --lint-response-state=LINT_RESPONSE_STATE
      --lint-response-issues=[code=CODE],[message=MESSAGE],[path=PATH],[range=RANGE],[severity=SEVERITY]
      | --add-lint-response-issues=[code=CODE],[message=MESSAGE],[path=PATH],[range=RANGE],[severity=SEVERITY]
      --clear-lint-response-issues
      | --remove-lint-response-issues=[code=CODE],[message=MESSAGE],[path=PATH],[range=RANGE],[severity=SEVERITY]
      --lint-response-summary=[count=COUNT],[severity=SEVERITY]
      | --add-lint-response-summary=[count=COUNT],[severity=SEVERITY]
      --clear-lint-response-summary
      | --remove-lint-response-summary=[count=COUNT],[severity=SEVERITY]]
    [--clear-spec-type
      --spec-type-json-values=[SPEC_TYPE_JSON_VALUES,...]
      | --spec-type-string-values=[SPEC_TYPE_STRING_VALUES,...]
      | --spec-type-uri-values=[SPEC_TYPE_URI_VALUES,...]
      | --spec-type-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      | --add-spec-type-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      --clear-spec-type-enum-values
      | --remove-spec-type-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Spec resource - Identifier. The name of the spec. Format:
projects/{project}/locations/{location}/apis/{api}/versions/{version}/specs/{spec}

To set the project attribute:
 * provide the argument spec on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  [SPEC]
     ID of the spec or fully qualified identifier for the spec.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --api=API
     The api id of the spec resource.

  --location=LOCATION
     The location id of the spec resource.

  --version=VERSION
     The version id of the spec resource.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | The display name of the spec. This can contain the file name of the spec. |
| `--parsing-mode` | PARSING_MODE |  | Specifies the parsing mode for the OpenAPI Specification. CHOICES: relaxed (parsing errors in the specification will not fail the API call), strict (parsing errors in the specification will fail the API call). |
| `--source-uri` | SOURCE_URI |  | The URI of the spec source in case file is uploaded from an external version control system. |
| `--attributes` | [ATTRIBUTES,...] |  | Set attributes to new value. A map of attribute names to values. |
| `--update-attributes` | [UPDATE_ATTRIBUTES,...] |  | Update attributes value or add key value pair. |
| `--clear-attributes` |  |  | Clear attributes value and set to empty map. |
| `--remove-attributes` | REMOVE_ATTRIBUTES |  | Remove existing value from map attributes. |
| `--clear-contents` |  |  | Set googleCloudApihubV1Spec.contents back to default value. |
| `--contents` | CONTENTS |  | The contents of the spec. |
| `--contents-mime-type` | CONTENTS_MIME_TYPE |  | The mime type of the content for example application/json, application/yaml, application/wsdl etc. |
| `--clear-documentation` |  |  | Set googleCloudApihubV1Spec.documentation back to default value. |
| `--documentation-external-uri` | DOCUMENTATION_EXTERNAL_URI |  | The uri of the externally hosted documentation. |
| `--clear-lint-response` |  |  | Set lint response back to default value. |
| `--lint-response-create-time` | LINT_RESPONSE_CREATE_TIME |  | Timestamp when the linting response was generated. |
| `--lint-response-linter` | LINT_RESPONSE_LINTER |  | Name of the linter used. CHOICES: other, spectral. |
| `--lint-response-source` | LINT_RESPONSE_SOURCE |  | Name of the linting application. |
| `--lint-response-state` | LINT_RESPONSE_STATE |  | Lint state represents success or failure for linting. CHOICES: lint-state-error, lint-state-success. |
| `--lint-response-issues` | [code=CODE],[message=MESSAGE],[path=PATH],[range=RANGE],[severity=SEVERITY] |  | Set lint_response_issues to new value. |
| `--add-lint-response-issues` | [code=CODE],[message=MESSAGE],[path=PATH],[range=RANGE],[severity=SEVERITY] |  | Add new value to lint_response_issues list. |
| `--clear-lint-response-issues` |  |  | Clear lint_response_issues value and set to empty list. |
| `--remove-lint-response-issues` | [code=CODE],[message=MESSAGE],[path=PATH],[range=RANGE],[severity=SEVERITY] |  | Remove existing value from lint_response_issues list. |
| `--lint-response-summary` | [count=COUNT],[severity=SEVERITY] |  | Set lint_response_summary to new value. |
| `--add-lint-response-summary` | [count=COUNT],[severity=SEVERITY] |  | Add new value to lint_response_summary list. |
| `--clear-lint-response-summary` |  |  | Clear lint_response_summary value and set to empty list. |
| `--remove-lint-response-summary` | [count=COUNT],[severity=SEVERITY] |  | Remove existing value from lint_response_summary list. |
| `--clear-spec-type` |  |  | Set googleCloudApihubV1Spec.specType back to default value. |
| `--spec-type-json-values` | [SPEC_TYPE_JSON_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--spec-type-string-values` | [SPEC_TYPE_STRING_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--spec-type-uri-values` | [SPEC_TYPE_URI_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. |
| `--spec-type-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Set spec_type_enum_values to new value. The attribute values in case attribute data type is enum. |
| `--add-spec-type-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Add new value to spec_type_enum_values list. |
| `--clear-spec-type-enum-values` |  |  | Clear spec_type_enum_values and set to empty list. |
| `--remove-spec-type-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Remove existing value from spec_type_enum_values list. |

**Examples:**
```bash
To update a spec with the ID my-spec for version my-version and API
my-api, run:

    $ gcloud apihub apis versions specs update my-spec \
        --version=my-version --api=my-api --display-name="New Spec Name" \
        --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/apis/versions/specs/update)

---

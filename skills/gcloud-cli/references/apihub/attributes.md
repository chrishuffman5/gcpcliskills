# gcloud apihub attributes

manage Attribute resources

### `gcloud apihub attributes create`

Create an Attribute

Create an attribute.

**Synopsis:**
```
gcloud apihub attributes create ([ATTRIBUTE] : --location=LOCATION)
    --data-type=DATA_TYPE --display-name=DISPLAY_NAME --scope=SCOPE
    [--allowed-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]]
    [--cardinality=CARDINALITY] [--description=DESCRIPTION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Attribute resource - Identifier. The name of the attribute in the API
Hub.

Format:
projects/{project}/locations/{location}/attributes/{attribute} The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group
but can be set in other ways.

To set the project attribute:
 * provide the argument attribute on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ATTRIBUTE
     ID of the attribute or fully qualified identifier for the
     attribute.

     To set the attribute attribute:
     + provide the argument attribute on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the attribute resource.

     To set the location attribute:
     + provide the argument attribute on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--data-type` | DATA_TYPE |  | The type of the data of the attribute. DATA_TYPE must be one of: enum, json, string, uri. |
| `--display-name` | DISPLAY_NAME |  | The display name of the attribute. |
| `--scope` | SCOPE |  | The scope of the attribute. It represents the resource in the API Hub to which the attribute can be linked. SCOPE must be one of: api, api-operation, definition, dependency, deployment, external-api, plugin, spec, version. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allowed-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | The list of allowed values when the attribute value is of type enum. This is required when the data_type of the attribute is ENUM. The maximum number of allowed values of an attribute will be 1000. Keys: description — the detailed description of the allowed value; displayName — the display name of the allowed value; id — the ID of the allowed value (if provided, the same will be used; the service will throw an error if the specified id is already used by another allowed value in the same attribute resource; if not provided, a system generated id derived from the display name will be used, and the service will handle conflict resolution by adding a system generated suffix in case of duplicates; this value should be 4-63 characters, and valid characters are /[a-z][0-9]-/); immutable — when set to true, the allowed value cannot be updated or deleted by the user (it can only be true for System defined attributes). Accepts key=value shorthand, a JSON string, or a path to a JSON/YAML file. |
| `--cardinality` | CARDINALITY | 1 | The maximum number of values that the attribute can have when associated with an API Hub resource. Cardinality 1 would represent a single-valued attribute. It must not be less than 1 or greater than 20. If not specified, the cardinality would be set to 1 by default and represent a single-valued attribute. |
| `--description` | DESCRIPTION |  | The description of the attribute. |

**Examples:**
```bash
To create an attribute with the ID my-attribute, run:

    $ gcloud apihub attributes create --attribute=my-attribute \
        --display-name="My Attribute" --scope=api --data-type=string \
        --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/attributes/create)

---
### `gcloud apihub attributes delete`

Delete an Attribute

Delete an attribute.

**Synopsis:**
```
gcloud apihub attributes delete ([ATTRIBUTE] : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Attribute resource - The name of the attribute to delete. Format:
projects/{project}/locations/{location}/attributes/{attribute} The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group
but can be set in other ways.

To set the project attribute:
 * provide the argument attribute on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ATTRIBUTE
     ID of the attribute or fully qualified identifier for the
     attribute.

     To set the attribute attribute:
     + provide the argument attribute on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the attribute resource.

     To set the location attribute:
     + provide the argument attribute on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To delete an attribute with the ID my-attribute, run:

    $ gcloud apihub attributes delete my-attribute --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/attributes/delete)

---
### `gcloud apihub attributes describe`

Describe an Attribute

Describe an attribute.

**Synopsis:**
```
gcloud apihub attributes describe ([ATTRIBUTE] : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Attribute resource - The name of the attribute to retrieve. Format:
projects/{project}/locations/{location}/attributes/{attribute} The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group
but can be set in other ways.

To set the project attribute:
 * provide the argument attribute on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ATTRIBUTE
     ID of the attribute or fully qualified identifier for the
     attribute.

     To set the attribute attribute:
     + provide the argument attribute on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the attribute resource.

     To set the location attribute:
     + provide the argument attribute on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe an attribute with the ID my-attribute, run:

    $ gcloud apihub attributes describe my-attribute \
        --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/attributes/describe)

---
### `gcloud apihub attributes list`

List Attributes

List attributes.

**Synopsis:**
```
gcloud apihub attributes list --location=LOCATION [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Location resource - The parent resource for Attribute. Format: projects/{project}/locations/{location}. This represents a Cloud resource. (NOTE) Some attributes are not given arguments in this group but can be set in other ways. To set the project attribute: provide the argument --location on the command line with a fully specified name; provide the argument --project on the command line; set the property core/project. This must be specified. ID of the location or fully qualified identifier for the location. To set the location attribute: provide the argument --location on the command line. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--filter` | EXPRESSION |  | Apply a Boolean filter EXPRESSION to each resource item to be listed. If the expression evaluates True, then that item is listed. |
| `--limit` | LIMIT | unlimited | Maximum number of resources to list. The default is unlimited. |
| `--page-size` | PAGE_SIZE |  | Some services group resource list output into pages. This flag specifies the maximum number of resources per page. |
| `--sort-by` | [FIELD,...] |  | Comma-separated list of resource field key names to sort by. The default order is ascending. Prefix a field with "~" for descending order on that field. |
| `--uri` |  |  | Print a list of resource URIs instead of the default output, and change the command output to a list of URIs. |

**Examples:**
```bash
To list all attributes in project my-project and location us-central1,
run:

    $ gcloud apihub attributes list --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/attributes/list)

---
### `gcloud apihub attributes update`

Update an Attribute

Update an attribute.

**Synopsis:**
```
gcloud apihub attributes update ([ATTRIBUTE] : --location=LOCATION)
    [--cardinality=CARDINALITY] [--data-type=DATA_TYPE]
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [--scope=SCOPE]
    [--allowed-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      | --add-allowed-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      --clear-allowed-values
      | --remove-allowed-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Attribute resource - Identifier. The name of the attribute in the API
Hub.

Format:
projects/{project}/locations/{location}/attributes/{attribute} The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group
but can be set in other ways.

To set the project attribute:
 * provide the argument attribute on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ATTRIBUTE
     ID of the attribute or fully qualified identifier for the
     attribute.

     To set the attribute attribute:
     + provide the argument attribute on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the attribute resource.

     To set the location attribute:
     + provide the argument attribute on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--add-allowed-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Add new value to allowed_values list. The list of allowed values when the attribute value is of type enum. This is required when the data_type of the attribute is ENUM. The maximum number of allowed values of an attribute will be 1000. Same keys and input formats as --allowed-values. |
| `--allowed-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Set allowed_values to new value. The list of allowed values when the attribute value is of type enum. This is required when the data_type of the attribute is ENUM. The maximum number of allowed values of an attribute will be 1000. Keys: description — the detailed description of the allowed value; displayName — the display name of the allowed value; id — the ID of the allowed value (if provided, the same will be used; the service will throw an error if the specified id is already used by another allowed value in the same attribute resource; if not provided, a system generated id derived from the display name will be used, and the service will handle conflict resolution by adding a system generated suffix in case of duplicates; this value should be 4-63 characters, and valid characters are /[a-z][0-9]-/); immutable — when set to true, the allowed value cannot be updated or deleted by the user (it can only be true for System defined attributes). Accepts key=value shorthand, a JSON string, or a path to a JSON/YAML file. |
| `--cardinality` | CARDINALITY | 1 | The maximum number of values that the attribute can have when associated with an API Hub resource. Cardinality 1 would represent a single-valued attribute. It must not be less than 1 or greater than 20. If not specified, the cardinality would be set to 1 by default and represent a single-valued attribute. |
| `--clear-allowed-values` |  |  | Clear allowed_values value and set to empty list. |
| `--data-type` | DATA_TYPE |  | The type of the data of the attribute. DATA_TYPE must be one of: enum, json, string, uri. |
| `--description` | DESCRIPTION |  | The description of the attribute. |
| `--display-name` | DISPLAY_NAME |  | The display name of the attribute. |
| `--remove-allowed-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Remove existing value from allowed_values list. The list of allowed values when the attribute value is of type enum. This is required when the data_type of the attribute is ENUM. The maximum number of allowed values of an attribute will be 1000. Same keys and input formats as --allowed-values. |
| `--scope` | SCOPE |  | The scope of the attribute. It represents the resource in the API Hub to which the attribute can be linked. SCOPE must be one of: api, api-operation, definition, dependency, deployment, external-api, plugin, spec, version. |

**Examples:**
```bash
To update the display name of an attribute with the ID my-attribute,
run:

    $ gcloud apihub attributes update my-attribute \
        --display-name="New Display Name" --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/attributes/update)

---

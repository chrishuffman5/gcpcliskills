# gcloud dataplex entries

manage Dataplex Catalog Entries resources

### `gcloud dataplex entries create`

Create a Dataplex Entry resource

Create a Dataplex Entry resource.

**Synopsis:**
```
gcloud dataplex entries create
    (ENTRY : --entry-group=ENTRY_GROUP --location=LOCATION)
    (--entry-type=ENTRY_TYPE : --entry-type-location=ENTRY_TYPE_LOCATION
      --entry-type-project=ENTRY_TYPE_PROJECT)
    [--aspects=YAML_OR_JSON_FILE]
    [--fully-qualified-name=FULLY_QUALIFIED_NAME]
    [--parent-entry=PARENT_ENTRY]
    [--entry-source-ancestors=[ANCESTORS,...]
      --entry-source-create-time=DATE_TIME
      --entry-source-description=DESCRIPTION
      --entry-source-display-name=DISPLAY_NAME
      --entry-source-labels=[KEY=VALUE,...]
      --entry-source-platform=PLATFORM_NAME
      --entry-source-resource=RESOURCE --entry-source-system=SYSTEM_NAME
      --entry-source-update-time=DATE_TIME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Entry resource - Arguments and flags that define the Dataplex Entry you
want to reference. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument entry on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENTRY
     ID of the entry or fully qualified identifier for the entry.

     To set the entry attribute:
     + provide the argument entry on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --entry-group=ENTRY_GROUP
     Entry group containing Dataplex Entries.

     To set the entry-group attribute:
     + provide the argument entry on the command line with a fully
       specified name;
     + provide the argument --entry-group on the command line.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument entry on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--entry-type` | ENTRY_TYPE |  | _[This must be specified.]_ ID of the entry type or fully qualified identifier for the entry type. To set the entry_type attribute: + provide the argument --entry-type on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--entry-type-location` | ENTRY_TYPE_LOCATION |  | _[This must be specified.]_ The location of the EntryType resource. To set the entry-type-location attribute: + provide the argument --entry-type on the command line with a fully specified name; + provide the argument --entry-type-location on the command line. |
| `--entry-type-project` | ENTRY_TYPE_PROJECT |  | _[This must be specified.]_ The project of the EntryType resource. To set the entry-type-project attribute: + provide the argument --entry-type on the command line with a fully specified name; + provide the argument --entry-type-project on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--aspects` | YAML_OR_JSON_FILE |  | Path to a YAML or JSON file containing Aspects to add or update. When this flag is specified, only Aspects referenced in the file are going to be added or updated. Specifying this flag does not remove any Aspects from the entry. In other words, specifying this flag will not lead to a full replacement of Aspects with a contents of the provided file. Content of the file contains a map, where keys are in the format ASPECT_TYPE@PATH, or just ASPECT_TYPE, if the Aspect is attached to an entry itself rather than to a specific column defined in the schema. Values in the map represent Aspect's content, which must conform to a template defined for a given ASPECT_TYPE. Each Aspect will be replaced fully by the provided content. That means data in the Aspect will be replaced and not merged with existing contents of that Aspect in the Entry. ASPECT_TYPE is expected to be in a format PROJECT_ID.LOCATION.ASPECT_TYPE_ID. PATH can be either empty (which means a 'root' path, such that Aspect is attached to the entry itself) or point to a specific column defined in the schema. For example: Schema.some_column. Example YAML format: project-id1.us-central1.my-aspect-type1: data: aspectField1: someValue aspectField2: someOtherValue project-id2.us-central1.my-aspect-type2@Schema.column1: data: aspectField3: someValue3 Example JSON format: { "project-id1.us-central1.my-aspect-type1": { "data": { "aspectField1": "someValue", "aspectField2": "someOtherValue" } }, "project-id2.us-central1.my-aspect-type2@Schema.column1": { "data": { "aspectField3": "someValue3" } } } |
| `--fully-qualified-name` | FULLY_QUALIFIED_NAME |  | A name for the entry that can reference it in an external system. The maximum size of the field is 4000 characters. |


**Examples:**
```bash
To create a Dataplex entry with name my-dataplex-entry in location
us-central1 in entry group my-entry-group and with entry type
projects/my-project/locations/us-central1/entryTypes/my-type, run:

    $ gcloud dataplex entries create my-dataplex-entry \
        --location=us-central1 --entry_group=my-entry-group \
        --entry-type \
        projects/my-project/locations/us-central1/entryTypes/my-type

To create a Dataplex Entry with name my-child-entry and set its parent to
an existing entry my-parent-entry, run:

    $ gcloud dataplex entries create my-child-entry \
        --location=us-central1 --entry_group=my-entry-group \
        --entry-type \
        projects/my-project/locations/us-central1/entryTypes/my-type \
        --parent-entry \
        projects/my-project/locations/us-central1/entryGroups/\
    my-entry-group/entries/my-parent-entry

To create a Dataplex Entry with its description, display name, ancestors,
labels and timestamps populated in its EntrySource, run:

    $ gcloud dataplex entries create my-entry --location=us-central1 \
        --entry_group=my-entry-group \
        --entry-type \
        projects/my-project/locations/us-central1/entryTypes/my-type \
        --entry-source-description \
        'This is a description of the Entry.' \
        --entry-source-display-name 'display name' \
        --entry-source-ancestors \
        '{"type":"projects/my-project/locations/us-central1/entryTypes/s\
    ome-type",
     "name":"projects/my-project/locations/us-central1/entryGroups/my-en\
    try-group/entries/ancestor-entry"},
     {"type":"projects/my-project/locations/us-central1/entryTypes/anoth\
    er-type",
     "name":"projects/my-project/locations/us-central1/entryGroups/my-en\
    try-group/entries/another-ancestor-entry"}' \
        --entry-source-labels key1=value1,key2=value2 \
        --entry-source-create-time 2024-01-01T09:39:25.160173Z \
        --entry-source-update-time 2024-01-01T09:39:25.160173Z

To create a Dataplex Entry reading its aspects from a YAML file, run:

    $ gcloud dataplex entries create my-entry --location=us-central1 \
        --entry_group=my-entry-group \
        --entry-type \
        projects/my-project/locations/us-central1/entryTypes/my-type \
        --aspects aspects.yaml

The file containing the aspects has the following format:

    my-project.us-central1.my-aspect-type:
      aspectType: my-project.us-central1.my-aspect-type
      createTime: "2024-01-01T09:39:25.160173Z"
      updateTime: "2024-01-01T09:39:25.160173Z"
      data:
        {}
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/entries/create)

---
### `gcloud dataplex entries delete`

Delete a Dataplex entry

Delete a Dataplex entry.

**Synopsis:**
```
gcloud dataplex entries delete
    (ENTRY : --entry-group=ENTRY_GROUP --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Entry resource - Entry to delete. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument entry on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENTRY
     ID of the entry or fully qualified identifier for the entry.

     To set the entry attribute:
     + provide the argument entry on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --entry-group=ENTRY_GROUP
     Entry group containing Dataplex Entries.

     To set the entry-group attribute:
     + provide the argument entry on the command line with a fully
       specified name;
     + provide the argument --entry-group on the command line.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument entry on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Examples:**
```bash
To delete the entry 'entry1', run:

    $ gcloud dataplex entries delete entry1 --entry-group=entry-group1 \
        --location=us-central1 --project=test-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/entries/delete)

---
### `gcloud dataplex entries describe`

Describe a Dataplex entry

Describe a Dataplex entry.

Displays the details of a Dataplex entry resource given a valid entry ID.

**Synopsis:**
```
gcloud dataplex entries describe
    (ENTRY : --entry-group=ENTRY_GROUP --location=LOCATION)
    [--aspect-types=[ASPECT_TYPES,...]] [--paths=[PATHS,...]] [--view=VIEW]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Entry resource - Arguments and flags that define the Dataplex Entry you
want to describe. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument entry on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENTRY
     ID of the entry or fully qualified identifier for the entry.

     To set the entry attribute:
     + provide the argument entry on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --entry-group=ENTRY_GROUP
     Entry group containing Dataplex Entries.

     To set the entry-group attribute:
     + provide the argument entry on the command line with a fully
       specified name;
     + provide the argument --entry-group on the command line.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument entry on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--aspect-types` | [ASPECT_TYPES,...] |  | Limits the aspects returned to the provided aspect types. Only works if the --view=custom is selected. For example, if two aspect types are specified: "projects/projectA/locations/us-central1/my-aspect-type,projects/projectB/locations/us/my-aspect-type2" then only aspects matching these aspect types will be returned. Can be further constrained by the --paths argument. |
| `--paths` | [PATHS,...] |  | Limits the aspects returned to those associated with the provided paths within the Entry. Only works if the --view=custom is selected. For example, if two paths are specified: "--paths=property1,property2" then only aspects on these paths will be returned. To return aspects without any path, the empty (root) path can be specified. For this "." can be used. For example, when "--paths=.,property1" are specified, then only aspects on the path "property1" and on the entry itself will be returned. Can be further constrained by --aspect-types argument. |
| `--view` | one of: all Returns all aspects |  | Controls which parts of an entry are to be returned. VIEW must be one of: all Returns all aspects. If the number of aspects would exceed 100, the first 100 will be returned. basic Returns entry only, without aspects. custom Returns aspects filtered based on --aspect-types AND --paths arguments specified. When used, at least one of --aspect-types and --paths arguments must be specified. If the number of aspects would exceed 100, the first 100 will be returned. full Default value. Returns all required aspects, as well as the keys of all non-required aspects. |


**Examples:**
```bash
To describe a Dataplex entry entry1 within entry group entry-group1 in
location us-central1, run:

    $ gcloud dataplex entries describe entry1 \
        --entry-group=entry-group1 --location=us-central1 \
        --project=test-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/entries/describe)

---
### `gcloud dataplex entries list`

List Dataplex entries

List Dataplex entries in an entry group.

**Synopsis:**
```
gcloud dataplex entries list
    (--entry-group=ENTRY_GROUP : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--entry-group` | ENTRY_GROUP |  | _[This must be specified.]_ ID of the entry group or fully qualified identifier for the entry group. To set the entry-group attribute: + provide the argument --entry-group on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Location of the Dataplex resource. To set the location attribute: + provide the argument --entry-group on the command line with a fully specified name; + provide the argument --location on the command line; + set the property dataplex/location. |


**Examples:**
```bash
To List the entries in entry group 'entry-group1', run:

    $ gcloud dataplex entries list --entry-group=entry-group1 \
        --location=us-central1 --project=test-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/entries/list)

---
### `gcloud dataplex entries lookup`

Lookup a Dataplex entry

Lookup a Dataplex entry.

Displays the details of a Dataplex entry resource given a valid entry ID.
Unlike describe, where the Dataplex permission is required for access, for
lookup the permission from the original source system is required on the
entry instead. For example, if the source is a BigQuery table, you need the
bigquery.tables.get permission to lookup an entry.

**Synopsis:**
```
gcloud dataplex entries lookup
    (ENTRY : --entry-group=ENTRY_GROUP --location=LOCATION)
    [--aspect-types=[ASPECT_TYPES,...]] [--paths=[PATHS,...]] [--view=VIEW]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Entry resource - Arguments and flags that define the Dataplex Entry you
want to lookup. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument entry on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENTRY
     ID of the entry or fully qualified identifier for the entry.

     To set the entry attribute:
     + provide the argument entry on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --entry-group=ENTRY_GROUP
     Entry group containing Dataplex Entries.

     To set the entry-group attribute:
     + provide the argument entry on the command line with a fully
       specified name;
     + provide the argument --entry-group on the command line.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument entry on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--aspect-types` | [ASPECT_TYPES,...] |  | Limits the aspects returned to the provided aspect types. Only works if the --view=custom is selected. For example, if two aspect types are specified: "projects/projectA/locations/us-central1/my-aspect-type,projects/projectB/locations/us/my-aspect-type2" then only aspects matching these aspect types will be returned. Can be further constrained by the --paths argument. |
| `--paths` | [PATHS,...] |  | Limits the aspects returned to those associated with the provided paths within the Entry. Only works if the --view=custom is selected. For example, if two paths are specified: "--paths=property1,property2" then only aspects on these paths will be returned. To return aspects without any path, the empty (root) path can be specified. For this "." can be used. For example, when "--paths=.,property1" are specified, then only aspects on the path "property1" and on the entry itself will be returned. Can be further constrained by --aspect-types argument. |
| `--view` | one of: all Returns all aspects |  | Controls which parts of an entry are to be returned. VIEW must be one of: all Returns all aspects. If the number of aspects would exceed 100, the first 100 will be returned. basic Returns entry only, without aspects. custom Returns aspects filtered based on --aspect-types AND --paths arguments specified. When used, at least one of --aspect-types and --paths arguments must be specified. If the number of aspects would exceed 100, the first 100 will be returned. full Default value. Returns all required aspects, as well as the keys of all non-required aspects. |


**Examples:**
```bash
To lookup a Dataplex entry entry1 within entry group entry-group1 in
location us-central1, run:

    $ gcloud dataplex entries lookup entry1 --entry-group=entry-group1 \
        --location=us-central1 --project=test-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/entries/lookup)

---
### `gcloud dataplex entries remove-aspects`

Remove aspects from a Dataplex Entry

Remove aspects from a Dataplex Entry.

**Synopsis:**
```
gcloud dataplex entries remove-aspects
    (ENTRY : --entry-group=ENTRY_GROUP --location=LOCATION)
    --keys=[ASPECT_TYPE@PATH,...] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Entry resource - Arguments and flags that define the Dataplex Entry you
want to reference. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument entry on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENTRY
     ID of the entry or fully qualified identifier for the entry.

     To set the entry attribute:
     + provide the argument entry on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --entry-group=ENTRY_GROUP
     Entry group containing Dataplex Entries.

     To set the entry-group attribute:
     + provide the argument entry on the command line with a fully
       specified name;
     + provide the argument --entry-group on the command line.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument entry on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--keys` | [ASPECT_TYPE@PATH,...] |  | List of Aspect keys, identifying Aspects to remove from the entry. Keys are in the format ASPECT_TYPE@PATH, or just ASPECT_TYPE, if the Aspect is attached to an entry itself rather than to a specific column defined in the schema. ASPECT_TYPE is expected to be in a format PROJECT_ID.LOCATION.ASPECT_TYPE_ID or a wildcard *, which targets all aspect types. PATH can be either empty (which means a 'root' path, such that Aspect is attached to the entry itself), point to a specific column defined in the schema (for example: Schema.some_column) or a wildcard * (target all paths). ASPECT_TYPE and PATH cannot be both specified as wildcards *. |


**Examples:**
```bash
To remove all aspects of type test-project.us-central1.some-aspect-type
from the entry, run:

    $ gcloud dataplex entries remove-aspects entry1 \
        --project=test-project --location=us-central1 \
        --entry-group entry-group1 \
        --keys='test-project.us-central1.some-aspect-type@*'

To remove all aspects on path Schema.column1 from the entry, run:

    $ gcloud dataplex entries remove-aspects entry1 \
        --project=test-project --location=us-central1 \
        --entry-group entry-group1 --keys='*@Schema.column1'

To remove exact aspects
test-project.us-central1.some-aspect-type@Schema.column1 and
test-project.us-central1.some-aspect-type2@Schema.column2 from the entry,
run:

    $ gcloud dataplex entries remove-aspects entry1 \
        --project=test-project --location=us-central1 \
        --entry-group entry-group1 \
        --keys=test-project.us-central1.some-aspect-type@Schema.column1,\
    test-project.us-central2.some-aspect-type@Schema.column2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/entries/remove-aspects)

---
### `gcloud dataplex entries search`

Searches for Dataplex entries

Searches for entries matching given query and scope.

**Synopsis:**
```
gcloud dataplex entries search QUERY --project=PROJECT [--limit=LIMIT]
    [--order-by=ORDER_BY] [--page-size=PAGE_SIZE] [--scope=SCOPE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
QUERY
   The query against which entries in scope should be matched.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--project` | PROJECT |  | The project to which the request should be attributed. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--limit` | LIMIT |  | Maximum number of resources. |
| `--order-by` | ORDER_BY |  | Specifies the ordering of results, currently supported case-sensitive choices are: * title [asc\|desc], defaults to ascending if not specified. |
| `--page-size` | PAGE_SIZE |  | Maximum number of resources per page. No more than 500. |
| `--scope` | SCOPE |  | The scope under which the search should be operating. Should either be organizations/<org_id> or projects/<project_ref>. If left unspecified, it will default to the organization where the project is located. |


**Examples:**
```bash
To search project 'my-project' for Dataplex resources that match the simple
predicate 'foo':

    $ gcloud dataplex entries search 'foo' --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/entries/search)

---
### `gcloud dataplex entries update`

Update a Dataplex Entry

Update specified fields in a given Dataplex Entry.

**Synopsis:**
```
gcloud dataplex entries update
    (ENTRY : --entry-group=ENTRY_GROUP --location=LOCATION)
    [--remove-aspects=[ASPECT_TYPE@PATH,...]]
    [--update-aspects=YAML_OR_JSON_FILE]
    [--clear-fully-qualified-name
      | --fully-qualified-name=FULLY_QUALIFIED_NAME]
    [--entry-source-update-time=DATE_TIME
      : --clear-entry-source-create-time
      | --entry-source-create-time=DATE_TIME
      --clear-entry-source-description
      | --entry-source-description=DESCRIPTION
      --clear-entry-source-display-name
      | --entry-source-display-name=DISPLAY_NAME
      --clear-entry-source-labels
      | --entry-source-labels=[KEY=VALUE,...] --clear-entry-source-platform
      | --entry-source-platform=PLATFORM_NAME --clear-entry-source-resource
      | --entry-source-resource=RESOURCE --clear-entry-source-system
      | --entry-source-system=SYSTEM_NAME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Entry resource - Arguments and flags that define the Dataplex Entry you
want to reference. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument entry on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENTRY
     ID of the entry or fully qualified identifier for the entry.

     To set the entry attribute:
     + provide the argument entry on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --entry-group=ENTRY_GROUP
     Entry group containing Dataplex Entries.

     To set the entry-group attribute:
     + provide the argument entry on the command line with a fully
       specified name;
     + provide the argument --entry-group on the command line.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument entry on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--remove-aspects` | [ASPECT_TYPE@PATH,...] |  | List of Aspect keys, identifying Aspects to remove from the entry. Keys are in the format ASPECT_TYPE@PATH, or just ASPECT_TYPE, if the Aspect is attached to an entry itself rather than to a specific column defined in the schema. ASPECT_TYPE is expected to be in a format PROJECT_ID.LOCATION.ASPECT_TYPE_ID or a wildcard *, which targets all aspect types. PATH can be either empty (which means a 'root' path, such that Aspect is attached to the entry itself), point to a specific column defined in the schema (for example: Schema.some_column) or a wildcard * (target all paths). ASPECT_TYPE and PATH cannot be both specified as wildcards *. If both --update-aspects and --remove-aspects flags are specified, and the same aspect key is used in both flags, then --update-aspects takes precedence, and such an aspect will be updated and not removed. |
| `--update-aspects` | YAML_OR_JSON_FILE |  | Path to a YAML or JSON file containing Aspects to add or update. When this flag is specified, only Aspects referenced in the file are going to be added or updated. Specifying this flag does not remove any Aspects from the entry. In other words, specifying this flag will not lead to a full replacement of Aspects with a contents of the provided file. Content of the file contains a map, where keys are in the format ASPECT_TYPE@PATH, or just ASPECT_TYPE, if the Aspect is attached to an entry itself rather than to a specific column defined in the schema. Values in the map represent Aspect's content, which must conform to a template defined for a given ASPECT_TYPE. Each Aspect will be replaced fully by the provided content. That means data in the Aspect will be replaced and not merged with existing contents of that Aspect in the Entry. ASPECT_TYPE is expected to be in a format PROJECT_ID.LOCATION.ASPECT_TYPE_ID. PATH can be either empty (which means a 'root' path, such that Aspect is attached to the entry itself) or point to a specific column defined in the schema. For example: Schema.some_column. Example YAML format: project-id1.us-central1.my-aspect-type1: data: aspectField1: someValue aspectField2: someOtherValue project-id2.us-central1.my-aspect-type2@Schema.column1: data: aspectField3: someValue3 Example JSON format: { "project-id1.us-central1.my-aspect-type1": { "data": { "aspectField1": "someValue", "aspectField2": "someOtherValue" } }, "project-id2.us-central1.my-aspect-type2@Schema.column1": { "data": { "aspectField3": "someValue3" } } } If both --update-aspects and --remove-aspects flags are specified, and the same aspect key is used in both flags, then --update-aspects takes precedence, and such an aspect will be updated and not removed. |


**Examples:**
```bash
To update fully qualified name (FQN) of an entry, run:

    $ gcloud dataplex entries update entry1 --project=test-project \
        --location=us-central1 --entry-group entry-group1 \
        --fully-qualified-name='custom:a.b.c'

To update description of an entry, run:

    $ gcloud dataplex entries update entry1 --project=test-project \
        --location=us-central1 --entry-group entry-group1 \
        --entry-source-description='Updated description' \
        --entry-source-update-time='1998-09-04T12:00:00-0700'

To clear the description of an entry, run:

    $ gcloud dataplex entries update entry1 --project=test-project \
        --location=us-central1 --entry-group entry-group1 \
        --clear-entry-source-description \
        --entry-source-update-time='1998-09-04T12:00:00-0700'

To add or update aspects from the YAML/JSON file, run:

    $ gcloud dataplex entries update entry1 --project=test-project \
        --location=us-central1 --entry-group entry-group1 \
        --update-aspects=path-to-a-file-with-aspects.json

To remove all aspects of type test-project.us-central1.some-aspect-type
from the entry, run:

    $ gcloud dataplex entries update entry1 --project=test-project \
        --location=us-central1 --entry-group entry-group1 \
        --remove-aspects='test-project.us-central1.some-aspect-type@*'

To remove all aspects on path Schema.column1 from the entry, run:

    $ gcloud dataplex entries update entry1 --project=test-project \
        --location=us-central1 --entry-group entry-group1 \
        --remove-aspects='*@Schema.column1'

To remove exact aspects
test-project.us-central1.some-aspect-type@Schema.column1 and
test-project.us-central1.some-aspect-type2@Schema.column2 from the entry,
run:

    $ gcloud dataplex entries update entry1 --project=test-project \
        --location=us-central1 --entry-group entry-group1 \
        --remove-aspects=test-project.us-central1.some-aspect-type@Schem\
    a.column1,test-project.us-central2.some-aspect-type@Schema.column2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/entries/update)

---
### `gcloud dataplex entries update-aspects`

Add or update aspects for a Dataplex Entry

Add or update aspects for a Dataplex Entry.

**Synopsis:**
```
gcloud dataplex entries update-aspects
    (ENTRY : --entry-group=ENTRY_GROUP --location=LOCATION)
    --aspects=YAML_OR_JSON_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Entry resource - Arguments and flags that define the Dataplex Entry you
want to reference. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument entry on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENTRY
     ID of the entry or fully qualified identifier for the entry.

     To set the entry attribute:
     + provide the argument entry on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --entry-group=ENTRY_GROUP
     Entry group containing Dataplex Entries.

     To set the entry-group attribute:
     + provide the argument entry on the command line with a fully
       specified name;
     + provide the argument --entry-group on the command line.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument entry on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--aspects` | YAML_OR_JSON_FILE |  | Path to a YAML or JSON file containing Aspects to add or update. When this flag is specified, only Aspects referenced in the file are going to be added or updated. Specifying this flag does not remove any Aspects from the entry. In other words, specifying this flag will not lead to a full replacement of Aspects with a contents of the provided file. Content of the file contains a map, where keys are in the format ASPECT_TYPE@PATH, or just ASPECT_TYPE, if the Aspect is attached to an entry itself rather than to a specific column defined in the schema. Values in the map represent Aspect's content, which must conform to a template defined for a given ASPECT_TYPE. Each Aspect will be replaced fully by the provided content. That means data in the Aspect will be replaced and not merged with existing contents of that Aspect in the Entry. ASPECT_TYPE is expected to be in a format PROJECT_ID.LOCATION.ASPECT_TYPE_ID. PATH can be either empty (which means a 'root' path, such that Aspect is attached to the entry itself) or point to a specific column defined in the schema. For example: Schema.some_column. Example YAML format: project-id1.us-central1.my-aspect-type1: data: aspectField1: someValue aspectField2: someOtherValue project-id2.us-central1.my-aspect-type2@Schema.column1: data: aspectField3: someValue3 Example JSON format: { "project-id1.us-central1.my-aspect-type1": { "data": { "aspectField1": "someValue", "aspectField2": "someOtherValue" } }, "project-id2.us-central1.my-aspect-type2@Schema.column1": { "data": { "aspectField3": "someValue3" } } } |


**Examples:**
```bash
To add or update aspects for the Dataplex entry entry1 within the entry
group entry-group1 in location us-central1 from the YAML/JSON file, run:

    $ gcloud dataplex entries update-aspects entry1 \
        --project=test-project --location=us-central1 \
        --entry-group entry-group1 \
        --aspects=path-to-a-file-with-aspects.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/entries/update-aspects)

---
# gcloud data-catalog tags

manage tags in Data Catalog

### `gcloud data-catalog tags create`

Create a Data Catalog entry tag

(DEPRECATED) This command is deprecated. Please use gcloud dataplex entries
instead. Note that aspects - successors of tags - are part of the entry
resource and are managed by gcloud dataplex entries command.

Create a Data Catalog entry tag.

**Synopsis:**
```
gcloud data-catalog tags create --tag-file=TAG_FILE
    (--entry=ENTRY : --entry-group=ENTRY_GROUP --location=LOCATION)
    (--tag-template=TAG_TEMPLATE
      : --tag-template-location=TAG_TEMPLATE_LOCATION
      --tag-template-project=TAG_TEMPLATE_PROJECT) [--scope=SCOPE]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--tag-file` | TAG_FILE |  | Path to a JSON or YAML file containing the tag. The file should contain a JSON/YAML object with a key and value for each field that should be set. See $ gcloud topic datetimes for information on how to specify timestamp fields. For example: { "dbl_field": 123, "str_field": "String", "bool_field": true, "ts_field": "1970-01-01T00:00:00.000Z", "enum_field": "ENUM_A", } |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--scope` | SCOPE |  | Scope within the parent resource that the tag is attached to. Scopes allow users to attach tags to individual columns based on the parent resource's schema. To attach a tag to a nested column, use '.' to separate the column names: 'outer_column.inner_column'. |


**Examples:**
```bash
Create a Data Catalog entry tag:

    $ gcloud data-catalog tags create --entry=ENTRY \
        --tag-template=TAG_TEMPLATE --tag-file=TAG_FILE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/tags/create)

---
### `gcloud data-catalog tags delete`

Delete a Data Catalog entry tag

(DEPRECATED) This command is deprecated. Please use gcloud dataplex entries
instead. Note that aspects - successors of tags - are part of the entry
resource and are managed by gcloud dataplex entries command.

Delete a Data Catalog entry tag.

**Synopsis:**
```
gcloud data-catalog tags delete
    (TAG : --entry=ENTRY --entry-group=ENTRY_GROUP --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tag resource - Entry tag to delete. The arguments in this group can be
used to specify the attributes of this resource. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument tag on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TAG
     ID of the tag or fully qualified identifier for the tag.

     To set the tag attribute:
     + provide the argument tag on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --entry=ENTRY
     Entry of the tag.

     To set the entry attribute:
     + provide the argument tag on the command line with a fully
       specified name;
     + provide the argument --entry on the command line.

  --entry-group=ENTRY_GROUP
     Entry group of the tag.

     To set the entry-group attribute:
     + provide the argument tag on the command line with a fully
       specified name;
     + provide the argument --entry-group on the command line.

  --location=LOCATION
     Location of the tag.

     To set the location attribute:
     + provide the argument tag on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
Delete a Data Catalog entry tag:

    $ gcloud data-catalog tags delete TAG
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/tags/delete)

---
### `gcloud data-catalog tags list`

List Data Catalog entry tags

(DEPRECATED) This command is deprecated. Please use gcloud dataplex entries
instead. Note that aspects - successors of tags - are part of the entry
resource and are managed by gcloud dataplex entries command.

List Data Catalog entry tags.

**Synopsis:**
```
gcloud data-catalog tags list
    (--entry=ENTRY : --entry-group=ENTRY_GROUP --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--entry` | ENTRY |  | _[This must be specified.]_ ID of the entry or fully qualified identifier for the entry. To set the entry attribute: + provide the argument --entry on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--entry-group` | ENTRY_GROUP |  | _[This must be specified.]_ Entry group of the entry. To set the entry-group attribute: + provide the argument --entry on the command line with a fully specified name; + provide the argument --entry-group on the command line. |
| `--location` | LOCATION |  | _[This must be specified.]_ Location of the entry. To set the location attribute: + provide the argument --entry on the command line with a fully specified name; + provide the argument --location on the command line. |


**Examples:**
```bash
List the tags for a Data Catalog entry:

    $ gcloud data-catalog tags list --entry=ENTRY
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/tags/list)

---
### `gcloud data-catalog tags update`

Update a Data Catalog entry tag

(DEPRECATED) This command is deprecated. Please use gcloud dataplex entries
instead. Note that aspects - successors of tags - are part of the entry
resource and are managed by gcloud dataplex entries command.

Update a Data Catalog entry tag. This will overwrite the current values of
the tag.

**Synopsis:**
```
gcloud data-catalog tags update
    (TAG : --entry=ENTRY --entry-group=ENTRY_GROUP --location=LOCATION)
    --tag-file=TAG_FILE
    (--tag-template=TAG_TEMPLATE
      : --tag-template-location=TAG_TEMPLATE_LOCATION
      --tag-template-project=TAG_TEMPLATE_PROJECT) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tag resource - Entry tag to update. The arguments in this group can be
used to specify the attributes of this resource. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument tag on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TAG
     ID of the tag or fully qualified identifier for the tag.

     To set the tag attribute:
     + provide the argument tag on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --entry=ENTRY
     Entry of the tag.

     To set the entry attribute:
     + provide the argument tag on the command line with a fully
       specified name;
     + provide the argument --entry on the command line.

  --entry-group=ENTRY_GROUP
     Entry group of the tag.

     To set the entry-group attribute:
     + provide the argument tag on the command line with a fully
       specified name;
     + provide the argument --entry-group on the command line.

  --location=LOCATION
     Location of the tag.

     To set the location attribute:
     + provide the argument tag on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--tag-file` | TAG_FILE |  | Path to a JSON or YAML file containing the tag. The file should contain a JSON/YAML object with a key and value for each field that should be set. See $ gcloud topic datetimes for information on how to specify timestamp fields For example: { "dbl_field": 123, "str_field": "String", "bool_field": true, "ts_field": "1970-01-01T00:00:00.000Z", "enum_field": "ENUM_A", } |


**Examples:**
```bash
Update a Data Catalog entry tag:

    $ gcloud data-catalog tags update TAG --tag-template=TAG_TEMPLATE \
        --tag-file=TAG_FILE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/tags/update)

---
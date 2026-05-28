# gcloud pubsub schemas

manage Pub/Sub schemas

### `gcloud pubsub schemas commit`

Commit a Pub/Sub schema revision

Commit a Pub/Sub schema revision.

**Synopsis:**
```
gcloud pubsub schemas commit SCHEMA --type=TYPE
    (--definition=DEFINITION | --definition-file=PATH_TO_FILE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Schema resource - Name of the schema to revise. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument schema on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SCHEMA
     ID of the schema or fully qualified identifier for the schema.

     To set the schema attribute:
     + provide the argument schema on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--type` | TYPE |  | The type of the schema. |


**Examples:**
```bash
To commit a PROTOCOL_BUFFER schema revision called "key-schema" that
requires exactly one-string field named "key", run:

    $ gcloud pubsub schemas commit key-schema \
        --definition="syntax = 'proto3'; message Message { optional \
    string key = 1; }" --type=protocol-buffer To commit an equivalent \
        AVRO schema revision, run:

    $ gcloud pubsub schemas commit key-schema \
        --definition="{ 'type': 'record', 'namespace': 'my.ns', 'name': \
    'KeyMsg', 'fields': [ { 'name': 'key', 'type': 'string' } ] }" \
        --type=avro
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/schemas/commit)

---
### `gcloud pubsub schemas create`

Create a Pub/Sub schema

Create a new Pub/Sub schema.

**Synopsis:**
```
gcloud pubsub schemas create SCHEMA --type=TYPE
    (--definition=DEFINITION | --definition-file=PATH_TO_FILE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Schema resource - Pub/Sub schema to create. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument schema on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SCHEMA
     ID of the schema or fully qualified identifier for the schema.

     To set the schema attribute:
     + provide the argument schema on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--type` | one of: avro, protocol-buffer |  | Type of the schema. TYPE must be one of: avro, protocol-buffer. |


**Examples:**
```bash
To create a PROTOCOL_BUFFER schema called "key-schema" that requires
exactly one string field named "key", run:        $ gcloud pubsub schemas create key-schema \
        --definition="syntax = 'proto3'; message Message { optional \
    string key = 1; }" --type=PROTOCOL_BUFFER

To create an equivalent AVRO schema, run:        $ gcloud pubsub schemas create key-schema \
        --definition='{ "type": "record", "namespace": "my.ns", "name":
     "KeyMsg", "fields": [ { "name": "key", "type": "string" } ] }' \
        --type=AVRO
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/schemas/create)

---
### `gcloud pubsub schemas delete`

Delete a Pub/Sub schema

Delete a Pub/Sub schema.

**Synopsis:**
```
gcloud pubsub schemas delete SCHEMA [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Schema resource - Pub/Sub schema to delete. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument schema on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SCHEMA
     ID of the schema or fully qualified identifier for the schema.

     To set the schema attribute:
     + provide the argument schema on the command line.
```

**Examples:**
```bash
To delete a schema called my-schema, run:

    $ gcloud pubsub schemas delete my-schema
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/schemas/delete)

---
### `gcloud pubsub schemas delete-revision`

Delete a Pub/Sub schema revision

Delete a Pub/Sub schema revision.

**Synopsis:**
```
gcloud pubsub schemas delete-revision SCHEMA [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Schema resource - Name of the schema revision to delete. This represents a
Cloud resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument schema on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SCHEMA
     ID of the schema or fully qualified identifier for the schema.

     To set the schema attribute:
     + provide the argument schema on the command line.
```

**Examples:**
```bash
To roll back to an existing schema revision called "key-schema" with
revision_id: "0a0b0c0d", run:

    $ gcloud pubsub schemas delete-revision key-schema@0a0b0c0d
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/schemas/delete-revision)

---
### `gcloud pubsub schemas describe`

Show details of a Pub/Sub schema

Show details of a Pub/Sub schema.

**Synopsis:**
```
gcloud pubsub schemas describe SCHEMA [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Schema resource - The schema you want to describe. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument schema on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SCHEMA
     ID of the schema or fully qualified identifier for the schema.

     To set the schema attribute:
     + provide the argument schema on the command line.
```

**Examples:**
```bash
To show details about a schema named my-schema, run:

    $ gcloud pubsub schemas describe my-schema
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/schemas/describe)

---
### `gcloud pubsub schemas list`

List Pub/Sub schemas

List Pub/Sub schemas.

**Synopsis:**
```
gcloud pubsub schemas list [--view=VIEW; default="basic"]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--view` | one of: basic Include the name and type of the schema, but not the definition | basic | There are two possible views, 'basic' and 'full', default is 'basic'. VIEW must be one of: basic Include the name and type of the schema, but not the definition. full Include all Schema object fields. |


**Examples:**
```bash
To list the schemas, run:

    $ gcloud pubsub schemas list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/schemas/list)

---
### `gcloud pubsub schemas list-revisions`

List revisions of a Pub/Sub schema

List revisions of a Pub/Sub schema.

**Synopsis:**
```
gcloud pubsub schemas list-revisions SCHEMA [--view=VIEW; default="basic"]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Schema resource - Parent Pub/Sub schema to list all contained revisions.
This represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument schema on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SCHEMA
     ID of the schema or fully qualified identifier for the schema.

     To set the schema attribute:
     + provide the argument schema on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--view` | one of: basic Include the name and type of the schema, but not the definition | basic | There are two possible views, 'basic' and 'full', default is 'basic'. VIEW must be one of: basic Include the name and type of the schema, but not the definition. full Include all Schema object fields. |


**Examples:**
```bash
To list the revisions for a schema, run:

    $ gcloud pubsub schemas list-revisions my-schema
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/schemas/list-revisions)

---
### `gcloud pubsub schemas rollback`

Roll back a Pub/Sub schema to a specified revision

Roll back a Pub/Sub schema to a specified revision.

**Synopsis:**
```
gcloud pubsub schemas rollback SCHEMA --revision-id=REVISION_ID
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Schema resource - Name of the schema to rollback. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument schema on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SCHEMA
     ID of the schema or fully qualified identifier for the schema.

     To set the schema attribute:
     + provide the argument schema on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--revision-id` | REVISION_ID |  | The revision to roll back to. |


**Examples:**
```bash
To roll back to an existing schema revision called "key-schema" with
revision_id: "0a0b0c0d", run:

    $ gcloud pubsub schemas rollback key-schema --revision-id=0a0b0c0d
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/schemas/rollback)

---
### `gcloud pubsub schemas validate-message`

Validate a message against a Pub/Sub schema

Validate a message against a Pub/Sub schema.

**Synopsis:**
```
gcloud pubsub schemas validate-message --message=MESSAGE
    --message-encoding=MESSAGE_ENCODING
    (--schema-name=SCHEMA_NAME | --type=TYPE (--definition=DEFINITION
      | --definition-file=PATH_TO_FILE)) [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--message` | MESSAGE |  | The message to validate against the schema. |
| `--message-encoding` | one of: binary, json |  | The encoding of the message. MESSAGE_ENCODING must be one of: binary, json. |


**Examples:**
```bash
To validate message against provided PROTOCOL_BUFFER schema, run:

    $ gcloud pubsub schemas validate-message --message="{\"key\": \
        \"my-key\"}" --message-encoding=JSON --definition="syntax = \
        'proto3'; message Message { optional string key = 1; \
        }" --type=PROTOCOL_BUFFER

To validate an equivalent AVRO schema, run:

    $ gcloud pubsub schemas validate-message \
        --definition='{ "type": "record", "namespace": "my.ns", "name":
     "KeyMsg", "fields": [ { "name": "key", "type": "string" } ] }' \
        --type=AVRO
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/schemas/validate-message)

---
### `gcloud pubsub schemas validate-schema`

Validate a Pub/Sub schema

Validate a new Pub/Sub schema.

**Synopsis:**
```
gcloud pubsub schemas validate-schema --type=TYPE
    (--definition=DEFINITION | --definition-file=PATH_TO_FILE)
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--type` | one of: avro, protocol-buffer |  | Type of the schema. TYPE must be one of: avro, protocol-buffer. |


**Examples:**
```bash
To validate a PROTOCOL_BUFFER schema, run:

    $ gcloud pubsub schemas validate-schema \
        --definition="syntax = 'proto3'; message Message { optional \
    string key = 1; }" --type=PROTOCOL_BUFFER

To validate an equivalent AVRO schema, run:

    $ gcloud pubsub schemas validate-schema \
        --definition='{ "type": "record", "namespace": "my.ns", "name":
     "KeyMsg", "fields": [ { "name": "key", "type": "string" } ] }' \
        --type=AVRO
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/schemas/validate-schema)

---
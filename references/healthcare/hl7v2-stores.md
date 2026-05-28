# gcloud healthcare hl7v2-stores

manage Cloud Healthcare API HL7v2 stores

### `gcloud healthcare hl7v2-stores add-iam-policy-binding`

Add an IAM policy binding to a Cloud Healthcare API HL7v2 store

Add an IAM policy binding to a Cloud Healthcare API HL7v2 store.

**Synopsis:**
```
gcloud healthcare hl7v2-stores add-iam-policy-binding
    (HL7V2_STORE : --dataset=DATASET --location=LOCATION)
    --member=PRINCIPAL --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Hl7v2Store resource - Cloud Healthcare API HL7v2 store to add an IAM
policy binding to. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument hl7v2_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HL7V2_STORE
     ID of the hl7v2Store or fully qualified identifier for the
     hl7v2Store.

     To set the hl7v2_store attribute:
     + provide the argument hl7v2_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument hl7v2_store on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument hl7v2_store on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--condition` | [KEY=VALUE,...] |  | _[At most one of these can be specified:]_ A condition to include in the binding. When the condition is explicitly specified as None (--condition=None), a binding without a condition is added. When the condition is specified and is not None, --role cannot be a basic role. Basic roles are roles/editor, roles/owner, and roles/viewer. For more on conditions, refer to the conditions overview guide: https://cloud.google.com/iam/docs/conditions-overview When using the --condition flag, include the following key-value pairs: expression (Required) Condition expression that evaluates to True or False. This uses a subset of Common Expression Language syntax. If the condition expression includes a comma, use a different delimiter to separate the key-value pairs. Specify the delimiter before listing the key-value pairs. For example, to specify a colon (:) as the delimiter, do the following: --condition=^:^title=TITLE:expression=EXPRESSION. For more information, see https://cloud.google.com/sdk/gcloud/reference/topic/escaping. title (Required) A short string describing the purpose of the expression. description (Optional) Additional description for the expression. |
| `--condition-from-file` | PATH_TO_FILE |  | _[At most one of these can be specified:]_ Path to a local JSON or YAML file that defines the condition. To see available fields, see the help for --condition. Use a full or relative path to a local file containing the value of condition. |


**Examples:**
```bash
To add an IAM policy binding for the role of 'roles/editor' for the user
'test-user@gmail.com' on the HL7v2 store 'test-hl7v2-store', run:

    $ gcloud healthcare hl7v2-stores add-iam-policy-binding \
        test-hl7v2-store --dataset=test-dataset \
        --member='user:test-user@gmail.com' --role='roles/editor'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/hl7v2-stores/add-iam-policy-binding)

---
### `gcloud healthcare hl7v2-stores create`

Create a Cloud Healthcare API HL7v2 store

Create a Cloud Healthcare API HL7v2 store.

**Synopsis:**
```
gcloud healthcare hl7v2-stores create
    (HL7V2_STORE : --dataset=DATASET --location=LOCATION)
    [--notification-config=[filter=FILTER],[pubsub-topic=PUBSUB-TOPIC]]
    [--parser-version=PARSER_VERSION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Hl7v2Store resource - Cloud Healthcare API HL7v2 store to create. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument hl7v2_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HL7V2_STORE
     ID of the hl7v2Store or fully qualified identifier for the
     hl7v2Store.

     To set the hl7v2_store attribute:
     + provide the argument hl7v2_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument hl7v2_store on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument hl7v2_store on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--notification-config` | [filter=FILTER],[pubsub-topic=PUBSUB-TOPIC] |  | A list of notification configs. Each configuration uses a filter to determine whether to publish a message (both Ingest & Create) on the corresponding notification destination. Only the message name is sent as part of the notification. Supplied by the client. See https://cloud.google.com/appengine/docs/standard/python/search/query_strings for the syntax of the filter. Note: A topic must be created before publishing or subscribing to it. For instructions on creating topics, refer to: https://cloud.google.com/pubsub/docs/admin#create_a_topic |
| `--parser-version` | one of: v1 The parsedData includes every given non-empty message field except the Field Separator (MSH-1) field |  | Immutable. Determines the version of both the default parser to be used when schema (https://cloud.google.com/healthcare-api/docs/reference/rest/v1/projects.locations.datasets.hl7V2Stores#ParserConfig.FIELDS.schema) is not given, as well as the schematized parser used when schema (https://cloud.google.com/healthcare-api/docs/reference/rest/v1/projects.locations.datasets.hl7V2Stores#ParserConfig.FIELDS.schema) is specified. This field is immutable after HL7v2 store creation. PARSER_VERSION must be one of: v1 The parsedData includes every given non-empty message field except the Field Separator (MSH-1) field. As a result, the parsed MSH segment starts with the MSH-2 field and the field numbers are off-by-one with respect to the HL7 standard. v2 The parsedData includes every given non-empty message field. v3 This version is the same as V2, with the following change. The parsedData contains unescaped escaped field separators, component separators, sub-component separators, repetition separators, escape characters, and truncation characters. If schema (https://cloud.google.com/healthcare-api/docs/reference/rest/v1/projects.locations.datasets.hl7V2Stores#ParserConfig.FIELDS.schema) is specified, the schematized parser uses improved parsing heuristics compared to previous versions. |


**Examples:**
```bash
To create a HL7v2 store called test-hl7v2-store, run:

    $ gcloud healthcare hl7v2-stores create test-hl7v2-store \
        --dataset=test-dataset

To create a HL7v2 store with two Cloud Pub/Sub topics test-pubsub-topic1
and test-pubsub-topic2 with corresponding filters, run:

    $ gcloud healthcare hl7v2-stores create test-hl7v2-store \
        --dataset=test-dataset \
        --notification-config=pubsub-topic=projects/my-project/topics/\
    test-pubsub-topic1,filter="labels.priority=high" \
        --notification-config=pubsub-topic=projects/my-project/topics/\
    test-pubsub-topic2,filter=PatientId("123456", "MRN")
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/hl7v2-stores/create)

---
### `gcloud healthcare hl7v2-stores delete`

Delete a Cloud Healthcare API HL7v2 store

Delete a Cloud Healthcare API HL7v2 store.

**Synopsis:**
```
gcloud healthcare hl7v2-stores delete
    (HL7V2_STORE : --dataset=DATASET --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Hl7v2Store resource - Cloud Healthcare API HL7v2 store to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument hl7v2_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HL7V2_STORE
     ID of the hl7v2Store or fully qualified identifier for the
     hl7v2Store.

     To set the hl7v2_store attribute:
     + provide the argument hl7v2_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument hl7v2_store on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument hl7v2_store on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Examples:**
```bash
To delete the HL7v2 store 'test-hl7v2-store', run:

    $ gcloud healthcare hl7v2-stores delete test-hl7v2-store \
        --dataset=test-dataset
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/hl7v2-stores/delete)

---
### `gcloud healthcare hl7v2-stores describe`

Describe a Cloud Healthcare API HL7v2 store

Describe a Cloud Healthcare API HL7v2 store.

**Synopsis:**
```
gcloud healthcare hl7v2-stores describe
    (HL7V2_STORE : --dataset=DATASET --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Hl7v2Store resource - Cloud Healthcare API HL7v2 store to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument hl7v2_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HL7V2_STORE
     ID of the hl7v2Store or fully qualified identifier for the
     hl7v2Store.

     To set the hl7v2_store attribute:
     + provide the argument hl7v2_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument hl7v2_store on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument hl7v2_store on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Examples:**
```bash
To describe the HL7v2 store 'test-hl7v2-store', run:

    $ gcloud healthcare hl7v2-stores describe test-hl7v2-store \
        --dataset=test-dataset
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/hl7v2-stores/describe)

---
### `gcloud healthcare hl7v2-stores get-iam-policy`

Retrieve the IAM policy for a Cloud Healthcare API HL7v2 store

Retrieve the IAM policy for a Cloud Healthcare API HL7v2 store.

**Synopsis:**
```
gcloud healthcare hl7v2-stores get-iam-policy
    (HL7V2_STORE : --dataset=DATASET --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Hl7v2Store resource - Cloud Healthcare API HL7v2 store whose IAM policy to
fetch. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument hl7v2_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HL7V2_STORE
     ID of the hl7v2Store or fully qualified identifier for the
     hl7v2Store.

     To set the hl7v2_store attribute:
     + provide the argument hl7v2_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument hl7v2_store on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument hl7v2_store on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Examples:**
```bash
To print the IAM policy for the HL7v2 store 'test-hl7v2-store', run:

    $ gcloud healthcare hl7v2-stores get-iam-policy test-hl7v2-store \
        --dataset=test-dataset
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/hl7v2-stores/get-iam-policy)

---
### `gcloud healthcare hl7v2-stores list`

List Cloud Healthcare API HL7v2 stores

List Cloud Healthcare API HL7v2 stores.

**Synopsis:**
```
gcloud healthcare hl7v2-stores list
    (--dataset=DATASET : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--dataset` | DATASET |  | _[This must be specified.]_ ID of the dataset or fully qualified identifier for the dataset. To set the dataset attribute: + provide the argument --dataset on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Google Cloud location. To set the location attribute: + provide the argument --dataset on the command line with a fully specified name; + provide the argument --location on the command line; + set the property healthcare/location. |


**Examples:**
```bash
To list the HL7v2 stores in 'test-dataset', run:

    $ gcloud healthcare hl7v2-stores list --dataset=test-dataset
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/hl7v2-stores/list)

---
### `gcloud healthcare hl7v2-stores metrics`

Gets the metrics for a Cloud Healthcare API HL7v2 store

Gets the metrics for a Cloud Healthcare API HL7v2 store.

**Synopsis:**
```
gcloud healthcare hl7v2-stores metrics
    (HL7V2_STORE : --dataset=DATASET --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Hl7v2Store resource - Cloud Healthcare API HL7v2 store to get metrics for.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument hl7v2_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HL7V2_STORE
     ID of the hl7v2Store or fully qualified identifier for the
     hl7v2Store.

     To set the hl7v2_store attribute:
     + provide the argument hl7v2_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument hl7v2_store on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument hl7v2_store on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Examples:**
```bash
To get metrics for the HL7v2 store 'test-hl7v2-store', run:

    $ gcloud healthcare hl7v2-stores metrics test-hl7v2-store \
        --dataset=test-dataset
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/hl7v2-stores/metrics)

---
### `gcloud healthcare hl7v2-stores remove-iam-policy-binding`

Remove an IAM policy binding from a Cloud Healthcare API HL7v2 store

Remove an IAM policy binding from a Cloud Healthcare API HL7v2 store.

**Synopsis:**
```
gcloud healthcare hl7v2-stores remove-iam-policy-binding
    (HL7V2_STORE : --dataset=DATASET --location=LOCATION)
    --member=PRINCIPAL --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Hl7v2Store resource - Cloud Healthcare API HL7v2 store to remove an IAM
policy binding from. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument hl7v2_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HL7V2_STORE
     ID of the hl7v2Store or fully qualified identifier for the
     hl7v2Store.

     To set the hl7v2_store attribute:
     + provide the argument hl7v2_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument hl7v2_store on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument hl7v2_store on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--all` |  |  | _[At most one of these can be specified:]_ Remove all bindings with this role and principal, irrespective of any conditions. |
| `--condition` | [KEY=VALUE,...] |  | _[At most one of these can be specified:]_ The condition of the binding that you want to remove. When the condition is explicitly specified as None (--condition=None), a binding without a condition is removed. Otherwise, only a binding with a condition that exactly matches the specified condition (including the optional description) is removed. For more on conditions, refer to the conditions overview guide: https://cloud.google.com/iam/docs/conditions-overview When using the --condition flag, include the following key-value pairs: expression (Required) Condition expression that evaluates to True or False. This uses a subset of Common Expression Language syntax. If the condition expression includes a comma, use a different delimiter to separate the key-value pairs. Specify the delimiter before listing the key-value pairs. For example, to specify a colon (:) as the delimiter, do the following: --condition=^:^title=TITLE:expression=EXPRESSION. For more information, see https://cloud.google.com/sdk/gcloud/reference/topic/escaping. title (Required) A short string describing the purpose of the expression. description (Optional) Additional description for the expression. |
| `--condition-from-file` | PATH_TO_FILE |  | _[At most one of these can be specified:]_ Path to a local JSON or YAML file that defines the condition. To see available fields, see the help for --condition. Use a full or relative path to a local file containing the value of condition. |


**Examples:**
```bash
To remove an IAM policy binding for the role of 'roles/editor' for the user
'test-user@gmail.com' on the HL7v2 store 'test-hl7v2-store', run:

    $ gcloud healthcare hl7v2-stores remove-iam-policy-binding \
        test-hl7v2-store --dataset=test-dataset \
        --member='user:test-user@gmail.com' --role='roles/editor'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/hl7v2-stores/remove-iam-policy-binding)

---
### `gcloud healthcare hl7v2-stores set-iam-policy`

Set the IAM policy for a Cloud Healthcare API HL7v2 store

Set the IAM policy for a Cloud Healthcare API HL7v2 store.

**Synopsis:**
```
gcloud healthcare hl7v2-stores set-iam-policy
    (HL7V2_STORE : --dataset=DATASET --location=LOCATION) POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Hl7v2Store resource - Cloud Healthcare API HL7v2 store whose IAM policy to
set. The arguments in this group can be used to specify the attributes of
this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument hl7v2_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HL7V2_STORE
     ID of the hl7v2Store or fully qualified identifier for the
     hl7v2Store.

     To set the hl7v2_store attribute:
     + provide the argument hl7v2_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument hl7v2_store on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument hl7v2_store on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command will read am IAM policy defined in a JSON file
'policy.json' and set it for the HL7v2 store 'test-hl7v2-store':

    $ gcloud healthcare hl7v2-stores set-iam-policy test-hl7v2-store \
        policy.json --dataset=test-dataset

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/hl7v2-stores/set-iam-policy)

---
### `gcloud healthcare hl7v2-stores update`

Update a Cloud Healthcare API HL7v2 store

Update a Cloud Healthcare API HL7v2 store.

**Synopsis:**
```
gcloud healthcare hl7v2-stores update
    (HL7V2_STORE : --dataset=DATASET --location=LOCATION)
    [--notification-config=[filter=FILTER],[pubsub-topic=PUBSUB-TOPIC]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Hl7v2Store resource - Cloud Healthcare API HL7v2 store to update. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument hl7v2_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HL7V2_STORE
     ID of the hl7v2Store or fully qualified identifier for the
     hl7v2Store.

     To set the hl7v2_store attribute:
     + provide the argument hl7v2_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument hl7v2_store on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument hl7v2_store on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--notification-config` | [filter=FILTER],[pubsub-topic=PUBSUB-TOPIC] |  | A list of notification configs. Each configuration uses a filter to determine whether to publish a message (both Ingest & Create) on the corresponding notification destination. Only the message name is sent as part of the notification. Supplied by the client. See https://cloud.google.com/appengine/docs/standard/python/search/query_strings for the syntax of the filter. Note: A topic must be created before publishing or subscribing to it. For instructions on creating topics, refer to: https://cloud.google.com/pubsub/docs/admin#create_a_topic |


**Examples:**
```bash
To update the Cloud Pub/Sub topics on a HL7v2 store test-hl7v2-store, run:

    $ gcloud healthcare hl7v2-stores update test-hl7v2-store \
        --notification-config=pubsub-topic=projects/my-project/topics/\
    test-pubsub-topic1,filter="labels.priority=high" \
        --notification-config=pubsub-topic=projects/my-project/topics/\
    test-pubsub-topic2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/hl7v2-stores/update)

---

## `gcloud healthcare hl7v2-stores export` — manage Cloud Healthcare API HL7v2 store exports
### `gcloud healthcare hl7v2-stores export gcs`

Export Cloud Healthcare API HL7v2 messages to Google Cloud Storage

Export Cloud Healthcare API HL7v2 messages to Google Cloud Storage.

**Synopsis:**
```
gcloud healthcare hl7v2-stores export gcs
    (HL7V2_STORE : --dataset=DATASET --location=LOCATION) --gcs-uri=GCS_URI
    [--async] [--end-time=END_TIME] [--message-view=MESSAGE_VIEW]
    [--start-time=START_TIME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Hl7v2Store resource - Cloud Healthcare API HL7v2 store to export messages
from. The arguments in this group can be used to specify the attributes of
this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument hl7v2_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HL7V2_STORE
     ID of the hl7v2Store or fully qualified identifier for the
     hl7v2Store.

     To set the hl7v2_store attribute:
     + provide the argument hl7v2_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument hl7v2_store on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument hl7v2_store on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--gcs-uri` | GCS_URI |  | The Cloud Storage destination location. Specify a path to a Cloud Storage bucket or folder rather than a concrete object. The exported messages are ordered by the message send_time (MSH.7) in ascending order. The server will create one or more objects. Each object contains newline delimited JSON, and each line is an HL7v2 message. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--end-time` | END_TIME |  | The end of the range in message send_time (MSH.7) to process. If not specified, the time when the export is scheduled is used. |
| `--message-view` | one of: basic Exported resources include only the name field |  | Specifies the parts of the Message resource to include in the export. The default is FULL. MESSAGE_VIEW must be one of: basic Exported resources include only the name field. full Exported resources include all the message fields. parsed-only Exported resources include all the message fields except data and schematizedData fields. raw-only Exported resources include all the message fields except parsedData and schematizedData fields. schematized-only Exported resources include all the message fields except data and parsedData fields. |
| `--start-time` | START_TIME |  | The start of the range in message send_time (MSH.7) to process. If not specified, the UNIX epoch (1970-01-01T00:00:00Z) is used. |


**Examples:**
```bash
To export the hl7v2-store 'test-hl7v2-store' to the existing bucket
'testGcsBucket' in the folder 'someFolder', run:

    $ gcloud healthcare hl7v2-stores export gcs test-hl7v2-store \
        --gcs-uri=gs://testGcsBucket/someFolder --dataset=test-dataset

To perform the same export, but exporting messages with the message view of
'RAW_ONLY', run:

    $ gcloud healthcare hl7v2-stores export gcs test-hl7v2-store \
        --gcs-uri=gs://testGcsBucket/someFolder --dataset=test-dataset \
        --message-view=RAW_ONLY
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/hl7v2-stores/export/gcs)

---

## `gcloud healthcare hl7v2-stores import` — manage Cloud Healthcare API HL7v2 store imports
### `gcloud healthcare hl7v2-stores import gcs`

Import HL7v2 messages from Google Cloud Storage into a Cloud Healthcare API HL7v2 store

Import HL7v2 messages from Google Cloud Storage into a Cloud Healthcare API
HL7v2 store.

**Synopsis:**
```
gcloud healthcare hl7v2-stores import gcs
    (HL7V2_STORE : --dataset=DATASET --location=LOCATION) --gcs-uri=GCS_URI
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Hl7v2Store resource - Cloud Healthcare API HL7v2 store into which the data
is imported. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument hl7v2_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HL7V2_STORE
     ID of the hl7v2Store or fully qualified identifier for the
     hl7v2Store.

     To set the hl7v2_store attribute:
     + provide the argument hl7v2_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument hl7v2_store on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument hl7v2_store on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--gcs-uri` | GCS_URI |  | Cloud Storage source data locations. Each Cloud Storage object should be a text file that contains newline-delimited JSON objects. Each JSON object has a data field that contains a base64-encoded HL7v2 message. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To import the HL7v2 messages from the existing bucket 'testGcsBucket' in
the folder 'someFolder' into the HL7v2 store 'test-hl7v2-store', run:

    $ gcloud healthcare hl7v2-stores import gcs test-hl7v2-store \
        --gcs-uri=gs://testGcsBucket/someFolder --dataset=test-dataset
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/hl7v2-stores/import/gcs)

---
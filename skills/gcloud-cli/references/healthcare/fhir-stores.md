# gcloud healthcare fhir-stores

manage Cloud Healthcare API FHIR stores

### `gcloud healthcare fhir-stores add-iam-policy-binding`

Add an IAM policy binding to a Cloud Healthcare API FHIR store

Adds an IAM policy binding to a Cloud Healthcare API FHIR store.

**Synopsis:**
```
gcloud healthcare fhir-stores add-iam-policy-binding
    (FHIR_STORE : --dataset=DATASET --location=LOCATION) --member=PRINCIPAL
    --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FhirStore resource - Cloud Healthcare API FHIR store to add an IAM policy
binding to. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument fhir_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FHIR_STORE
     ID of the fhirStore or fully qualified identifier for the fhirStore.

     To set the fhir_store attribute:
     + provide the argument fhir_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument fhir_store on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument fhir_store on the command line with a fully
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
'test-user@gmail.com' on the fhir store 'test-fhir-store', run:

    $ gcloud healthcare fhir-stores add-iam-policy-binding \
        test-fhir-store --dataset=test-dataset \
        --member='user:test-user@gmail.com' --role='roles/editor'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/fhir-stores/add-iam-policy-binding)

---
### `gcloud healthcare fhir-stores create`

Create a Cloud Healthcare API FHIR store

Creates a Cloud Healthcare API FHIR store.

**Synopsis:**
```
gcloud healthcare fhir-stores create
    (FHIR_STORE : --dataset=DATASET --location=LOCATION) --version=VERSION
    [--disable-referential-integrity] [--disable-resource-versioning]
    [--enable-update-create] [--pubsub-topic=PUBSUB_TOPIC]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FhirStore resource - Cloud Healthcare API FHIR store to create. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument fhir_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FHIR_STORE
     ID of the fhirStore or fully qualified identifier for the fhirStore.

     To set the fhir_store attribute:
     + provide the argument fhir_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument fhir_store on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument fhir_store on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--version` | VERSION |  | The FHIR specification version that this FHIR store supports natively. This field is immutable after store creation. Requests are rejected if they contain FHIR resources of a different version. An empty value is treated as STU3. VERSION must be one of: dstu2 Draft Standard for Trial Use, Release 2 (https://www.hl7.org/fhir/DSTU2) r4 Release 4 (https://www.hl7.org/fhir/R4) stu3 Standard for Trial Use, Release 3 (https://www.hl7.org/fhir/STU3) |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--disable-referential-integrity` |  |  | Whether to disable referential integrity in this FHIR store. Default value is false, meaning that the API will enforce referential integrity and fail the requests that will result in inconsistent state in the FHIR store. When this field is set to true, the API will skip referential integrity check. This field is immutable after store creation. |
| `--disable-resource-versioning` |  |  | Whether to disable resource versioning for this FHIR store. If set to false, which is the default behavior, all write operations will cause historical versions to be recorded automatically. Historical versions can be fetched through the history APIs, but cannot be updated. This field is immutable after store creation. |
| `--enable-update-create` |  |  | Whether this FHIR store has the [updateCreate] (https://www.hl7.org/fhir/capabilitystatement-definitions.html#CapabilityStatement.rest.resource.updateCreate) capability. Determines if the client can use an Update operation to create a new resource with a client-specified ID. If false, all IDs are server-assigned through the Create operation and attempts to Update a non-existent resource will return errors. |
| `--pubsub-topic` | PUBSUB_TOPIC |  | Google Cloud Pub/Sub topic to send updates to. Note, a topic needs to be created before publishing or subscribing to it. For instructions on creating topics, refer to: https://cloud.google.com/pubsub/docs/admin#create_a_topic |


**Examples:**
```bash
To create a FHIR store called 'test-fhir-store', run:

    $ gcloud healthcare fhir-stores create test-fhir-store \
        --dataset=test-dataset --version=r4

To create a fhir store with the Cloud Pub/Sub topic 'test-pubsub-topic',
run:

    $ gcloud healthcare fhir-stores create test-fhir-store \
        --dataset=test-dataset --version=r4 \
        --pubsub-topic=projects/my-project/topics/test-pubsub-topic
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/fhir-stores/create)

---
### `gcloud healthcare fhir-stores deidentify`

De-identify data from the source store and write it to the destination store

De-identify data from the source store and write it to the destination
store.

**Synopsis:**
```
gcloud healthcare fhir-stores deidentify
    (FHIR_STORE : --dataset=DATASET --location=LOCATION)
    --destination-store=DESTINATION_STORE [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FhirStore resource - Source Cloud Healthcare API FHIR store to deidentify.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument fhir_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FHIR_STORE
     ID of the fhirStore or fully qualified identifier for the fhirStore.

     To set the fhir_store attribute:
     + provide the argument fhir_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument fhir_store on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument fhir_store on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination-store` | DESTINATION_STORE |  | The name of the FHIR store to which the redacted data should be written (e.g., projects/{projectId}/locations/{locationId}/datasets/{datasetId}/fhirStores/{fhirStoreId}). The destination FHIR store must already exist, or the request will fail. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To generate a de-identified version of the FHIR store 'test-fhir-store',
run the command below.

    $ gcloud healthcare fhir-stores deidentify test-fhir-store \
        --destination-store=projects/{projectId}/locations/us-central1/\
    datasets/{datasetId}/fhirStores/test-deid-fhir-store
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/fhir-stores/deidentify)

---
### `gcloud healthcare fhir-stores delete`

Delete a Cloud Healthcare API FHIR store

Delete a Cloud Healthcare API FHIR store.

**Synopsis:**
```
gcloud healthcare fhir-stores delete
    (FHIR_STORE : --dataset=DATASET --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FhirStore resource - Cloud Healthcare API FHIR store to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument fhir_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FHIR_STORE
     ID of the fhirStore or fully qualified identifier for the fhirStore.

     To set the fhir_store attribute:
     + provide the argument fhir_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument fhir_store on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument fhir_store on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Examples:**
```bash
To delete the FHIR store 'test-fhir-store', run:

    $ gcloud healthcare fhir-stores delete test-fhir-store \
        --dataset=test-dataset
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/fhir-stores/delete)

---
### `gcloud healthcare fhir-stores describe`

Describe a Cloud Healthcare API FHIR store

Describe a Cloud Healthcare API FHIR store.

**Synopsis:**
```
gcloud healthcare fhir-stores describe
    (FHIR_STORE : --dataset=DATASET --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FhirStore resource - Cloud Healthcare API FHIR store to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument fhir_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FHIR_STORE
     ID of the fhirStore or fully qualified identifier for the fhirStore.

     To set the fhir_store attribute:
     + provide the argument fhir_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument fhir_store on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument fhir_store on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Examples:**
```bash
To describe the FHIR store 'test-fhir-store', run:

    $ gcloud healthcare fhir-stores describe test-fhir-store \
        --dataset=test-dataset
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/fhir-stores/describe)

---
### `gcloud healthcare fhir-stores get-iam-policy`

Retrieve the IAM policy for a Cloud Healthcare API FHIR store

Retrieve the IAM policy for a Cloud Healthcare API FHIR store.

**Synopsis:**
```
gcloud healthcare fhir-stores get-iam-policy
    (FHIR_STORE : --dataset=DATASET --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FhirStore resource - Cloud Healthcare API FHIR store whose IAM policy to
fetch. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument fhir_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FHIR_STORE
     ID of the fhirStore or fully qualified identifier for the fhirStore.

     To set the fhir_store attribute:
     + provide the argument fhir_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument fhir_store on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument fhir_store on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Examples:**
```bash
To print the IAM policy for the fhir store 'test-fhir-store', run:

    $ gcloud healthcare fhir-stores get-iam-policy test-fhir-store \
        --dataset=test-dataset
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/fhir-stores/get-iam-policy)

---
### `gcloud healthcare fhir-stores list`

List Cloud Healthcare API FHIR stores

List Cloud Healthcare API FHIR stores.

**Synopsis:**
```
gcloud healthcare fhir-stores list
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
To list the FHIR stores in 'test-dataset', run:

    $ gcloud healthcare fhir-stores list --dataset=test-dataset
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/fhir-stores/list)

---
### `gcloud healthcare fhir-stores metrics`

Gets the metrics for a Cloud Healthcare API FHIR store

Gets the metrics for a Cloud Healthcare API FHIR store.

**Synopsis:**
```
gcloud healthcare fhir-stores metrics
    (FHIR_STORE : --dataset=DATASET --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FhirStore resource - Cloud Healthcare API FHIR store to get metrics for.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument fhir_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FHIR_STORE
     ID of the fhirStore or fully qualified identifier for the fhirStore.

     To set the fhir_store attribute:
     + provide the argument fhir_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument fhir_store on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument fhir_store on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Examples:**
```bash
To get metrics for the FHIR store 'test-fhir-store', run:

    $ gcloud healthcare fhir-stores metrics test-fhir-store \
        --dataset=test-dataset
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/fhir-stores/metrics)

---
### `gcloud healthcare fhir-stores remove-iam-policy-binding`

Remove an IAM policy binding from a Cloud Healthcare API FHIR store

Removes an IAM policy binding from a Cloud Healthcare API FHIR store.

**Synopsis:**
```
gcloud healthcare fhir-stores remove-iam-policy-binding
    (FHIR_STORE : --dataset=DATASET --location=LOCATION) --member=PRINCIPAL
    --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FhirStore resource - Cloud Healthcare API FHIR store to remove an IAM
policy binding from. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument fhir_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FHIR_STORE
     ID of the fhirStore or fully qualified identifier for the fhirStore.

     To set the fhir_store attribute:
     + provide the argument fhir_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument fhir_store on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument fhir_store on the command line with a fully
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
'test-user@gmail.com' on the fhir store 'test-fhir-store', run:

    $ gcloud healthcare fhir-stores remove-iam-policy-binding \
        test-fhir-store --dataset=test-dataset \
        --member='user:test-user@gmail.com' --role='roles/editor'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/fhir-stores/remove-iam-policy-binding)

---
### `gcloud healthcare fhir-stores set-iam-policy`

Set the IAM policy for a Cloud Healthcare API FHIR store

Set the IAM policy for a Cloud Healthcare API FHIR store.

**Synopsis:**
```
gcloud healthcare fhir-stores set-iam-policy
    (FHIR_STORE : --dataset=DATASET --location=LOCATION) POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FhirStore resource - Cloud Healthcare API FHIR store whose IAM policy to
set. The arguments in this group can be used to specify the attributes of
this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument fhir_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FHIR_STORE
     ID of the fhirStore or fully qualified identifier for the fhirStore.

     To set the fhir_store attribute:
     + provide the argument fhir_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument fhir_store on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument fhir_store on the command line with a fully
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
'policy.json' and set it for the fhir store 'test-fhir-store':

    $ gcloud healthcare fhir-stores set-iam-policy test-fhir-store \
        policy.json --dataset=test-dataset

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/fhir-stores/set-iam-policy)

---
### `gcloud healthcare fhir-stores update`

Update a Cloud Healthcare API FHIR store

Update a Cloud Healthcare API FHIR store.

**Synopsis:**
```
gcloud healthcare fhir-stores update
    (FHIR_STORE : --dataset=DATASET --location=LOCATION)
    [--enable-update-create] [--pubsub-topic=PUBSUB_TOPIC]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FhirStore resource - The Cloud Healthcare API FHIR store you want to
update. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument fhir_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FHIR_STORE
     ID of the fhirStore or fully qualified identifier for the fhirStore.

     To set the fhir_store attribute:
     + provide the argument fhir_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument fhir_store on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument fhir_store on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--enable-update-create` |  |  | Whether this FHIR store has the [updateCreate] (https://www.hl7.org/fhir/capabilitystatement-definitions.html#CapabilityStatement.rest.resource.updateCreate) capability. Determines if the client can use an Update operation to create a new resource with a client-specified ID. If false, all IDs are server-assigned through the Create operation and attempts to Update a non-existent resource will return errors. |
| `--pubsub-topic` | PUBSUB_TOPIC |  | Google Cloud Pub/Sub topic to send updates to. Note, a topic needs to be created before publishing or subscribing to it. For instructions on creating topics, refer to: https://cloud.google.com/pubsub/docs/admin#create_a_topic |


**Examples:**
```bash
To update the Cloud Pub/Sub topic on a FHIR store 'test-fhir-store', run:

    $ gcloud healthcare fhir-stores update test-fhir-store \
        --pubsub-topic=projects/my-project/topics/test-pubsub-topic
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/fhir-stores/update)

---

## `gcloud healthcare fhir-stores export` — manage Cloud Healthcare API FHIR store exports
### `gcloud healthcare fhir-stores export bq`

Export Cloud Healthcare API FHIR resources to BigQuery

Export Cloud Healthcare API FHIR resources to BigQuery.

**Synopsis:**
```
gcloud healthcare fhir-stores export bq
    (FHIR_STORE : --dataset=DATASET --location=LOCATION)
    --bq-dataset=BQ_DATASET --schema-type=SCHEMA_TYPE [--async]
    [--recursive-depth=RECURSIVE_DEPTH] [--resource-type=RESOURCE_TYPE]
    [--since=SINCE] [--write-disposition=WRITE_DISPOSITION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FhirStore resource - Cloud Healthcare API FHIR store to export resources
from. The arguments in this group can be used to specify the attributes of
this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument fhir_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FHIR_STORE
     ID of the fhirStore or fully qualified identifier for the fhirStore.

     To set the fhir_store attribute:
     + provide the argument fhir_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument fhir_store on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument fhir_store on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--bq-dataset` | BQ_DATASET |  | BigQuery dataset that houses the BigQuery tables. |
| `--schema-type` | one of: analytics Analytics schema defined by the FHIR community |  | Specifies the output schema type. SCHEMA_TYPE must be one of: analytics Analytics schema defined by the FHIR community. See https://github.com/rbrush/sql-on-fhir/blob/master/sql-on-fhir.md. analytics_v2 Analytics V2, similar to Analytics schema type, with added support for extensions with one or more occurrences and contained resources to be represented in stringified JSON. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--recursive-depth` | RECURSIVE_DEPTH |  | The depth for all recursive structures in the output analytics schema. For example, concept in the CodeSystem resource is a recursive structure; when the depth is 2, the CodeSystem table will have a column called concept.concept but not concept.concept.concept. If not specified or set to 0, the server will use the default value 2. |
| `--resource-type` | RESOURCE_TYPE |  | String of comma-delimited FHIR resource types. If provided, only resources of the specified resource type(s) are exported. |
| `--since` | SINCE |  | If provided, only resources updated after this time are exported. The time uses the format YYYY-MM-DDThh:mm:ss.sss+zz:zz. For example, 2015-02-07T13:28:17.239+02:00 or 2017-01-01T00:00:00Z. The time must be specified to the second and include a time zone. |
| `--write-disposition` | one of: write-append Append data to the existing tables |  | Determines whether existing tables in the destination dataset are overwritten or appended to. WRITE_DISPOSITION must be one of: write-append Append data to the existing tables. write-empty Only export data if the destination tables are empty. write-truncate Erase all existing data in the tables before writing the instances. |


**Examples:**
```bash
To export the fhir-store 'test-fhir-store' to the BigQuery dataset
'bqdataset', run:

    $ gcloud healthcare fhir-stores export bq test-fhir-store \
        --bq-dataset=bq://my-project.bqdataset --dataset=test-dataset

To perform the same export, but with the 'ANALYTICS' schema and the
recursive structure depth of 3, run:

    $ gcloud healthcare fhir-stores export bq test-fhir-store \
        --bq-dataset=bq://my-project.bqdataset --dataset=test-dataset \
        --schema-type=analytics --recursive-depth=3
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/fhir-stores/export/bq)

---
### `gcloud healthcare fhir-stores export gcs`

Export Cloud Healthcare API FHIR resources to Google Cloud Storage

Export Cloud Healthcare API FHIR resources to Google Cloud Storage.

**Synopsis:**
```
gcloud healthcare fhir-stores export gcs
    (FHIR_STORE : --dataset=DATASET --location=LOCATION) --gcs-uri=GCS_URI
    [--async] [--resource-type=RESOURCE_TYPE] [--since=SINCE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FhirStore resource - Cloud Healthcare API FHIR store to export resources
from. The arguments in this group can be used to specify the attributes of
this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument fhir_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FHIR_STORE
     ID of the fhirStore or fully qualified identifier for the fhirStore.

     To set the fhir_store attribute:
     + provide the argument fhir_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument fhir_store on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument fhir_store on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--gcs-uri` | GCS_URI |  | The Cloud Storage destination location. Specify a path to a Cloud Storage bucket or folder rather than a concrete object. The exported outputs are organized by FHIR resource types. The server will create one object per resource type. Each object contains newline delimited JSON, and each line is a FHIR resource. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--resource-type` | RESOURCE_TYPE |  | String of comma-delimited FHIR resource types. If provided, only resources of the specified resource type(s) are exported. |
| `--since` | SINCE |  | If provided, only resources updated after this time are exported. The time uses the format YYYY-MM-DDThh:mm:ss.sss+zz:zz. For example, 2015-02-07T13:28:17.239+02:00 or 2017-01-01T00:00:00Z. The time must be specified to the second and include a time zone. |


**Examples:**
```bash
To export the fhir-store 'test-fhir-store' to the existing bucket
'testGcsBucket' in the folder 'someFolder', run:

    $ gcloud healthcare fhir-stores export gcs test-fhir-store \
        --gcs-uri=gs://testGcsBucket/someFolder --dataset=test-dataset
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/fhir-stores/export/gcs)

---

## `gcloud healthcare fhir-stores import` — manage Cloud Healthcare API FHIR store imports
### `gcloud healthcare fhir-stores import gcs`

Import FHIR resources from Google Cloud Storage into a Cloud Healthcare API FHIR store

Import FHIR resources from Google Cloud Storage into a Cloud Healthcare API
FHIR store.

**Synopsis:**
```
gcloud healthcare fhir-stores import gcs
    (FHIR_STORE : --dataset=DATASET --location=LOCATION) --gcs-uri=GCS_URI
    [--async] [--content-structure=CONTENT_STRUCTURE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FhirStore resource - Cloud Healthcare API FHIR store into which the data
is imported. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument fhir_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FHIR_STORE
     ID of the fhirStore or fully qualified identifier for the fhirStore.

     To set the fhir_store attribute:
     + provide the argument fhir_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument fhir_store on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument fhir_store on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--gcs-uri` | GCS_URI |  | Cloud Storage source data locations. Each Cloud Storage object should be a text file that contains newline-delimited JSON structures conforming to the FHIR standard. You can use wildcards to import multiple files from one or more directories. * Use * to match 0 or more non-separator characters. For example, gs://BUCKET/DIRECTORY/Example*.ndjson matches Example.ndjson and Example22.ndjson in DIRECTORY. * Use ** to match 0 or more characters (including separators). Must be used at the end of a path and with no other wildcards in the path. Can also be used with a filename extension (such as .ndjson), which imports all files with the filename extension in the specified directory and its subdirectories. For example, gs://BUCKET/DIRECTORY/**.ndjson imports all files with the .ndjson filename extension in DIRECTORY and its subdirectories. * Use ? to match 1 character. For example, gs://BUCKET/DIRECTORY/Example?.ndjson matches Example1.ndjson but does not match Example.ndjson or Example01.ndjson. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--content-structure` | one of: bundle Each unit is a bundle, which contains one or more resources |  | Content structure in the source location. The default is BUNDLE. CONTENT_STRUCTURE must be one of: bundle Each unit is a bundle, which contains one or more resources. bundle-pretty The entire file is one JSON bundle. The JSON can span multiple lines. resource Each unit is a single resource. resource-pretty The entire file is one JSON resource. The JSON can span multiple lines. |


**Examples:**
```bash
To import the FHIR resources from the existing bucket 'testGcsBucket' in
the folder 'someFolder' into the FHIR store 'test-fhir-store', run:

    $ gcloud healthcare fhir-stores import gcs test-fhir-store \
        --gcs-uri=gs://testGcsBucket/someFolder/* --dataset=test-dataset

To perform the same import, but importing resources with the content
structure of 'RESOURCE', run:

    $ gcloud healthcare fhir-stores import gcs test-fhir-store \
        --gcs-uri=gs://testGcsBucket/someFolder/* \
        --dataset=test-dataset --content-structure=RESOURCE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/fhir-stores/import/gcs)

---
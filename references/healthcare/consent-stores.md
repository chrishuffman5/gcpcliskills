# gcloud healthcare consent-stores

manage Cloud Healthcare API consent stores

### `gcloud healthcare consent-stores add-iam-policy-binding`

Add an IAM policy binding to a Cloud Healthcare API consent store

Add an IAM policy binding to a Cloud Healthcare API consent store.

**Synopsis:**
```
gcloud healthcare consent-stores add-iam-policy-binding
    (CONSENT_STORE : --dataset=DATASET --location=LOCATION)
    --member=PRINCIPAL --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ConsentStore resource - Cloud Healthcare API consent store to add an IAM
policy binding to. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument consent_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONSENT_STORE
     ID of the consentStore or fully qualified identifier for the
     consentStore.

     To set the consent_store attribute:
     + provide the argument consent_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument consent_store on the command line with a
       fully specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument consent_store on the command line with a
       fully specified name;
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
'test-user@gmail.com' on the consent store 'test-consent-store', run:

    $ gcloud healthcare consent-stores add-iam-policy-binding \
        test-consent-store --dataset=test-dataset \
        --member='user:test-user@gmail.com' --role='roles/editor'

To add an IAM policy binding for the role of
'roles/healthcare.consentEditor' for the user 'test-user@gmail.com' on the
consent store 'test-consent-store', and have it expire at the end of the
year 2020, run:

    $ gcloud healthcare consent-stores add-iam-policy-binding \
        test-consent-store --dataset=test-dataset \
        --member='user:test-user@gmail.com' \
        --role='roles/healthcare.consentEditor' \
        --condition='expression=request.time <
     timestamp("2021-01-01T00:00:00Z"),title=expires_end_of_2020,descrip\
    tion=Expires at midnight on 2020-12-31'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/consent-stores/add-iam-policy-binding)

---
### `gcloud healthcare consent-stores check-data-access`

Check the consent for a particular data ID

Check if a particular data ID of a user data mapping in the given Cloud
Healthcare API consent store is consented for a given use.

**Synopsis:**
```
gcloud healthcare consent-stores check-data-access
    (CONSENT_STORE : --dataset=DATASET --location=LOCATION)
    --data-id=DATA_ID [--request-attributes=[KEY=VALUE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ConsentStore resource - Cloud Healthcare API consent store where the
requested data-id is stored. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument consent_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONSENT_STORE
     ID of the consentStore or fully qualified identifier for the
     consentStore.

     To set the consent_store attribute:
     + provide the argument consent_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument consent_store on the command line with a
       fully specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument consent_store on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--data-id` | DATA_ID |  | The unique identifier of the data to check access for. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--request-attributes` | [KEY=VALUE,...] |  | Comma-separated list of request attributes associated with this access request. Each attribute has the form "KEY=VALUE". |


**Examples:**
```bash
To check if the data ID 'test-data-id' in the consent-store
'test-consent-store' can be used given request attributes
{"organization":"admins", "use_case":"research"}, run:

    $ gcloud healthcare consent-stores check-data-access \
        test-consent-store --data-id=test-data-id \
        --request-attributes=organization=admins,use_case=research \
        --dataset=test-dataset
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/consent-stores/check-data-access)

---
### `gcloud healthcare consent-stores create`

Create a Cloud Healthcare API consent store

Create a Cloud Healthcare API consent store.

**Synopsis:**
```
gcloud healthcare consent-stores create
    (CONSENT_STORE : --dataset=DATASET --location=LOCATION)
    [--labels=[KEY=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ConsentStore resource - Cloud Healthcare API consent store to create. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument consent_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONSENT_STORE
     ID of the consentStore or fully qualified identifier for the
     consentStore.

     To set the consent_store attribute:
     + provide the argument consent_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument consent_store on the command line with a
       fully specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument consent_store on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To create an consent store called 'test-consent-store' with labels
{"key1":"value1", "key2":"value2"}, run:

    $ gcloud healthcare consent-stores create test-consent-store \
        --labels=key1=value1,key2=value2 --dataset=test-dataset
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/consent-stores/create)

---
### `gcloud healthcare consent-stores delete`

Delete a Cloud Healthcare API consent store

Delete a Cloud Healthcare API consent store.

**Synopsis:**
```
gcloud healthcare consent-stores delete
    (CONSENT_STORE : --dataset=DATASET --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ConsentStore resource - Cloud Healthcare API consent store to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument consent_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONSENT_STORE
     ID of the consentStore or fully qualified identifier for the
     consentStore.

     To set the consent_store attribute:
     + provide the argument consent_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument consent_store on the command line with a
       fully specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument consent_store on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Examples:**
```bash
To delete the consent-store 'test-consent-store', run:

    $ gcloud healthcare consent-stores delete test-consent-store \
        --dataset=test-dataset
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/consent-stores/delete)

---
### `gcloud healthcare consent-stores describe`

Describe a Cloud Healthcare API consent store

Describe a Cloud Healthcare API consent store.

**Synopsis:**
```
gcloud healthcare consent-stores describe
    (CONSENT_STORE : --dataset=DATASET --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ConsentStore resource - Cloud Healthcare API consent store to describe.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument consent_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONSENT_STORE
     ID of the consentStore or fully qualified identifier for the
     consentStore.

     To set the consent_store attribute:
     + provide the argument consent_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument consent_store on the command line with a
       fully specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument consent_store on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Examples:**
```bash
To describe the consent-store 'test-consent-store', run:

    $ gcloud healthcare consent-stores describe test-consent-store \
        --dataset=test-dataset
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/consent-stores/describe)

---
### `gcloud healthcare consent-stores evaluate-user-consents`

Check the consents for a particular user's data

Check if each matching user data mapping in the given Cloud Healthcare API
consent store is consented for a given use.

**Synopsis:**
```
gcloud healthcare consent-stores evaluate-user-consents
    (CONSENT_STORE : --dataset=DATASET --location=LOCATION)
    --user-id=USER_ID [--consent-list=[CONSENT_LIST,...]]
    [--page-size=PAGE_SIZE] [--page-token=PAGE_TOKEN]
    [--request-attributes=[KEY=VALUE,...]]
    [--resource-attributes=[KEY=VALUE,...]] [--response-view=RESPONSE_VIEW]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ConsentStore resource - Cloud Healthcare API consent store where the
requested data is stored. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument consent_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONSENT_STORE
     ID of the consentStore or fully qualified identifier for the
     consentStore.

     To set the consent_store attribute:
     + provide the argument consent_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument consent_store on the command line with a
       fully specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument consent_store on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--user-id` | USER_ID |  | The unique identifier of the user to evaluate consents for. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--consent-list` | [CONSENT_LIST,...] |  | List of user consents to evaluate the access request against. They must have the same user_id as the data to check access for, exist in the current consent_store, and have a state of either ACTIVE or DRAFT. A maximum of 100 consents can be provided here. |
| `--page-size` | PAGE_SIZE |  | Limit on the number of user data mappings to return in a single response. If zero the default page size of 100 is used. |
| `--page-token` | PAGE_TOKEN |  | Token to retrieve the next page of results. |
| `--request-attributes` | [KEY=VALUE,...] |  | Comma-separated list of request attributes associated with this access request. Each attribute has the form "KEY=VALUE". |
| `--resource-attributes` | [KEY=VALUE,...] |  | Comma-separated list of resource attributes associated with this access request. Each attribute has the form "KEY=VALUE". If no values are specified, then all data types are queried. |
| `--response-view` | one of: basic, full, response-view-unspecified |  | The requested view of information provided in the response (BASIC or FULL). RESPONSE_VIEW must be one of: basic, full, response-view-unspecified. |


**Examples:**
```bash
To check if the data for user 'test-user-id' in the consent-store
'test-consent-store' can be used given request attributes
{"organization":"admins", "use_case":"research"}, run:

    $ gcloud healthcare consent-stores evaluate-user-consents \
        test-consent-store --user-id=test-user-id \
        --request-attributes=organization=admins,use_case=research \
        --dataset=test-dataset
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/consent-stores/evaluate-user-consents)

---
### `gcloud healthcare consent-stores get-iam-policy`

Retrieve the IAM policy for a Cloud Healthcare API consent store

Retrieve the IAM policy for a Cloud Healthcare API consent store.

**Synopsis:**
```
gcloud healthcare consent-stores get-iam-policy
    (CONSENT_STORE : --dataset=DATASET --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ConsentStore resource - Cloud Healthcare API consent store whose IAM
policy to fetch. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument consent_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONSENT_STORE
     ID of the consentStore or fully qualified identifier for the
     consentStore.

     To set the consent_store attribute:
     + provide the argument consent_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument consent_store on the command line with a
       fully specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument consent_store on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Examples:**
```bash
To print the IAM policy for the consent store 'test-consent-store', run:

    $ gcloud healthcare consent-stores get-iam-policy \
        test-consent-store --dataset=test-dataset
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/consent-stores/get-iam-policy)

---
### `gcloud healthcare consent-stores list`

List Cloud Healthcare API consent stores

List Cloud Healthcare API consent stores.

**Synopsis:**
```
gcloud healthcare consent-stores list
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
To list the consent stores in 'test-dataset' with a filter 'key1=value1' on
labels, run:

    $ gcloud healthcare consent-stores list \
        --filter="labels.key1=value1" --dataset=test-dataset
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/consent-stores/list)

---
### `gcloud healthcare consent-stores query-accessible-data`

Queries all accessible data IDs

Queries all data IDs that are consented for a given use in the given Cloud
Healthcare API consent store and writes them to a specified destination.

**Synopsis:**
```
gcloud healthcare consent-stores query-accessible-data
    (CONSENT_STORE : --dataset=DATASET --location=LOCATION)
    --gcs-uri=GCS_URI [--async] [--request-attributes=[KEY=VALUE,...]]
    [--resource-attributes=[KEY=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ConsentStore resource - Cloud Healthcare API consent store to retrieve
user data mappings from. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument consent_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONSENT_STORE
     ID of the consentStore or fully qualified identifier for the
     consentStore.

     To set the consent_store attribute:
     + provide the argument consent_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument consent_store on the command line with a
       fully specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument consent_store on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--gcs-uri` | GCS_URI |  | The Cloud Storage destination for the result file. The Cloud Healthcare API service account must have the roles/storage.objectAdmin Cloud IAM role for this Cloud Storage location. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--request-attributes` | [KEY=VALUE,...] |  | Comma-separated list of request attributes associated with this access request. Each attribute has the form "KEY=VALUE". |
| `--resource-attributes` | [KEY=VALUE,...] |  | Comma-separated list of resources attributes associated with the type of data being requested. Each attribute has the form "KEY=VALUE". If no values are specified, then all data types are included in the output. |


**Examples:**
```bash
To query all data IDs in the consent-store 'test-consent-store' that can be
used given request attributes {"organization":"admins",
"use_case":"research"} and resource attributes {"anonymity":"identified"},
and write the result file to "gs://test-bucket/folder", run:

    $ gcloud healthcare consent-stores query-accessible-data \
        test-consent-store --gcs-uri=gs://test-bucket/folder \
        --request-attributes=organization=admins,use_case=research \
        --resource-attributes=anonymity=identified \
        --dataset=test-dataset
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/consent-stores/query-accessible-data)

---
### `gcloud healthcare consent-stores remove-iam-policy-binding`

Remove an IAM policy binding from a Cloud Healthcare API consent store

Remove an IAM policy binding from a Cloud Healthcare API consent store.

**Synopsis:**
```
gcloud healthcare consent-stores remove-iam-policy-binding
    (CONSENT_STORE : --dataset=DATASET --location=LOCATION)
    --member=PRINCIPAL --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ConsentStore resource - Cloud Healthcare API consent store to remove an
IAM policy binding from. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument consent_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONSENT_STORE
     ID of the consentStore or fully qualified identifier for the
     consentStore.

     To set the consent_store attribute:
     + provide the argument consent_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument consent_store on the command line with a
       fully specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument consent_store on the command line with a
       fully specified name;
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
'test-user@gmail.com' on the consent store 'test-consent-store', run:

    $ gcloud healthcare consent-stores remove-iam-policy-binding \
        test-consent-store --dataset=test-dataset \
        --member='user:test-user@gmail.com' --role='roles/editor'

To remove an IAM policy binding for the role of
'roles/healthcare.consentEditor' for the user 'test-user@gmail.com' on the
consent store 'test-consent-store' and matches a specific condition, run:

    $ gcloud healthcare consent-stores remove-iam-policy-binding \
        test-consent-store --dataset=test-dataset \
        --member='user:test-user@gmail.com' \
        --role='roles/healthcare.consentEditor' \
        --condition='expression=request.time <
     timestamp("2021-01-01T00:00:00Z"),title=expires_end_of_2020,descrip\
    tion=Expires at midnight on 2020-12-31'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/consent-stores/remove-iam-policy-binding)

---
### `gcloud healthcare consent-stores set-iam-policy`

Set the IAM policy for a Cloud Healthcare API consent store

Set the IAM policy for a Cloud Healthcare API consent store.

**Synopsis:**
```
gcloud healthcare consent-stores set-iam-policy
    (CONSENT_STORE : --dataset=DATASET --location=LOCATION) POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ConsentStore resource - Cloud Healthcare API consent store whose IAM
policy to set. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument consent_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONSENT_STORE
     ID of the consentStore or fully qualified identifier for the
     consentStore.

     To set the consent_store attribute:
     + provide the argument consent_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument consent_store on the command line with a
       fully specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument consent_store on the command line with a
       fully specified name;
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
'policy.json' and set it for the consent store 'test-consent-store':

    $ gcloud healthcare consent-stores set-iam-policy \
        test-consent-store policy.json --dataset=test-dataset

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/consent-stores/set-iam-policy)

---
### `gcloud healthcare consent-stores update`

Update a Cloud Healthcare API consent store

Update a Cloud Healthcare API consent store.

**Synopsis:**
```
gcloud healthcare consent-stores update
    (CONSENT_STORE : --dataset=DATASET --location=LOCATION)
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ConsentStore resource - Cloud Healthcare API consent store to update. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument consent_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONSENT_STORE
     ID of the consentStore or fully qualified identifier for the
     consentStore.

     To set the consent_store attribute:
     + provide the argument consent_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument consent_store on the command line with a
       fully specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument consent_store on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update the consent store 'test-consent-store' with labels
{"key1":"value1", "key2":"value2"}, run:

    $ gcloud healthcare consent-stores update test-consent-store \
        --update-labels=key1=value1,key2=value2 --dataset=test-dataset
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/consent-stores/update)

---
# gcloud dataplex assets

manage Dataplex Asset resources

### `gcloud dataplex assets add-iam-policy-binding`

Adds IAM policy binding to a Dataplex asset resource

Adds IAM policy binding to a Dataplex asset resource.

**Synopsis:**
```
gcloud dataplex assets add-iam-policy-binding
    (ASSET : --lake=LAKE --location=LOCATION --zone=ZONE)
    --member=PRINCIPAL --role=ROLE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Assets resource - Arguments and flags that define the Dataplex asset you
want to add IAM policy binding to. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument asset on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ASSET
     ID of the assets or fully qualified identifier for the assets.

     To set the asset attribute:
     + provide the argument asset on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     The identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument asset on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument asset on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.

  --zone=ZONE
     The identifier of the Dataplex zone resource.

     To set the zone attribute:
     + provide the argument asset on the command line with a fully
       specified name;
     + provide the argument --zone on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Examples:**
```bash
To add an IAM policy binding for the role of roles/dataplex.viewer for the
user test-user@gmail.com to asset test-asset within zone test-zone in lake
test-lake in location us-central, run:

    $ gcloud dataplex assets add-iam-policy-binding test-asset \
        --location=us-central1 --lake=test-lake --zone=test-zone \
        --role=roles/dataplex.viewer --member=user:foo@gmail.com

See https://cloud.google.com/dataplex/docs/iam-roles for details of policy
role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/assets/add-iam-policy-binding)

---
### `gcloud dataplex assets create`

Create a Dataplex asset resource

An asset represents a cloud resource that is being managed within a lake as
a member of a zone.

This asset ID will be used to generate names such as table names when
publishing metadata to Hive Metastore and BigQuery.
  o Must contain only lowercase letters, numbers, and hyphens.
  o Must start with a letter.
  o Must end with a number or a letter.
  o Must be between 1-63 characters.
  o Must be unique within the zone.

**Synopsis:**
```
gcloud dataplex assets create
    (ASSET : --lake=LAKE --location=LOCATION --zone=ZONE)
    (--resource-type=RESOURCE_TYPE : --resource-name=RESOURCE_NAME
      --resource-read-access-mode=RESOURCE_READ_ACCESS_MODE) [--async]
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [--labels=[KEY=VALUE,...]] [--validate-only]
    [--[no-]discovery-enabled
      --discovery-exclude-patterns=[EXCLUDE_PATTERNS,...]
      --discovery-include-patterns=[INCLUDE_PATTERNS,...]
      --discovery-schedule=DISCOVERY_SCHEDULE --csv-delimiter=CSV_DELIMITER
      --[no-]csv-disable-type-inference --csv-encoding=CSV_ENCODING
      --csv-header-rows=CSV_HEADER_ROWS
      --[no-]json-disable-type-inference --json-encoding=JSON_ENCODING]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Assets resource - Arguments and flags that define the Dataplex asset you
want to create. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument asset on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ASSET
     ID of the assets or fully qualified identifier for the assets.

     To set the asset attribute:
     + provide the argument asset on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     The identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument asset on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument asset on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.

  --zone=ZONE
     The identifier of the Dataplex zone resource.

     To set the zone attribute:
     + provide the argument asset on the command line with a fully
       specified name;
     + provide the argument --zone on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--resource-type` | one of: BIGQUERY_DATASET BigQuery Dataset STORAGE_BUCKET Cloud Storage Bucket This flag argument must be specified if any of the other arguments in this group are specified |  | _[This must be specified.]_ Type. RESOURCE_TYPE must be one of: BIGQUERY_DATASET BigQuery Dataset STORAGE_BUCKET Cloud Storage Bucket This flag argument must be specified if any of the other arguments in this group are specified. |
| `--resource-name` | RESOURCE_NAME |  | _[This must be specified.]_ "Relative name of the cloud resource that contains the data that is being managed within a lake. For example: projects/{project_number}/buckets/{bucket_id} or projects/{project_number}/datasets/{dataset_id} |
| `--resource-read-access-mode` | one of: DIRECT Data is accessed directly using storage APIs MANAGED Data is accessed through a managed interface using BigQuery APIs |  | _[This must be specified.]_ Read access mode. RESOURCE_READ_ACCESS_MODE must be one of: DIRECT Data is accessed directly using storage APIs MANAGED Data is accessed through a managed interface using BigQuery APIs. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Description of the asset |
| `--display-name` | DISPLAY_NAME |  | Display name of the asset |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--validate-only` |  |  | Validate the create action, but don't actually perform it. |


**Examples:**
```bash
To create a Dataplex asset with name test-asset, within zone test-zone, in
lake test-lake, in location us-central1, with resource type STORAGE_BUCKET,
with resource name projects/test-project/buckets/test-bucket, run:

    $ gcloud dataplex assets create test-asset --location=us-central \
        --lake=test-lake --zone=test-zone \
        --resource-type=STORAGE_BUCKET \
        --resource-name=projects/test-project/buckets/test-bucket

To create a Dataplex asset with name test-asset, within zone test-zone, in
lake test-lake, in location us-central1, with resource type STORAGE_BUCKET,
with resource name projects/test-project/buckets/test-bucket, with
discovery-enabled, and discovery schedule 0 * * * *, run:

    $ gcloud dataplex assets create test-asset --location=us-central \
        --lake=test-lake --zone=test-zone \
        --resource-type=STORAGE_BUCKET \
        --resource-name=projects/test-project/buckets/test-bucket \
        --discovery-enabled --discovery-schedule="0 * * * *"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/assets/create)

---
### `gcloud dataplex assets delete`

Delete a Dataplex asset resource

Delete a Dataplex asset resource.

**Synopsis:**
```
gcloud dataplex assets delete
    (ASSET : --lake=LAKE --location=LOCATION --zone=ZONE) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Asset resource - Arguments and flags that define the Dataplex asset you
want to delete. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument asset on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ASSET
     ID of the asset or fully qualified identifier for the asset.

     To set the asset attribute:
     + provide the argument asset on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     Identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument asset on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument asset on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.

  --zone=ZONE
     Identifier of the Dataplex zone resource.

     To set the zone attribute:
     + provide the argument asset on the command line with a fully
       specified name;
     + provide the argument --zone on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a Dataplex asset test-asset within zone test-zone in lake
test-lake in location us-central1, run:

    $ gcloud dataplex assets delete test-asset --location=us-central1 \
      --lake=test-lake --zone=test-zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/assets/delete)

---
### `gcloud dataplex assets describe`

Describe a Dataplex asset resource

Displays all details of a Dataplex asset resource given a valid asset ID.

**Synopsis:**
```
gcloud dataplex assets describe
    (ASSET : --lake=LAKE --location=LOCATION --zone=ZONE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Asset resource - Arguments and flags that define the Dataplex asset you
want to retrieve. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument asset on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ASSET
     ID of the asset or fully qualified identifier for the asset.

     To set the asset attribute:
     + provide the argument asset on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     Identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument asset on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument asset on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.

  --zone=ZONE
     Identifier of the Dataplex zone resource.

     To set the zone attribute:
     + provide the argument asset on the command line with a fully
       specified name;
     + provide the argument --zone on the command line.
```

**Examples:**
```bash
To describe a Dataplex asset test-asset within zone test-zone in lake
test-lake in location us-central1, run:

    $ gcloud dataplex assets describe test-asset \
      --location=us-central1 --lake=test-lake --zone=test-zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/assets/describe)

---
### `gcloud dataplex assets get-iam-policy`

Get the IAM policy for a Dataplex asset resource

Displays the IAM policy associated with a Dataplex asset resource. If
formatted as JSON, the output can be edited and used as a policy file for
set-iam-policy. The output includes an "etag" field identifying the version
emitted and allowing detection of concurrent policy updates.

**Synopsis:**
```
gcloud dataplex assets get-iam-policy
    (ASSET : --lake=LAKE --location=LOCATION --zone=ZONE)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Asset resource - Arguments and flags that define the Dataplex asset IAM
policy you want to retrieve. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument asset on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ASSET
     ID of the asset or fully qualified identifier for the asset.

     To set the asset attribute:
     + provide the argument asset on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     Identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument asset on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument asset on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.

  --zone=ZONE
     Identifier of the Dataplex zone resource.

     To set the zone attribute:
     + provide the argument asset on the command line with a fully
       specified name;
     + provide the argument --zone on the command line.
```

**Examples:**
```bash
To print the IAM policy for Dataplex asset test-asset within zone test-zone
in lake test-lake in location us-central1, run:

    $ gcloud dataplex assets get-iam-policy test-asset \
      --location=us-central1 --lake=test-lake --zone=test-zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/assets/get-iam-policy)

---
### `gcloud dataplex assets list`

List Dataplex asset resources

List Dataplex asset resource under a specific project. location, lake, and
zone.

**Synopsis:**
```
gcloud dataplex assets list (--zone=ZONE : --lake=LAKE --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | _[This must be specified.]_ ID of the zone or fully qualified identifier for the zone. To set the zone attribute: + provide the argument --zone on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--lake` | LAKE |  | _[This must be specified.]_ Identifier of the Dataplex lake resource. To set the lake attribute: + provide the argument --zone on the command line with a fully specified name; + provide the argument --lake on the command line. |
| `--location` | LOCATION |  | _[This must be specified.]_ Location of the Dataplex resource. To set the location attribute: + provide the argument --zone on the command line with a fully specified name; + provide the argument --location on the command line; + set the property dataplex/location. |


**Examples:**
```bash
To list all Dataplex asset resources within zone test-zone in lake
test-lake in location us-central, run:

    $ gcloud dataplex assets list --location=us-central1 \
      --lake=test-lake --zone=test-zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/assets/list)

---
### `gcloud dataplex assets remove-iam-policy-binding`

Remove IAM policy binding from a Dataplex asset resource

Remove IAM policy binding from a Dataplex asset resource.

**Synopsis:**
```
gcloud dataplex assets remove-iam-policy-binding
    (ASSET : --lake=LAKE --location=LOCATION --zone=ZONE)
    --member=PRINCIPAL --role=ROLE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Assets resource - Arguments and flags that define the Dataplex asset you
want to remove IAM policy binding from. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument asset on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ASSET
     ID of the assets or fully qualified identifier for the assets.

     To set the asset attribute:
     + provide the argument asset on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     The identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument asset on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument asset on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.

  --zone=ZONE
     The identifier of the Dataplex zone resource.

     To set the zone attribute:
     + provide the argument asset on the command line with a fully
       specified name;
     + provide the argument --zone on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Examples:**
```bash
To remove an IAM policy binding for the role of roles/dataplex.viewer for
the user test-user@gmail.com from asset test-asset in zone test-zone in
lake test-lake in location us-central, run:

    $ gcloud dataplex assets remove-iam-policy-binding test-asset \
        --location=us-central1 --lake=test-lake --zone=test-zone \
        --role=roles/dataplex.viewer --member=user:foo@gmail.com

See https://cloud.google.com/dataplex/docs/iam-roles for details of policy
role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/assets/remove-iam-policy-binding)

---
### `gcloud dataplex assets set-iam-policy`

Set the IAM policy to a Dataplex asset as defined in a JSON or YAML file

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud dataplex assets set-iam-policy
    (ASSET : --lake=LAKE --location=LOCATION --zone=ZONE) POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Assets resource - Arguments and flags that define the Dataplex asset you
want to set IAM policy binding to. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument asset on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ASSET
     ID of the assets or fully qualified identifier for the assets.

     To set the asset attribute:
     + provide the argument asset on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     The identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument asset on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument asset on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.

  --zone=ZONE
     The identifier of the Dataplex zone resource.

     To set the zone attribute:
     + provide the argument asset on the command line with a fully
       specified name;
     + provide the argument --zone on the command line.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command will read an IAM policy defined in a JSON file
policy.son and set it for the Dataplex asset test-asset in zone test-zone
in lake test-lake in location us-central1:

    $ gcloud dataplex assets set-iam-policy test-asset \
        --location=us-central1 --lake=test-lake --zone=test-zone \
        policy.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/assets/set-iam-policy)

---
### `gcloud dataplex assets update`

Update a Dataplex asset resource

Update a Dataplex asset resource.

**Synopsis:**
```
gcloud dataplex assets update
    (ASSET : --lake=LAKE --location=LOCATION --zone=ZONE) [--async]
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [--labels=[KEY=VALUE,...]]
    [--resource-read-access-mode=RESOURCE_READ_ACCESS_MODE]
    [--validate-only]
    [--[no-]discovery-enabled
      --discovery-exclude-patterns=[EXCLUDE_PATTERNS,...]
      --discovery-include-patterns=[INCLUDE_PATTERNS,...]
      --discovery-schedule=DISCOVERY_SCHEDULE --csv-delimiter=CSV_DELIMITER
      --[no-]csv-disable-type-inference --csv-encoding=CSV_ENCODING
      --csv-header-rows=CSV_HEADER_ROWS
      --[no-]json-disable-type-inference --json-encoding=JSON_ENCODING]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Assets resource - Arguments and flags that define the Dataplex asset you
want to update. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument asset on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ASSET
     ID of the assets or fully qualified identifier for the assets.

     To set the asset attribute:
     + provide the argument asset on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     The identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument asset on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument asset on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.

  --zone=ZONE
     The identifier of the Dataplex zone resource.

     To set the zone attribute:
     + provide the argument asset on the command line with a fully
       specified name;
     + provide the argument --zone on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Description of the asset |
| `--display-name` | DISPLAY_NAME |  | Display Name |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--validate-only` |  |  | _[Data is accessed through a managed interface using BigQuery APIs.]_ Validate the update action, but don't actually perform it. |


**Examples:**
```bash
To update a Dataplex asset test-asset in zone test-zone in lake test-lake
in location us-central1 to have the display name first-dataplex-asset and
discovery include patterns abc, def, run:

    $ gcloud dataplex assets update test-asset --location=us-central1 \
        --lake=test-lake --zone=test-zone \
        --display-name="first-dataplex-asset" \
        --discovery-include-patterns=abc,def
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/assets/update)

---

## `gcloud dataplex assets actions` — manage Dataplex asset resource actions
### `gcloud dataplex assets actions list`

List Dataplex asset actions

List all Dataplex Actions under a specific asset.

**Synopsis:**
```
gcloud dataplex assets actions list
    (--asset=ASSET : --lake=LAKE --location=LOCATION --zone=ZONE)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--asset` | ASSET |  | _[This must be specified.]_ ID of the asset or fully qualified identifier for the asset. To set the asset attribute: + provide the argument --asset on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--lake` | LAKE |  | _[This must be specified.]_ Identifier of the Dataplex lake resource. To set the lake attribute: + provide the argument --asset on the command line with a fully specified name; + provide the argument --lake on the command line. |
| `--location` | LOCATION |  | _[This must be specified.]_ Location of the Dataplex resource. To set the location attribute: + provide the argument --asset on the command line with a fully specified name; + provide the argument --location on the command line; + set the property dataplex/location. |
| `--zone` | ZONE |  | _[This must be specified.]_ Identifier of the Dataplex zone resource. To set the zone attribute: + provide the argument --asset on the command line with a fully specified name; + provide the argument --zone on the command line. |


**Examples:**
```bash
To list all actions of a Dataplex asset test-asset defined in location
us-central1 with lake test-lake, zone test-zone, run:

    $ gcloud dataplex assets actions list --project=test-project \
        --location=us-central1 --lake=test-lake --zone=test-zone \
        --asset=test-asset
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/assets/actions/list)

---
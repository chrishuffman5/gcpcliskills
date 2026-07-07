# gcloud dataplex zones

manage Dataplex Zone resources

### `gcloud dataplex zones add-iam-policy-binding`

Add IAM policy binding to a Dataplex zone resource

Add IAM policy binding to a Dataplex zone resource.

**Synopsis:**
```
gcloud dataplex zones add-iam-policy-binding
    (ZONE : --lake=LAKE --location=LOCATION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Zones resource - Arguments and flags that define the Dataplex zone you
want to add IAM policy binding to. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument zone on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ZONE
     ID of the zones or fully qualified identifier for the zones.

     To set the zone attribute:
     + provide the argument zone on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     The identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument zone on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument zone on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Examples:**
```bash
To add an IAM policy binding for the role of roles/dataplex.viewer for the
user test-user@gmail.com to zone test-zone within lake test-lake in
location us-central, run:

    $ gcloud dataplex zones add-iam-policy-binding test-zone \
        --location=us-central1 --lake=test-lake \
        --role=roles/dataplex.viewer --member=user:foo@gmail.com

See https://cloud.google.com/dataplex/docs/iam-roles for details of policy
role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/zones/add-iam-policy-binding)

---
### `gcloud dataplex zones create`

Create a zone

A zone represents a logical group of related assets within a lake. A zone
can be used to map to organizational structure or represent stages of data
readiness from raw to curated. It provides managing behavior that is shared
or inherited by all contained assets.

The Zone ID is used to generate names such as database and dataset names
when publishing metadata to Hive Metastore and BigQuery.
  o Must contain only lowercase letters, numbers, and hyphens.
  o Must start with a letter.
  o Must end with a number or a letter.
  o Must be between 1-63 characters.
  o Must be unique across all lakes from all locations in a project.

**Synopsis:**
```
gcloud dataplex zones create (ZONE : --lake=LAKE --location=LOCATION)
    --resource-location-type=RESOURCE_LOCATION_TYPE --type=TYPE [--async]
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
Zones resource - Arguments and flags that define the Dataplex zone you
want to create. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument zone on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ZONE
     ID of the zones or fully qualified identifier for the zones.

     To set the zone attribute:
     + provide the argument zone on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     The identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument zone on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument zone on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--resource-location-type` | one of: MULTI_REGION Resources that are associated with a multi-region location |  | _[This must be specified.]_ Location type of the resources attached to a zone. RESOURCE_LOCATION_TYPE must be one of: MULTI_REGION Resources that are associated with a multi-region location. SINGLE_REGION Resources that are associated with a single region. |
| `--type` | one of: CURATED A zone that contains data that is considered to be ready for broader consumption and analytics workloads |  | _[This must be specified.]_ Type. TYPE must be one of: CURATED A zone that contains data that is considered to be ready for broader consumption and analytics workloads. Curated structured data stored in Cloud Storage must conform to certain file formats (Parquet, Avro, and Orc) and organized in a hive-compatible directory layout. RAW A zone that contains data that needs further processing before it is considered generally ready for consumption and analytics workloads. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Description of the zone. |
| `--display-name` | DISPLAY_NAME |  | Display name of the zone. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--validate-only` |  |  | Validate the create action, but don't actually perform it. |


**Examples:**
```bash
To create a Dataplex zone with name test-zone within lake test-lake in
location us-central1 with type RAW, and resource location type
SINGLE_REGION, run:

    $ gcloud dataplex zones create test-zone --location=us-central \
        --lake=test-lake --resource-location-type=SINGLE_REGION \
        --type=RAW

To create a Dataplex zone with name test-zone within lake test-lake in
location us-central1 with type RAW,resource location type SINGLE_REGION
with discovery-enabled and discovery schedule 0 * * * *, run:

    $ gcloud dataplex zones create test-zone --location=us-central \
        --lake=test-lake --resource-location-type=SINGLE_REGION \
        --type=RAW --discovery-enabled --discovery-schedule="0 * * * *"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/zones/create)

---
### `gcloud dataplex zones delete`

Delete a Dataplex zone resource

Delete a Dataplex zone resource.

**Synopsis:**
```
gcloud dataplex zones delete (ZONE : --lake=LAKE --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Zone resource - Arguments and flags that define the Dataplex zone you want
to delete. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument zone on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ZONE
     ID of the zone or fully qualified identifier for the zone.

     To set the zone attribute:
     + provide the argument zone on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     Identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument zone on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument zone on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a Dataplex zone test-zone within lake test-lake in location
us-central1, run:

    $ gcloud dataplex zones delete test-lake --location=us-central1 \
      --lake=test-lake
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/zones/delete)

---
### `gcloud dataplex zones describe`

Describe a Dataplex zone resource

Displays all details of a Dataplex zone resource given a valid zone ID.

**Synopsis:**
```
gcloud dataplex zones describe (ZONE : --lake=LAKE --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Zone resource - Arguments and flags that define the Dataplex zones you
want to retrieve. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument zone on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ZONE
     ID of the zone or fully qualified identifier for the zone.

     To set the zone attribute:
     + provide the argument zone on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     Identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument zone on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument zone on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Examples:**
```bash
To describe a Dataplex zone test-zone within lake test-lake in location
us-central1, run:

    $ gcloud dataplex zones describe test-zone --location=us-central1 \
      --lake=test-lake
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/zones/describe)

---
### `gcloud dataplex zones get-iam-policy`

Get the IAM policy for a Dataplex zone resource

Displays the IAM policy associated with a Dataplex zone resource. If
formatted as JSON, the output can be edited and used as a policy file for
set-iam-policy. The output includes an "etag" field identifying the version
emitted and allowing detection of concurrent policy updates.

**Synopsis:**
```
gcloud dataplex zones get-iam-policy
    (ZONE : --lake=LAKE --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Zone resource - Arguments and flags that define the Dataplex zone IAM
policy you want to retrieve. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument zone on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ZONE
     ID of the zone or fully qualified identifier for the zone.

     To set the zone attribute:
     + provide the argument zone on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     Identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument zone on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument zone on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Examples:**
```bash
To print the IAM policy for Dataplex zone test-zone within lake test-lake
in location us-central1, run:

    $ gcloud dataplex zones get-iam-policy test-zone \
      --location=us-central1 --lake=test-lake
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/zones/get-iam-policy)

---
### `gcloud dataplex zones list`

List Dataplex zone resources under a lake

List Dataplex zone resource under a specific project. location, and lake.

**Synopsis:**
```
gcloud dataplex zones list (--lake=LAKE : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--lake` | LAKE |  | _[This must be specified.]_ ID of the lake or fully qualified identifier for the lake. To set the lake attribute: + provide the argument --lake on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Location of the Dataplex resource. To set the location attribute: + provide the argument --lake on the command line with a fully specified name; + provide the argument --location on the command line; + set the property dataplex/location. |


**Examples:**
```bash
To list all Dataplex zone resources within lake test-lake in location
us-central, run:

    $ gcloud dataplex zones list --location=us-central1 --lake=test-lake
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/zones/list)

---
### `gcloud dataplex zones remove-iam-policy-binding`

Remove IAM policy binding from a Dataplex zone resource

Remove IAM policy binding from a Dataplex zone resource.

**Synopsis:**
```
gcloud dataplex zones remove-iam-policy-binding
    (ZONE : --lake=LAKE --location=LOCATION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Zones resource - Arguments and flags that define the Dataplex zone you
want to remove IAM policy binding from. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument zone on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ZONE
     ID of the zones or fully qualified identifier for the zones.

     To set the zone attribute:
     + provide the argument zone on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     The identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument zone on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument zone on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Examples:**
```bash
To remove an IAM policy binding for the role roles/dataplex.viewer for the
user test-user@gmail.com from zone test-zone in lake test-lake in location
us-central, run:

    $ gcloud dataplex zones remove-iam-policy-binding test-zone \
        --location=us-central1 --lake=test-lake \
        --role=roles/dataplex.viewer --member=user:foo@gmail.com

See https://cloud.google.com/dataplex/docs/iam-roles for details of policy
role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/zones/remove-iam-policy-binding)

---
### `gcloud dataplex zones set-iam-policy`

Set the IAM policy to a Dataplex zone as defined in a JSON or YAML file

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud dataplex zones set-iam-policy
    (ZONE : --lake=LAKE --location=LOCATION) POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Zones resource - Arguments and flags that define the Dataplex zone you
want to set IAM policy binding to. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument zone on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ZONE
     ID of the zones or fully qualified identifier for the zones.

     To set the zone attribute:
     + provide the argument zone on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     The identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument zone on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument zone on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command will read an IAM policy defined in a JSON file
policy.son and set it for the Dataplex zone test-zone defined in lake
test-lake in location us-central1:

    $ gcloud dataplex zones set-iam-policy test-zone \
        --location=us-central1 --lake=test-lake policy.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/zones/set-iam-policy)

---
### `gcloud dataplex zones update`

Update a Dataplex zone resource

Update a Dataplex zone resource.

**Synopsis:**
```
gcloud dataplex zones update (ZONE : --lake=LAKE --location=LOCATION)
    [--async] [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
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
Zones resource - Arguments and flags that define the Dataplex zone you
want to update. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument zone on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ZONE
     ID of the zones or fully qualified identifier for the zones.

     To set the zone attribute:
     + provide the argument zone on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     The identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument zone on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument zone on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Description of the zone |
| `--display-name` | DISPLAY_NAME |  | Display Name |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--validate-only` |  |  | Validate the create action, but don't actually perform it. |


**Examples:**
```bash
To update a Dataplex zone test-zone in lake test-lake in location
us-central1 to have the display name first-dataplex-zone and discovery
include patterns abc, def, run:

    $ gcloud dataplex zones update test-zone --location=us-central1 \
        --lake=test-lake --display-name="first-dataplex-zone" \
        --discovery-include-patterns=abc,def
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/zones/update)

---

## `gcloud dataplex zones actions` — manage Dataplex zone resource actions
### `gcloud dataplex zones actions list`

List Dataplex zone actions

List all Dataplex Actions under a specific zone.

**Synopsis:**
```
gcloud dataplex zones actions list
    (--zone=ZONE : --lake=LAKE --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | _[This must be specified.]_ ID of the zone or fully qualified identifier for the zone. To set the zone attribute: + provide the argument --zone on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--lake` | LAKE |  | _[This must be specified.]_ Identifier of the Dataplex lake resource. To set the lake attribute: + provide the argument --zone on the command line with a fully specified name; + provide the argument --lake on the command line. |
| `--location` | LOCATION |  | _[This must be specified.]_ Location of the Dataplex resource. To set the location attribute: + provide the argument --zone on the command line with a fully specified name; + provide the argument --location on the command line; + set the property dataplex/location. |


**Examples:**
```bash
To list all actions of a Dataplex zone test-zone defined in project
test-project in location us-central1 with lake test-lake, run:

    $ gcloud dataplex zones actions list --project=test-project \
        --location=us-central1 --lake=test-lake --zone=test-zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/zones/actions/list)

---
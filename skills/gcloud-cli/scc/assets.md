# gcloud scc assets

filter an organization's assets and groups them by their specified properties

### `gcloud scc assets describe`

Describe an asset given its resource name or asset id

(DEPRECATED) Security Command Center Asset APIs are deprecated and will be
removed on or after June 26, 2024. Use Cloud Asset Inventory instead
(gcloud asset) (https://cloud.google.com/sdk/gcloud/reference/asset). For
more information, see the deprecation notice at Assets Page
(https://cloud.google.com/security-command-center/docs/how-to-use-security-command-center#assets_page).

Describe an asset given its resource name or asset id.

**Synopsis:**
```
gcloud scc assets describe [PARENT]
    (--asset=ASSET | --resource-name=RESOURCE_NAME) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Parent resource - parent organization, folder, or project in the Google
Cloud resource hierarchy to be used for the gcloud scc command. Specify
the argument as either [RESOURCE_TYPE/RESOURCE_ID] or [RESOURCE_ID], as
shown in the preceding examples. This represents a Cloud resource.

  [PARENT]
     ID of the parent or fully qualified identifier for the parent.

     To set the parent attribute:
     + provide the argument parent on the command line;
     + Set the parent property in configuration using gcloud config set
       scc/parent if it is not specified in command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--asset` | ASSET |  | _[Exactly one of these must be specified:]_ Cloud SCC specific asset. It's derived from the the asset's relative resource name. See: https://cloud.google.com/apis/design/resource_names#relative_resource_name. For Example, for the given asset name: "organizations/123/assets/456", 456 represents asset id. |
| `--resource-name` | RESOURCE_NAME |  | _[Exactly one of these must be specified:]_ Asset's resource name. Full resource name of the Google Cloud Platform resource this asset represents. This field is immutable after create time. See: https://cloud.google.com/apis/design/resource_names#full_resource_name. For Example: "//cloudresourcemanager.googleapis.com/projects/1234567890123" could be the resource-name for a project. |


**Examples:**
```bash
Describe an asset under organization 123456, given its full resource name
(https://cloud.google.com/apis/design/resource_names#full_resource_name)
e.g. //storage.googleapis.com/my-bucket:

    $ gcloud scc assets describe 123456 \
        --resource-name="//storage.googleapis.com/my-bucket"

Describe an asset under organization 123456, given its Cloud SCC asset id
5678

    $ gcloud scc assets describe 123456 --asset=5678

Describe an asset under project example-project, given its Cloud SCC asset
id 5678

    $ gcloud scc assets describe projects/example-project/assets/5678

Describe an asset under folder 456, given its Cloud SCC asset id 5678

    $ gcloud scc assets describe folders/456/assets/5678
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/assets/describe)

---
### `gcloud scc assets get-parent`

Get the Parent for an asset given its resource name or asset id

(DEPRECATED) Security Command Center Asset APIs are deprecated and will be
removed on or after June 26, 2024. Use Cloud Asset Inventory instead
(gcloud asset) (https://cloud.google.com/sdk/gcloud/reference/asset). For
more information, see the deprecation notice at Assets Page
(https://cloud.google.com/security-command-center/docs/how-to-use-security-command-center#assets_page).

Get the Parent for an asset given its resource name or asset id.

**Synopsis:**
```
gcloud scc assets get-parent [ORGANIZATION]
    (--asset=ASSET | --resource-name=RESOURCE_NAME) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Organization resource - The organization to be used for the SCC (Security
Command Center) command. This represents a Cloud resource.

  [ORGANIZATION]
     ID of the organization or fully qualified identifier for the
     organization.

     To set the organization attribute:
     + provide the argument organization on the command line;
     + Set the organization property in configuration using gcloud
       config set scc/organization if it is not specified in command
       line..
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--asset` | ASSET |  | _[Exactly one of these must be specified:]_ Cloud SCC specific asset. It's derived from the the asset's relative resource name. See: https://cloud.google.com/apis/design/resource_names#relative_resource_name. For Example, for the given asset name: "organizations/123/assets/456", 456 represents asset id. |
| `--resource-name` | RESOURCE_NAME |  | _[Exactly one of these must be specified:]_ Asset's resource name. Full resource name of the Google Cloud Platform resource this asset represents. This field is immutable after create time. See: https://cloud.google.com/apis/design/resource_names#full_resource_name. For Example: "//cloudresourcemanager.googleapis.com/projects/1234567890123" could be the resource-name for a project. |


**Examples:**
```bash
Get parent's relative resource name given an asset's full resource name
(https://cloud.google.com/apis/design/resource_names#full_resource_name)
e.g. //storage.googleapis.com/my-bucket under organization 123456:

    $ gcloud scc assets get-parent 123456 \
        --resource-name="//storage.googleapis.com/my-bucket"

Get parent's relative resource name given an asset's Cloud SCC id 5678
under organization 123456.

    $ gcloud scc assets get-parent 123456 --asset=5678
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/assets/get-parent)

---
### `gcloud scc assets get-project`

Get the Project for an asset given its resource name or asset id

(DEPRECATED) Security Command Center Asset APIs are deprecated and will be
removed on or after June 26, 2024. Use Cloud Asset Inventory instead
(gcloud asset) (https://cloud.google.com/sdk/gcloud/reference/asset). For
more information, see the deprecation notice at Assets Page
(https://cloud.google.com/security-command-center/docs/how-to-use-security-command-center#assets_page).

Get the Project for an asset given its resource name or asset id.

**Synopsis:**
```
gcloud scc assets get-project [ORGANIZATION]
    (--asset=ASSET | --resource-name=RESOURCE_NAME) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Organization resource - The organization to be used for the SCC (Security
Command Center) command. This represents a Cloud resource.

  [ORGANIZATION]
     ID of the organization or fully qualified identifier for the
     organization.

     To set the organization attribute:
     + provide the argument organization on the command line;
     + Set the organization property in configuration using gcloud
       config set scc/organization if it is not specified in command
       line..
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--asset` | ASSET |  | _[Exactly one of these must be specified:]_ Cloud SCC specific asset. It's derived from the the asset's relative resource name. See: https://cloud.google.com/apis/design/resource_names#relative_resource_name. For Example, for the given asset name: "organizations/123/assets/456", 456 represents asset id. |
| `--resource-name` | RESOURCE_NAME |  | _[Exactly one of these must be specified:]_ Asset's resource name. Full resource name of the Google Cloud Platform resource this asset represents. This field is immutable after create time. See: https://cloud.google.com/apis/design/resource_names#full_resource_name. For Example: "//cloudresourcemanager.googleapis.com/projects/1234567890123" could be the resource-name for a project. |


**Examples:**
```bash
Get project id
(https://cloud.google.com/resource-manager/docs/creating-managing-projects#identifying_projects)
given an asset's full resource name
(https://cloud.google.com/apis/design/resource_names#full_resource_name)
e.g. //storage.googleapis.com/my-bucket under organization 123456:

    $ gcloud scc assets get-project 123456 \
        --resource-name="//storage.googleapis.com/my-bucket"

Get project id given an asset's Cloud SCC id 5678 under organization
123456.

    $ gcloud scc assets get-project 123456 --asset=5678
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/assets/get-project)

---
### `gcloud scc assets list`

List Cloud Security Command Center assets

(DEPRECATED) Security Command Center Asset APIs are deprecated and will be
removed on or after June 26, 2024. Use Cloud Asset Inventory instead
(gcloud asset) (https://cloud.google.com/sdk/gcloud/reference/asset). For
more information, see the deprecation notice at Assets Page
(https://cloud.google.com/security-command-center/docs/how-to-use-security-command-center#assets_page).

List Cloud Security Command Center assets.

**Synopsis:**
```
gcloud scc assets list [PARENT] [--compare-duration=COMPARE_DURATION]
    [--field-mask=FIELD_MASK] [--order-by=ORDER_BY]
    [--page-token=PAGE_TOKEN] [--read-time=READ_TIME] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Parent resource - parent organization, folder, or project in the Google
Cloud resource hierarchy to be used for the gcloud scc command. Specify
the argument as either [RESOURCE_TYPE/RESOURCE_ID] or [RESOURCE_ID], as
shown in the preceding examples. This represents a Cloud resource.

  [PARENT]
     ID of the parent or fully qualified identifier for the parent.

     To set the parent attribute:
     + provide the argument parent on the command line;
     + Set the parent property in configuration using gcloud config set
       scc/parent if it is not specified in command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--compare-duration` | COMPARE_DURATION |  | The result's "state_change" attribute is updated to indicate whether the asset was added, removed, or remained present during the compare_duration period of time that precedes the read_time. See $ gcloud topic datetimes for information on supported duration formats. |
| `--field-mask` | FIELD_MASK |  | Field mask to specify the Asset fields to be listed in the response. An empty field mask will list all fields. Example field mask: "asset.security_center_properties.resource_type,asset.security_center_properties.resource_parent" |
| `--order-by` | ORDER_BY |  | Expression that defines what fields and order to use for sorting. Example order by: "resource_properties.sort_prop ASC" |
| `--page-token` | PAGE_TOKEN |  | The value returned by the last 'ListAssetsResponse'; indicates that this is a continuation of a prior 'ListAssets' call, and that the system should return the next page of data. |
| `--read-time` | READ_TIME |  | Time used as a reference point when filtering. Absence of this field will default to the API's version of NOW. See $ gcloud topic datetimes for information on supported time formats. |


**Examples:**
```bash
List all assets under organization (123456)

    $ gcloud scc assets list 123456

List all assets under project (example-project)

    $ gcloud scc assets list projects/example-project

List all assets under folder (456)

    $ gcloud scc assets list folders/456

List all assets under organization (123456) that were present as of
2019-01-01T01:00:00 GMT time.

    $ gcloud scc assets list 123456 --read-time="2019-01-01T01:00:00Z"

Only list category and resource_name for all assets under organization
(123456):

    $ gcloud scc assets list 123456 --field-mask="category,resource_name"

List all compute instances under organization (123456):

    $ gcloud scc assets list 123456 \
        --filter="security_center_properties.resource_type=\"google.comp\
    ute.Instance\""

List all firewall rules that have open HTTP Ports:

    $ gcloud scc assets list 123456 \
        --filter="security_center_properties.resource_type = \
    \"google.compute.Firewall\" AND resource_properties.name \
        =\"default-allow-http\""

List all assets that belong to either projects: 5678 OR 78910 (project's
numeric identifier).

    $ gcloud scc assets list 123456 \
        --filter="security_center_properties.resource_parent = \
    \"//cloudresourcemanager.googleapis.com/projects/5678\" OR \
        security_center_properties.resource_parent = "\78910\""

List all projects that are owned by a user:someone@domain.com. Notice the
usage of : which enforces partial matching.

    $ gcloud scc assets list 123456 \
        --filter="security_center_properties.resource_type = \
    \"google.cloud.resourcemanager.Project\" AND \
        security_center_properties.resource_owners : \
        \"user:someone@domain.com\""

List assets and add a state_change property that indicates if the asset was
added, removed, or remained present during the past 24 hours period:

    $ gcloud scc assets list 123456 --compare-duration=86400s
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/assets/list)

---
### `gcloud scc assets list-marks`

List an assets's security marks

(DEPRECATED) Security Command Center Asset APIs are deprecated and will be
removed on or after June 26, 2024. Use Cloud Asset Inventory instead
(gcloud asset) (https://cloud.google.com/sdk/gcloud/reference/asset). For
more information, see the deprecation notice at Assets Page
(https://cloud.google.com/security-command-center/docs/how-to-use-security-command-center#assets_page).

List an assets's security marks.

**Synopsis:**
```
gcloud scc assets list-marks (ASSET : --organization=ORGANIZATION)
    [--page-token=PAGE_TOKEN] [--read-time=READ_TIME] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Asset resource - The asset to be used for the SCC (Security Command
Center) command. The arguments in this group can be used to specify the
attributes of this resource.

This must be specified.

  ASSET
     ID of the asset or fully qualified identifier for the asset.

     To set the asset attribute:
     + provide the argument asset on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --organization=ORGANIZATION
     (Optional) If the full resource name isn't provided e.g.
     organizations/123, then provide the organization id which is the
     suffix of the organization. Example: organizations/123, the id is
     123.

     To set the organization attribute:
     + provide the argument asset on the command line with a fully
       specified name;
     + provide the argument --organization on the command line;
     + Set the organization property in configuration using gcloud
       config set scc/organization if it is not specified in command
       line..
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--page-token` | PAGE_TOKEN |  | Response objects will return a non-null value for page-token to indicate that there is at least one additional page of data. User can either directly request that page by specifying the page-token explicitly or let gcloud fetch one-page-at-a-time. |
| `--read-time` | READ_TIME |  | Time used as a reference point when filtering. Absence of this field will default to the API's version of NOW. See $ gcloud topic datetimes for information on supported time formats. |


**Examples:**
```bash
List all security marks for asset (8910) under organization (123456):

    $ gcloud scc assets list-marks 8910 --organization=123456

List all security marks for asset (8910) under project (example-project):

    $ gcloud scc assets list-marks \
        projects/example-project/assets/8910 --organization=123456

List all security marks for asset (8910) under folder (456):

    $ gcloud scc assets list-marks folders/456/assets/8910 \
        --organization=123456
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/assets/list-marks)

---
### `gcloud scc assets run-discovery`

Scan an organization for new/modified/deleted assets

(DEPRECATED) Security Command Center Asset APIs are deprecated and will be
removed on or after June 26, 2024. Use Cloud Asset Inventory instead
(gcloud asset) (https://cloud.google.com/sdk/gcloud/reference/asset). For
more information, see the deprecation notice at Assets Page
(https://cloud.google.com/security-command-center/docs/how-to-use-security-command-center#assets_page).

Scan an organization for new/modified/deleted assets. Note that this API
can only be called with limited frequency for an organization. If it is
called too frequently the caller will receive a TOO_MANY_REQUESTS error.

**Synopsis:**
```
gcloud scc assets run-discovery [ORGANIZATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Organization resource - The organization for which scan should be run.
This represents a Cloud resource.

  [ORGANIZATION]
     ID of the organization or fully qualified identifier for the
     organization.

     To set the organization attribute:
     + provide the argument organization on the command line;
     + Set the organization property in configuration using gcloud
       config set scc/organization if it is not specified in command
       line..
```

**Examples:**
```bash
Run new scan for organization (123456):

    $ gcloud scc assets run-discovery 123456
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/assets/run-discovery)

---
### `gcloud scc assets update-marks`

Update Cloud Security Command Center asset's security marks

Update Cloud Security Command Center asset's security marks.

**Synopsis:**
```
gcloud scc assets update-marks (ASSET : --organization=ORGANIZATION)
    [--security-marks=[KEY=VALUE,...]] [--start-time=START_TIME]
    [--update-mask=UPDATE_MASK] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Asset resource - The asset to be used for the SCC (Security Command
Center) command. The arguments in this group can be used to specify the
attributes of this resource.

This must be specified.

  ASSET
     ID of the asset or fully qualified identifier for the asset.

     To set the asset attribute:
     + provide the argument asset on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --organization=ORGANIZATION
     (Optional) If the full resource name isn't provided e.g.
     organizations/123, then provide the organization id which is the
     suffix of the organization. Example: organizations/123, the id is
     123.

     To set the organization attribute:
     + provide the argument asset on the command line with a fully
       specified name;
     + provide the argument --organization on the command line;
     + Set the organization property in configuration using gcloud
       config set scc/organization if it is not specified in command
       line..
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--security-marks` | [KEY=VALUE,...] |  | SecurityMarks resource to be passed as the request body. It's a key=value pair separated by comma (,). For example: --security-marks="key1=val1,key2=val2". |
| `--start-time` | START_TIME |  | Time at which the updated SecurityMarks take effect. See $ gcloud topic datetimes for information on supported time formats. |
| `--update-mask` | UPDATE_MASK |  | Use update-mask if you want to selectively update marks represented by --security-marks flag. For example: --update-mask="marks.key1,marks.key2". If you want to override all the marks for the given asset either skip the update-mask flag or provide an empty value (--update-mask '') for it. |


**Examples:**
```bash
Selectively update value of security mark (key1) with 'val1.1' on asset
5678 under organization 123456. Note that other security marks on the same
asset will not change.

    $ gcloud scc assets update-marks 5678 --organization=123456 \
        --security-marks="key1=val1.1" --update-mask="marks.key1"

Update value of security mark (key1) and delete other marks on asset 5678
under organization 123456:

    $ gcloud scc assets update-marks 5678 --organization=123456 \
        --security-marks="key1=updatedVal"

Update value of security mark (key1) and delete other marks on asset 5678
under project example-project:

    $ gcloud scc assets update-marks \
        projects/example-project/assets/5678 \
        --security-marks="key1=updatedVal"

Update value of security mark (key1) and delete other marks on asset 5678
under folder 456:

    $ gcloud scc assets update-marks folders/456/assets/5678 \
        --security-marks="key1=updatedVal"

Delete all security marks on asset 5678 under organization 123456:

    $ gcloud scc assets update-marks 5678 --organization=123456 \
        --security-marks=""
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/assets/update-marks)

---
# gcloud asset (top-level commands)

### `gcloud asset analyze-iam-policy`

Analyzes IAM policies that match a request

Analyzes IAM policies that match a request.

**Synopsis:**
```
gcloud asset analyze-iam-policy
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID
      | --project=PROJECT_ID) [--access-time=ACCESS_TIME]
    [--full-resource-name=FULL_RESOURCE_NAME] [--identity=IDENTITY]
    [--saved-analysis-query=SAVED_ANALYSIS_QUERY]
    [--analyze-service-account-impersonation
      --execution-timeout=EXECUTION_TIMEOUT --expand-groups
      --expand-resources --expand-roles
      --output-group-edges --output-resource-edges --show-response]
    [--permissions=[PERMISSIONS,...] --roles=[ROLES,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[Exactly one of these must be specified:]_ Folder ID on which to perform the analysis. Only policies defined at or below this folder will be targeted in the analysis. |
| `--organization` | ORGANIZATION_ID |  | _[Exactly one of these must be specified:]_ Organization ID on which to perform the analysis. Only policies defined at or below this organization will be targeted in the analysis. |
| `--project` | PROJECT_ID |  | _[Exactly one of these must be specified:]_ Project ID or number on which to perform the analysis. Only policies defined at or below this project will be targeted in the analysis. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--access-time` | ACCESS_TIME |  | _[The hypothetical context to evaluate IAM conditions.]_ The hypothetical access timestamp to evaluate IAM conditions. |
| `--full-resource-name` | FULL_RESOURCE_NAME |  | _[Specifies a resource for analysis. Leaving it empty means ANY.]_ The full resource name. |
| `--identity` | IDENTITY |  | _[Specifies an identity for analysis. Leaving it empty means ANY.]_ The identity appearing in the form of principals in the IAM policy binding. |
| `--saved-analysis-query` | SAVED_ANALYSIS_QUERY |  | _[Specifies the name of a saved analysis query.]_ The name of a saved query. When a saved_analysis_query is provided, its query content will be used as the base query. Other flags' values will override the base query to compose the final query to run. IDs might be in one of the following formats: + projects/project_number/savedQueries/saved_query_id folders/folder_number/savedQueries/saved_query_id organizations/organization_number/savedQueries/saved_query_id |
| `--analyze-service-account-impersonation` |  |  | _[The analysis options.]_ If true, the response will include access analysis from identities to resources via service account impersonation. This is a very expensive operation, because many derived queries will be executed. We highly recommend you use AnalyzeIamPolicyLongrunning rpc instead. Default is false. |
| `--execution-timeout` | EXECUTION_TIMEOUT |  | _[The analysis options.]_ The amount of time the executable has to complete. See JSON representation of Duration (https://developers.google.com/protocol-buffers/docs/proto3#json). Deafult is empty. |
| `--expand-groups` |  |  | _[The analysis options.]_ If true, the identities section of the result will expand any Google groups appearing in an IAM policy binding. Default is false. |
| `--expand-resources` |  |  | _[The analysis options.]_ If true, the resource section of the result will expand any resource attached to an IAM policy to include resources lower in the resource hierarchy. Default is false. |
| `--expand-roles` |  |  | _[The analysis options.]_ If true, the access section of result will expand any roles appearing in IAM policy bindings to include their permissions. Default is false. |
| `--output-group-edges` |  |  | _[The analysis options.]_ If true, the result will output the relevant membership relationships between groups. Default is false. |
| `--output-resource-edges` |  |  | _[The analysis options.]_ If true, the result will output the relevant parent/child relationships between resources. Default is false. |
| `--show-response` |  |  | _[The analysis options.]_ If true, the response will be showed as-is in the command output. |
| `--permissions` | [PERMISSIONS,...] |  | _[Specifies roles or permissions for analysis. Leaving it empty means ANY.]_ The permissions to appear in the result. |
| `--roles` | [ROLES,...] |  | _[Specifies roles or permissions for analysis. Leaving it empty means ANY.]_ The roles to appear in the result. |


**Examples:**
```bash
To find out which users have been granted the iam.serviceAccounts.actAs
permission on a service account, run:

    $ gcloud asset analyze-iam-policy --organization=YOUR_ORG_ID \
        --full-resource-name=YOUR_SERVICE_ACCOUNT_FULL_RESOURCE_NAME \
        --permissions='iam.serviceAccounts.actAs'

To find out which resources a user can access, run:

    $ gcloud asset analyze-iam-policy --organization=YOUR_ORG_ID \
        --identity='user:u1@foo.com'

To find out which roles or permissions a user has been granted on a
project, run:

    $ gcloud asset analyze-iam-policy --organization=YOUR_ORG_ID \
        --full-resource-name=YOUR_PROJECT_FULL_RESOURCE_NAME \
        --identity='user:u1@foo.com'

To find out which users have been granted the iam.serviceAccounts.actAs
permission on any applicable resources, run:

    $ gcloud asset analyze-iam-policy --organization=YOUR_ORG_ID \
        --permissions='iam.serviceAccounts.actAs'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/asset/analyze-iam-policy)

---
### `gcloud asset analyze-iam-policy-longrunning`

Analyzes IAM policies that match a request asynchronously and writes the results to Google Cloud Storage or BigQuery destination

Analyzes IAM policies that match a request asynchronously and writes the
results to Google Cloud Storage or BigQuery destination.

**Synopsis:**
```
gcloud asset analyze-iam-policy-longrunning
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID
      | --project=PROJECT_ID)
    (--gcs-output-path=GCS_OUTPUT_PATH
      | [--bigquery-dataset=BIGQUERY_DATASET
      --bigquery-table-prefix=BIGQUERY_TABLE_PREFIX
      : --bigquery-partition-key=BIGQUERY_PARTITION_KEY
      --bigquery-write-disposition=BIGQUERY_WRITE_DISPOSITION])
    [--access-time=ACCESS_TIME] [--full-resource-name=FULL_RESOURCE_NAME]
    [--identity=IDENTITY]
    [--analyze-service-account-impersonation --expand-groups
      --expand-resources
      --expand-roles --output-group-edges --output-resource-edges]
    [--permissions=[PERMISSIONS,...] --roles=[ROLES,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[Exactly one of these must be specified:]_ Folder ID on which to perform the analysis. Only policies defined at or below this folder will be targeted in the analysis. |
| `--organization` | ORGANIZATION_ID |  | _[Exactly one of these must be specified:]_ Organization ID on which to perform the analysis. Only policies defined at or below this organization will be targeted in the analysis. |
| `--project` | PROJECT_ID |  | _[Exactly one of these must be specified:]_ Project ID or number on which to perform the analysis. Only policies defined at or below this project will be targeted in the analysis. |
| `--gcs-output-path` | GCS_OUTPUT_PATH |  | _[Exactly one of these must be specified:]_ Google Cloud Storage URI where the results will be written. URI must start with "gs://". For example, "gs://bucket_name/object_name". |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--access-time` | ACCESS_TIME |  | _[The hypothetical context to evaluate IAM conditions.]_ The hypothetical access timestamp to evaluate IAM conditions. |
| `--full-resource-name` | FULL_RESOURCE_NAME |  | _[Specifies a resource for analysis. Leaving it empty means ANY.]_ The full resource name. |
| `--identity` | IDENTITY |  | _[Specifies an identity for analysis. Leaving it empty means ANY.]_ The identity appearing in the form of principals in the IAM policy binding. |
| `--analyze-service-account-impersonation` |  |  | _[The analysis options.]_ If true, the response will include access analysis from identities to resources via service account impersonation. This is a very expensive operation, because many derived queries will be executed. We highly recommend you use AnalyzeIamPolicyLongrunning rpc instead. Default is false. |
| `--expand-groups` |  |  | _[The analysis options.]_ If true, the identities section of the result will expand any Google groups appearing in an IAM policy binding. Default is false. |
| `--expand-resources` |  |  | _[The analysis options.]_ If true, the resource section of the result will expand any resource attached to an IAM policy to include resources lower in the resource hierarchy. Default is false. |
| `--expand-roles` |  |  | _[The analysis options.]_ If true, the access section of result will expand any roles appearing in IAM policy bindings to include their permissions. Default is false. |
| `--output-group-edges` |  |  | _[The analysis options.]_ If true, the result will output the relevant membership relationships between groups. Default is false. |
| `--output-resource-edges` |  |  | _[The analysis options.]_ If true, the result will output the relevant parent/child relationships between resources. Default is false. |
| `--permissions` | [PERMISSIONS,...] |  | _[Specifies roles or permissions for analysis. Leaving it empty means ANY.]_ The permissions to appear in the result. |
| `--roles` | [ROLES,...] |  | _[Specifies roles or permissions for analysis. Leaving it empty means ANY.]_ The roles to appear in the result. |


**Examples:**
```bash
To find out which users have been granted the iam.serviceAccounts.actAs
permission on a service account, and write analysis results to Google Cloud
Storage, run:

    $ gcloud asset analyze-iam-policy-longrunning \
        --organization=YOUR_ORG_ID \
        --full-resource-name=YOUR_SERVICE_ACCOUNT_FULL_RESOURCE_NAME \
        --permissions='iam.serviceAccounts.actAs' \
        --gcs-output-path='gs://YOUR_BUCKET_NAME/YOUR_OBJECT_NAME'

To find out which resources a user can access, and write analysis results
to Google Cloud Storage, run:

    $ gcloud asset analyze-iam-policy-longrunning \
        --organization=YOUR_ORG_ID --identity='user:u1@foo.com' \
        --gcs-output-path='gs://YOUR_BUCKET_NAME/YOUR_OBJECT_NAME'

To find out which roles or permissions a user has been granted on a
project, and write analysis results to BigQuery, run:

    $ gcloud asset analyze-iam-policy-longrunning \
        --organization=YOUR_ORG_ID \
        --full-resource-name=YOUR_PROJECT_FULL_RESOURCE_NAME \
        --identity='user:u1@foo.com' \
        --bigquery-dataset='projects/YOUR_PROJECT_ID/datasets/YOUR_DATAS\
    ET_ID' --bigquery-table-prefix='YOUR_BIGQUERY_TABLE_PREFIX'

To find out which users have been granted the iam.serviceAccounts.actAs
permission on any applicable resources, and write analysis results to
BigQuery, run:

    $ gcloud asset analyze-iam-policy-longrunning \
        --organization=YOUR_ORG_ID \
        --permissions='iam.serviceAccounts.actAs' \
        --bigquery-dataset='projects/YOUR_PROJECT_ID/datasets/YOUR_DATAS\
    ET_ID' --bigquery-table-prefix='YOUR_BIGQUERY_TABLE_PREFIX'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/asset/analyze-iam-policy-longrunning)

---
### `gcloud asset analyze-move`

Analyzes resource move

Analyze resource migration from its current resource hierarchy.

**Synopsis:**
```
gcloud asset analyze-move --project=PROJECT_ID
    (--destination-folder=FOLDER_ID
      | --destination-organization=ORGANIZATION_ID)
    [--blockers-only=BLOCKERS_ONLY] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--project` | PROJECT_ID |  | The project ID or number to perform the analysis. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--blockers-only` | BLOCKERS_ONLY |  | Determines whether to perform analysis against blockers only. Leaving it empty means the full analysis will be performed including warnings and blockers for the specified resource move. |


**Examples:**
```bash
To analyze the impacts of moving a project to a different organization,
run:

    $ gcloud asset analyze-move --project=YOUR_PROJECT_ID \
      --destination-organization=ORGANIZATION_ID

To analyze the impacts of moving a project to a different folder, run:

    $ gcloud asset analyze-move --project=YOUR_PROJECT_ID \
      --destination-folder=FOLDER_ID

To analyze only the blockers of moving a project to a different folder,
run:

    $ gcloud asset analyze-move --project=YOUR_PROJECT_ID \
      --destination-folder=FOLDER_ID --blockers-only=true
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/asset/analyze-move)

---
### `gcloud asset analyze-org-policies`

Analyze organization policies under a scope

Analyze organization policies under a scope.

**Synopsis:**
```
gcloud asset analyze-org-policies --constraint=CONSTRAINT --scope=SCOPE
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--constraint` | CONSTRAINT |  | The name of the constraint to analyze organization policies for. The response only contains analyzed organization policies for the provided constraint. Example: * organizations/{ORGANIZATION_NUMBER}/customConstraints/{CUSTOM_CONSTRAINT_NAME} for a user-defined custom constraint. |
| `--scope` | SCOPE |  | Scope can only be an organization. The analysis is limited to the Cloud organization policies within this scope. The caller must be granted the cloudasset.assets.searchAllResources permission on the desired scope. The allowed values are: * organizations/{ORGANIZATION_NUMBER} (e.g. organizations/123456) |


**Examples:**
```bash
To list 10 organization policies of a constraint in an organization, run:

    $ gcloud asset analyze-org-policies \
        --scope=organizations/YOUR_ORG_ID \
        --constraint=YOUR_CONSTRAINT_NAME --limit=10
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/asset/analyze-org-policies)

---
### `gcloud asset analyze-org-policy-governed-assets`

Analyze organization policies governed assets under a scope

Analyze organization policies governed assets under a scope.

**Synopsis:**
```
gcloud asset analyze-org-policy-governed-assets --constraint=CONSTRAINT
    --scope=SCOPE [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--constraint` | CONSTRAINT |  | The name of the constraint to analyze organization policies for. The response only contains analyzed organization policies for the provided constraint. Examples: * organizations/{ORGANIZATION_NUMBER}/customConstraints/{CUSTOM_CONSTRAINT_NAME} for a user-defined custom constraint. * organizations/{ORGANIZATION_NUMBER}/constraints/{CANNED_CONSTRAINT_NAME} for a gcp-service-defined canned constraint. |
| `--scope` | SCOPE |  | Scope can only be an organization. The analysis is limited to the Cloud organization policies and assets within this scope. The caller must be granted the cloudasset.assets.searchAllResources and cloudasset.assets.searchAllIamPolicies permission on the desired scope. The allowed values are: * organizations/{ORGANIZATION_NUMBER} (e.g. organizations/123456) |


**Examples:**
```bash
To list 10 assets governed by a constraint in an organization, run:

    $ gcloud asset analyze-org-policy-governed-assets \
        --scope=organizations/YOUR_ORG_ID \
        --constraint=YOUR_CONSTRAINT_NAME --limit=10
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/asset/analyze-org-policy-governed-assets)

---
### `gcloud asset analyze-org-policy-governed-containers`

Analyze organization policies governed containers under a scope

Analyze organization policies governed containers under a scope.

**Synopsis:**
```
gcloud asset analyze-org-policy-governed-containers --constraint=CONSTRAINT
    --scope=SCOPE [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--constraint` | CONSTRAINT |  | The name of the constraint to analyze organization policies for. The response only contains analyzed organization policies for the provided constraint. Example: * organizations/{ORGANIZATION_NUMBER}/customConstraints/{CUSTOM_CONSTRAINT_NAME} for a user-defined custom constraint. |
| `--scope` | SCOPE |  | Scope can only be an organization. The analysis is limited to the Cloud organization policies and containers within this scope. The caller must be granted the cloudasset.assets.searchAllResources permission on the desired scope. The allowed values are: * organizations/{ORGANIZATION_NUMBER} (e.g. organizations/123456) |


**Examples:**
```bash
To list 10 containers governed by a constraint in an organization, run:

    $ gcloud asset analyze-org-policy-governed-containers \
        --scope=organizations/YOUR_ORG_ID \
        --constraint=YOUR_CONSTRAINT_NAME --limit=10
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/asset/analyze-org-policy-governed-containers)

---
### `gcloud asset export`

Export the cloud assets to Google Cloud Storage/BigQuery

Export the cloud assets to Google Cloud Storage or BigQuery. Use gcloud
asset operations describe to get the latest status of the operation. Note
that to export a project different from the project you want to bill, you
can use --billing-project or authenticate with a service account. See
https://cloud.google.com/resource-manager/docs/cloud-asset-inventory/gcloud-asset
for examples of using a service account.

**Synopsis:**
```
gcloud asset export
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID
      | --project=PROJECT_ID)
    (--output-path=OUTPUT_PATH | --output-path-prefix=OUTPUT_PATH_PREFIX
      | [(--bigquery-table=BIGQUERY_TABLE
      : --bigquery-dataset=BIGQUERY_DATASET) : --output-bigquery-force
      --partition-key=PARTITION_KEY --per-asset-type])
    [--asset-types=[ASSET_TYPES,...]] [--content-type=CONTENT_TYPE]
    [--relationship-types=[RELATIONSHIP_TYPES,...]]
    [--snapshot-time=SNAPSHOT_TIME] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[Exactly one of these must be specified:]_ The ID of the folder which is the root asset. |
| `--organization` | ORGANIZATION_ID |  | _[Exactly one of these must be specified:]_ The ID of the organization which is the root asset. |
| `--project` | PROJECT_ID |  | _[Exactly one of these must be specified:]_ The project which is the root asset. The Google Cloud project ID to use for this invocation. If omitted, then the current project is assumed; the current project can be listed using gcloud config list --format='text(core.project)' and can be set using gcloud config set project PROJECTID. --project and its fallback core/project property play two roles in the invocation. It specifies the project of the resource to operate on. It also specifies the project for API enablement check, quota, and billing. To specify a different project for quota and billing, use --billing-project or billing/quota_project property. |
| `--output-path` | OUTPUT_PATH |  | _[Exactly one of these must be specified:]_ Google Cloud Storage URI where the results will go. URI must start with "gs://". For example, "gs://bucket_name/object_name" |
| `--output-path-prefix` | OUTPUT_PATH_PREFIX |  | _[Exactly one of these must be specified:]_ Google Cloud Storage URI where the results will go. URI must start with "gs://". For example, "gs://bucket_name/object_name_prefix", in which case each exported object uri is in format: "gs://bucket_name/object_name_prefix/<asset type>/<shard number>" and it only contains assets for that type. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--asset-types` | [ASSET_TYPES,...] |  | A list of asset types (i.e., "compute.googleapis.com/Disk") to take a snapshot. If specified and non-empty, only assets matching the specified types will be returned. See http://cloud.google.com/asset-inventory/docs/supported-asset-types for supported asset types. |
| `--content-type` | one of: resource, iam-policy, org-policy, access-policy, os-inventory, relationship |  | Asset content type. If specified, only content matching the specified type will be returned. Otherwise, no content but the asset name will be returned. Specifying resource will export resource metadata, specifying iam-policy will export the IAM policy for each child asset, specifying org-policy will export the Org Policy set on child assets, specifying access-policy will export the Access Policy set on child assets, specifying os-inventory will export the OS inventory of VM instances, and specifying relationship will export relationships of the assets. CONTENT_TYPE must be one of: resource, iam-policy, org-policy, access-policy, os-inventory, relationship. |
| `--relationship-types` | [RELATIONSHIP_TYPES,...] |  | A list of relationship types (i.e., "INSTANCE_TO_INSTANCEGROUP") to take a snapshot. This argument will only be honoured if content_type=RELATIONSHIP. If specified and non-empty, only relationships matching the specified types will be returned. See http://cloud.google.com/asset-inventory/docs/supported-asset-types for supported relationship types. |
| `--snapshot-time` | SNAPSHOT_TIME |  | Timestamp to take a snapshot on assets. This can only be a current or past time. If not specified, the current time will be used. Due to delays in resource data collection and indexing, there is a volatile window during which running the same query at different times may return different results. See $ gcloud topic datetimes for information on time formats. |


**Examples:**
```bash
To export a snapshot of assets of type 'compute.googleapis.com/Disk' in
project 'test-project' at '2019-03-05T00:00:00Z' to
'gs://bucket-name/object-name' and only export the asset metadata, run:

    $ gcloud asset export --project='test-project' \
        --asset-types='compute.googleapis.com/Disk' \
        --snapshot-time='2019-03-05T00:00:00Z' \
        --output-path='gs://bucket-name/object-name' \
        --content-type='resource'

To export a snapshot of assets of type 'compute.googleapis.com/Disk' in
project 'test-project' at '2019-03-05T00:00:00Z' to
'projects/projectId/datasets/datasetId/tables/table_name', overwrite the
table if existed, run:

    $ gcloud asset export --project='test-project' \
        --asset-types='compute.googleapis.com/Disk' \
        --snapshot-time='2019-03-05T00:00:00Z' \
        --bigquery-table='projects/projectId/datasets/datasetId/tables/t\
    able_name' --output-bigquery-force --content-type='resource'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/asset/export)

---
### `gcloud asset get-effective-iam-policy`

Get effective IAM policies for a specified list of resources within accessible scope, such as a project, folder or organization

Batch get effective IAM policies that match a request.

**Synopsis:**
```
gcloud asset get-effective-iam-policy --names=NAMES,[NAMES,...]
    --scope=SCOPE [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--names` | NAMES,[NAMES,...] |  | Names refer to a list of full resource names (https://cloud.google.com/asset-inventory/docs/resource-name-format) of searchable asset types (https://cloud.google.com/asset-inventory/docs/supported-asset-types). For each batch call, total number of names provided is between 1 and 20. The example value is: * //cloudsql.googleapis.com/projects/{PROJECT_ID}/instances/{INSTANCE} (e.g. //cloudsql.googleapis.com/projects/probe-per-rt-project/instances/instance1) |
| `--scope` | SCOPE |  | Scope can be a project, a folder, or an organization. The search is limited to the IAM policies within this scope. The caller must be granted the cloudasset.assets.analyzeIamPolicy, cloudasset.assets.searchAllResources, cloudasset.assets.searchAllIamPolicies permissions on the desired scope. The allowed values are: * projects/{PROJECT_ID} (e.g. projects/foo-bar) * projects/{PROJECT_NUMBER} (e.g. projects/12345678) * folders/{FOLDER_NUMBER} (e.g. folders/1234567) * organizations/{ORGANIZATION_NUMBER} (e.g. organizations/123456) |


**Examples:**
```bash
To list effective IAM policies of 1 resource in an organization, run:

    $ gcloud asset get-effective-iam-policy \
        --scope=organizations/YOUR_ORG_ID --names=RESOURCE_NAME1

To list effective IAM policies of 2 resources in a folder, run:

    $ gcloud asset get-effective-iam-policy \
        --scope=folders/YOUR_FOLDER_ID \
        --names=RESOURCE_NAME1,RESOURCE_NAME2

To list effective IAM policies of 3 resources in a project using project
ID, run:

    $ gcloud asset get-effective-iam-policy \
        --scope=projects/YOUR_PROJECT_ID \
        --names=RESOURCE_NAME1,RESOURCE_NAME2,RESOURCE_NAME3

To list effective IAM policies of 2 resources in a project using project
number, run:

    $ gcloud asset get-effective-iam-policy \
        --scope=projects/YOUR_PROJECT_NUMBER \
        --names=RESOURCE_NAME1,RESOURCE_NAME2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/asset/get-effective-iam-policy)

---
### `gcloud asset get-history`

Get the update history of assets that overlaps a time window

Get the update history of assets that overlaps a time window.

**Synopsis:**
```
gcloud asset get-history --asset-names=[ASSET_NAMES,...]
    --content-type=CONTENT_TYPE --start-time=START_TIME
    (--organization=ORGANIZATION_ID | --project=PROJECT_ID)
    [--end-time=END_TIME] [--relationship-types=[RELATIONSHIP_TYPES,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--asset-names` | [ASSET_NAMES,...] |  | A list of full names of the assets to get the history for. For more information, see: https://cloud.google.com/apis/design/resource_names#full_resource_name |
| `--content-type` | one of: resource, iam-policy, org-policy, access-policy, os-inventory, relationship |  | Asset content type. Specifying resource will export resource metadata, specifying iam-policy will export the IAM policy for each child asset, specifying org-policy will export the Org Policy set on child assets, specifying access-policy will export the Access Policy set on child assets, specifying os-inventory will export the OS inventory of VM instances, and specifying relationship will export relationships of the assets. CONTENT_TYPE must be one of: resource, iam-policy, org-policy, access-policy, os-inventory, relationship. |
| `--start-time` | START_TIME |  | Start time of the time window (inclusive) for the asset history. Must be after the current time minus 35 days. See $ gcloud topic datetimes for information on time formats. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--end-time` | END_TIME |  | End time of the time window (exclusive) for the asset history. Defaults to current time if not specified. See $ gcloud topic datetimes for information on time formats. |
| `--relationship-types` | [RELATIONSHIP_TYPES,...] |  | A list of relationship types (i.e., "INSTANCE_TO_INSTANCEGROUP") to take a snapshot. This argument will only be honoured if content_type=RELATIONSHIP. If specified and non-empty, only relationships matching the specified types will be returned. See http://cloud.google.com/asset-inventory/docs/supported-asset-types for supported relationship types. |


**Examples:**
```bash
To get the history of asset metadata for
'//compute.googleapis.com/projects/test-project/zones/us-central1-f/instances/instance1'
between '2018-10-02T15:01:23.045Z' and '2018-12-05T13:01:21.045Z', run:

    $ gcloud asset get-history --project='test-project' \
        --asset-names='//compute.googleapis.com/projects/test-project/zo\
    nes/us-central1-f/instances/instance1' \
        --start-time='2018-10-02T15:01:23.045Z' \
        --end-time='2018-12-05T13:01:21.045Z' --content-type='resource'

To get the history of asset iam policy for
'//cloudresourcemanager.googleapis.com/projects/10179387634' between
'2018-10-02T15:01:23.045Z' and '2018-12-05T13:01:21.045Z', and project
'10179387634' is in organization '1060499660910', run:

    $ gcloud asset get-history --organization='1060499660910' \
        --asset-names='//cloudresourcemanager.googleapis.com/projects/10\
    179387634' --start-time='2018-10-02T15:01:23.045Z' \
        --end-time='2018-12-05T13:01:21.045Z' \
        --content-type='iam-policy'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/asset/get-history)

---
### `gcloud asset list`

List the Cloud assets

List the Cloud assets. Note that to list a project different from the
project you want to bill, you can use --billing-project or authenticate
with a service account. See
https://cloud.google.com/resource-manager/docs/cloud-asset-inventory/gcloud-asset
for examples of using a service account.

**Synopsis:**
```
gcloud asset list
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID
      | --project=PROJECT_ID) [--asset-types=[ASSET_TYPES,...]]
    [--content-type=CONTENT_TYPE]
    [--relationship-types=[RELATIONSHIP_TYPES,...]]
    [--snapshot-time=SNAPSHOT_TIME] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[Exactly one of these must be specified:]_ The ID of the folder which is the root asset. |
| `--organization` | ORGANIZATION_ID |  | _[Exactly one of these must be specified:]_ The ID of the organization which is the root asset. |
| `--project` | PROJECT_ID |  | _[Exactly one of these must be specified:]_ The project which is the root asset. The Google Cloud project ID to use for this invocation. If omitted, then the current project is assumed; the current project can be listed using gcloud config list --format='text(core.project)' and can be set using gcloud config set project PROJECTID. --project and its fallback core/project property play two roles in the invocation. It specifies the project of the resource to operate on. It also specifies the project for API enablement check, quota, and billing. To specify a different project for quota and billing, use --billing-project or billing/quota_project property. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--asset-types` | [ASSET_TYPES,...] |  | A list of asset types (i.e., "compute.googleapis.com/Disk") to take a snapshot. If specified and non-empty, only assets matching the specified types will be returned. See http://cloud.google.com/asset-inventory/docs/supported-asset-types for supported asset types. |
| `--content-type` | one of: resource, iam-policy, org-policy, access-policy, os-inventory, relationship |  | Asset content type. If not specified, no content but the asset name and type will be returned in the feed. For more information, see https://cloud.google.com/asset-inventory/docs/reference/rest/v1/feeds#ContentType. CONTENT_TYPE must be one of: resource, iam-policy, org-policy, access-policy, os-inventory, relationship. |
| `--relationship-types` | [RELATIONSHIP_TYPES,...] |  | A list of relationship types (i.e., "INSTANCE_TO_INSTANCEGROUP") to take a snapshot. This argument will only be honoured if content_type=RELATIONSHIP. If specified and non-empty, only relationships matching the specified types will be returned. See http://cloud.google.com/asset-inventory/docs/supported-asset-types for supported relationship types. |
| `--snapshot-time` | SNAPSHOT_TIME |  | Timestamp to take a snapshot on assets. This can only be a current or past time. If not specified, the current time will be used. Due to delays in resource data collection and indexing, there is a volatile window during which running the same query at different times may return different results. See $ gcloud topic datetimes for information on time formats. |


**Examples:**
```bash
To list a snapshot of assets of type 'compute.googleapis.com/Disk' in
project 'test-project' at '2019-03-05T00:00:00Z', run:

    $ gcloud asset list --project='test-project' \
        --asset-types='compute.googleapis.com/Disk' \
        --snapshot-time='2019-03-05T00:00:00Z'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/asset/list)

---
### `gcloud asset query`

Query the Cloud assets

Issue an analytical query on Cloud assets using a BigQuery Standard SQL
compatible statement.

**Synopsis:**
```
gcloud asset query
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID
      | --project=PROJECT_ID)
    (--job-reference=JOB_REFERENCE | --statement=STATEMENT)
    [--page-size=PAGE_SIZE] [--page-token=PAGE_TOKEN] [--timeout=TIMEOUT]
    [--snapshot-time=SNAPSHOT_TIME
      | [--start-time=START_TIME : --end-time=END_TIME]]
    [--write-disposition=WRITE_DISPOSITION [--bigquery-table=BIGQUERY_TABLE
      : --bigquery-dataset=BIGQUERY_DATASET]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[Exactly one of these must be specified:]_ The ID of the folder which is the root asset. |
| `--organization` | ORGANIZATION_ID |  | _[Exactly one of these must be specified:]_ The ID of the organization which is the root asset. |
| `--project` | PROJECT_ID |  | _[Exactly one of these must be specified:]_ The project which is the root asset. The Google Cloud project ID to use for this invocation. If omitted, then the current project is assumed; the current project can be listed using gcloud config list --format='text(core.project)' and can be set using gcloud config set project PROJECTID. --project and its fallback core/project property play two roles in the invocation. It specifies the project of the resource to operate on. It also specifies the project for API enablement check, quota, and billing. To specify a different project for quota and billing, use --billing-project or billing/quota_project property. |
| `--job-reference` | JOB_REFERENCE |  | _[Exactly one of these must be specified:]_ Reference to the query job, which is from the previous call. |
| `--statement` | STATEMENT |  | _[Exactly one of these must be specified:]_ A BigQuery Standard SQL compatible statement. If the query execution finishes within timeout and there is no pagination, the full query results will be returned. Otherwise, pass job_reference from previous call as --job-reference to obtain the full results. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--page-size` | PAGE_SIZE |  | The maximum number of rows to return in the results. One page is also limited to 10 MB. |
| `--page-token` | PAGE_TOKEN |  | A page token received from previous call. |
| `--timeout` | TIMEOUT |  | Maximum amount of time that the client will wait for the query to complete. |


**Examples:**
```bash
To count the number of compute instances, run:

    $ gcloud asset query --project='test-project' \
        --statement='SELECT * FROM compute_googleapis_com_Instance'

To see the query result of the previous job, pass the job-reference from
the previous response:

    $ gcloud asset query --project='test-project' \
        --job-reference=<job-reference-from>
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/asset/query)

---
### `gcloud asset search-all-iam-policies`

Searches all IAM policies within the specified accessible scope, such as a project, folder or organization

Searches all IAM policies within the specified scope, such as a project,
folder or organization. The caller must be granted the
cloudasset.assets.searchAllIamPolicies permission on the desired scope.

Note: The query is compared against each IAM policy binding, including its
principals, roles and conditions. The returned IAM policies, will only
contain the bindings that match your query. To learn more about the IAM
policy structure, see the IAM policy documentation
(https://cloud.google.com/iam/help/allow-policies/structure).

**Synopsis:**
```
gcloud asset search-all-iam-policies [--asset-types=[ASSET_TYPES,...]]
    [--order-by=ORDER_BY] [--query=QUERY] [--scope=SCOPE]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--asset-types` | [ASSET_TYPES,...] |  | List of asset types that the IAM policies are attached to. If empty, it will search the IAM policies that are attached to all the searchable asset types (https://cloud.google.com/asset-inventory/docs/supported-asset-types). Regular expressions are also supported. For example: * compute.googleapis.com.* snapshots IAM policies attached to asset type starts with compute.googleapis.com. * .*Instance snapshots IAM policies attached to asset type ends with Instance. * .*Instance.* snapshots IAM policies attached to asset type contains Instance. See RE2 (https://github.com/google/re2/wiki/Syntax) for all supported regular expression syntax. If the regular expression does not match any supported asset type, an INVALID_ARGUMENT error will be returned. |
| `--order-by` | ORDER_BY |  | Comma-separated list of fields specifying the sorting order of the results. The default order is ascending. Add DESC after the field name to indicate descending order. Redundant space characters are ignored. Example: assetType DESC, resource. Only singular primitive fields in the response are sortable: * resource * assetType * project All the other fields such as repeated fields (e.g., folders) and non-primitive fields (e.g., policy) are not supported. Both --order-by and --sort-by flags can be used to sort the output, with the following differences: * The --order-by flag performs server-side sorting (better performance), while the --sort-by flag performs client-side sorting. * The --sort-by flag supports all the fields in the output, while the --order-by flag only supports limited fields as shown above. |
| `--query` | QUERY |  | Query statement. See how to construct a query (https://cloud.google.com/asset-inventory/docs/searching-iam-policies#how_to_construct_a_query) for more information. If not specified or empty, it will search all the IAM policies within the specified scope. Note that the query string is compared against each Cloud IAM policy binding, including its principals, roles, and Cloud IAM conditions. The returned Cloud IAM policies will only contain the bindings that match your query. To learn more about the IAM policy structure, see the IAM policy documentation (https://cloud.google.com/iam/help/allow-policies/structure). Examples: * policy:amy@gmail.com to find IAM policy bindings that specify user amy@gmail.com. * policy:roles/compute.admin to find IAM policy bindings that specify the Compute Admin role. * policy:comp* to find IAM policy bindings that contain comp as a prefix of any word in the binding. * policy.role.permissions:storage.buckets.update to find IAM policy bindings that specify a role containing the storage.buckets.update permission. Note that if callers haven't been granted the iam.roles.get permission for a role's included permissions, policy bindings that specify this role will be dropped from the search results. * policy.role.permissions:upd* to find IAM policy bindings that specify a role containing upd as a prefix of any word in the role permission. Note that if callers haven't been granted the iam.roles.get permission for a role's included permissions, policy bindings that specify this role will be dropped from the search results. * resource:organizations/123456 to find IAM policy bindings that are set on organizations/123456. * resource=//cloudresourcemanager.googleapis.com/projects/myproject to find IAM policy bindings that are set on the project named myproject. * Important to find IAM policy bindings that contain Important as a word in any of the searchable fields (except for the included permissions). * resource:(instance1 OR instance2) policy:amy to find IAM policy bindings that are set on resources instance1 or instance2 and also specify user amy. * roles:roles/compute.admin to find IAM policy bindings that specify the Compute Admin role. * memberTypes:user to find IAM policy bindings that contain the user principal type. |
| `--scope` | SCOPE |  | Scope can be a project, a folder, or an organization. The search is limited to the IAM policies within this scope. The caller must be granted the cloudasset.assets.searchAllIamPolicies permission on the desired scope. If not specified, the configured project property (https://cloud.google.com//sdk/docs/configurations#setting_configuration_properties) will be used. To find the configured project, run: gcloud config get project. To change the setting, run: gcloud config set project PROJECT_ID. The allowed values are: * projects/{PROJECT_ID} (e.g. projects/foo-bar) * projects/{PROJECT_NUMBER} (e.g. projects/12345678) * folders/{FOLDER_NUMBER} (e.g. folders/1234567) * organizations/{ORGANIZATION_NUMBER} (e.g. organizations/123456) |


**Examples:**
```bash
To search all the IAM policies that specify amy@mycompany.com within
organizations/123456, ensure the caller has been granted the
cloudasset.assets.searchAllIamPolicies permission on the organization and
run:

    $ gcloud asset search-all-iam-policies \
        --scope='organizations/123456' \
        --query='policy:amy@mycompany.com'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/asset/search-all-iam-policies)

---
### `gcloud asset search-all-resources`

Searches all Cloud resources within the specified accessible scope, such as a project, folder or organization

Searches all Cloud resources within the specified scope, such as a project,
folder or organization. The caller must be granted the
cloudasset.assets.searchAllResources permission on the desired scope.

**Synopsis:**
```
gcloud asset search-all-resources [--asset-types=[ASSET_TYPES,...]]
    [--order-by=ORDER_BY] [--query=QUERY] [--read-mask=READ_MASK]
    [--scope=SCOPE] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--asset-types` | [ASSET_TYPES,...] |  | A list of asset types that this request searches for. If empty, it will search all the searchable asset types (https://cloud.google.com/asset-inventory/docs/supported-asset-types). Regular expressions are also supported. For example: * compute.googleapis.com.* snapshots resources whose asset type starts with compute.googleapis.com. * .*Instance snapshots resources whose asset type ends with Instance. * .*Instance.* snapshots resources whose asset type contains Instance. See RE2 (https://github.com/google/re2/wiki/Syntax) for all supported regular expression syntax. If the regular expression does not match any supported asset type, an INVALID_ARGUMENT error will be returned. |
| `--order-by` | ORDER_BY |  | A comma-separated list of fields specifying the sorting order of the results. The default order is ascending. Add DESC after the field name to indicate descending order. Redundant space characters are ignored. Example: location DESC, name. Only singular primitive fields in the response are sortable: * name * assetType * project * displayName * description * location * createTime * updateTime * state * parentFullResourceName * parentAssetType All the other fields such as repeated fields (e.g., networkTags, kmsKeys), map fields (e.g., labels) and struct fields (e.g., additionalAttributes) are not supported. Both --order-by and --sort-by flags can be used to sort the output, with the following differences: * The --order-by flag performs server-side sorting (better performance), while the --sort-by flag performs client-side sorting. * The --sort-by flag supports all the fields in the output, while the --order-by flag only supports limited fields as shown above. |
| `--query` | QUERY |  | The query statement. See how to construct a query (https://cloud.google.com/asset-inventory/docs/searching-resources#how_to_construct_a_query) for more details. If not specified or empty, it will search all the resources within the specified scope. Examples: * name:Important to find Cloud resources whose name contains Important as a word. * name=Important to find the Cloud resource whose name is exactly Important. * displayName:Impor* to find Cloud resources whose display name contains Impor as a prefix of any word. * location:us-west* to find Cloud resources whose location contains both us and west as prefixes. * labels:prod to find Cloud resources whose labels contain prod as a key or value. * labels.env:prod to find Cloud resources that have a label env and its value is prod. * labels.env:* to find Cloud resources that have a label env. * tagKeys:env to find Cloud resources that are directly attached to tags where the `TagKey.namespacedName` (https://cloud.google.com/resource-manager/reference/rest/v3/tagKeys#resource:-tagkey) contains env. * tagValues:prod* to find Cloud resources that are directly attached to tags where the `TagValue.namespacedName` (https://cloud.google.com/resource-manager/reference/rest/v3/tagValues#resource:-tagvalue) contains a word prefixed by prod. * tagValueIds=tagValues/123 to find Cloud resources that are directly attached to tags where the `TagValue.name` (https://cloud.google.com/resource-manager/reference/rest/v3/tagValues#resource:-tagvalue) is exactly tagValues/123. * effectiveTagKeys:env to find Cloud resources that are directly attached to or inherited tags where the `TagKey.namespacedName` (https://cloud.google.com/resource-manager/reference/rest/v3/tagKeys#resource:-tagkey) contains env. * effectiveTagValues:prod* to find Cloud resources that are directly attached to or inherited tags where the `TagValue.namespacedName` (https://cloud.google.com/resource-manager/reference/rest/v3/tagValues#resource:-tagvalue) contains a word prefixed by prod. * effectiveTagValueIds=tagValues/123 to find Cloud resources that are directly attached to or inherited tags where the `TagValue.name` (https://cloud.google.com/resource-manager/reference/rest/v3/tagValues#resource:-tagvalue) is exactly tagValues/123. * kmsKey:key to find Cloud resources encrypted with a customer-managed encryption key whose name contains key as a word. This field is deprecated. Please use the kmsKeys field to retrieve KMS key information. * kmsKeys:key to find Cloud resources encrypted with customer-managed encryption keys whose name contains the word key. * relationships:instance-group-1 to find Cloud resources that have relationships with instance-group-1 in the related resource name. * relationships:INSTANCE_TO_INSTANCEGROUP to find Compute instances that have relationships of type INSTANCE_TO_INSTANCEGROUP. * relationships.INSTANCE_TO_INSTANCEGROUP:instance-group-1 to find Compute instances that have relationships with instance-group-1 in the Compute instance group resource name, for relationship type INSTANCE_TO_INSTANCEGROUP. * sccSecurityMarks.key=value to find Cloud resources that are attached with security marks whose key is key and value is value. * sccSecurityMarks.key:* to find Cloud resources that are attached with security marks whose key is key. * state:ACTIVE to find Cloud resources whose state contains ACTIVE as a word. * NOT state:ACTIVE to find Cloud resources whose state doesn't contain ACTIVE as a word. * createTime<1609459200 or createTime<2021-01-01 or createTime<"2021-01-01T00:00:00" to find Cloud resources that were created before 2021-01-01 00:00:00 UTC. 1609459200 is the epoch timestamp of 2021-01-01 00:00:00 UTC in seconds. * updateTime>1609459200 or updateTime>2021-01-01 or updateTime>"2021-01-01T00:00:00" to find Cloud resources that were updated after 2021-01-01 00:00:00 UTC. 1609459200 is the epoch timestamp of 2021-01-01 00:00:00 UTC in seconds. * Important to find Cloud resources that contain Important as a word in any of the searchable fields. * Impor* to find Cloud resources that contain Impor as a prefix of any word in any of the searchable fields. * Important location:(us-west1 OR global) to find Cloud resources that contain Important as a word in any of the searchable fields and are also located in the us-west1 region or the global location. |
| `--read-mask` | READ_MASK |  | A comma-separated list of fields specifying which fields to be returned in the results. Only "*" or combination of top level fields can be specified. Examples: "*", "name,location", "name,versionedResources". The read_mask paths must be valid field paths listed but not limited to the following (both snake_case and camelCase are supported): * name * asset_type or assetType * project * display_name or displayName * description * location * labels * tags * effective_tags or effectiveTags * network_tags or networkTags * kms_keys or kmsKeys * create_time or createTime * update_time or updateTime * state * additional_attributes or additionalAttributes * versioned_resources or versionedResources If read_mask is not specified, all fields except versionedResources will be returned. If only "*" is specified, all fields including versionedResources will be returned. |
| `--scope` | SCOPE |  | A scope can be a project, a folder, or an organization. The search is limited to the Cloud resources within this scope. The caller must be granted the cloudasset.assets.searchAllResources permission on the desired scope. If not specified, the configured project property (https://cloud.google.com//sdk/docs/configurations#setting_configuration_properties) will be used. To find the configured project, run: gcloud config get project. To change the setting, run: gcloud config set project PROJECT_ID. The allowed values are: * projects/{PROJECT_ID} (e.g., projects/foo-bar) * projects/{PROJECT_NUMBER} (e.g., projects/12345678) * folders/{FOLDER_NUMBER} (e.g., folders/1234567) * organizations/{ORGANIZATION_NUMBER} (e.g. organizations/123456) |


**Examples:**
```bash
To search all Cloud resources whose full resource name contains xyz as a
prefix of any word, within organizations/123456, ensure the caller has been
granted the cloudasset.assets.searchAllResources permission on the
organization and run:

    $ gcloud asset search-all-resources --scope='organizations/123456' \
        --query='name:xyz*'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/asset/search-all-resources)

---
# gcloud storage buckets

manage Cloud Storage buckets

### `gcloud storage buckets add-iam-policy-binding`

Add an IAM policy binding to a bucket

Add an IAM policy binding to a bucket. For more information, see Cloud
Identity and Access Management
(https://cloud.google.com/storage/docs/access-control/iam).

**Synopsis:**
```
gcloud storage buckets add-iam-policy-binding URL --member=PRINCIPAL
    --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URL
   URL of bucket to add IAM policy binding to.
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
To grant a single role to a single principal for BUCKET:

    $ gcloud storage buckets add-iam-policy-binding gs://BUCKET \
        --member=user:john.doe@example.com \
        --role=roles/storage.objectCreator

To make objects in BUCKET publicly readable:

    $ gcloud storage buckets add-iam-policy-binding gs://BUCKET \
        --member=allUsers --role=roles/storage.objectViewer

To specify a custom role for a principal on BUCKET:

    $ gcloud storage buckets add-iam-policy-binding gs://BUCKET \
        --member=user:john.doe@example.com --role=roles/customRoleName
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/buckets/add-iam-policy-binding)

---
### `gcloud storage buckets create`

Create buckets for storing objects

Create new buckets.

**Synopsis:**
```
gcloud storage buckets create URL [URL ...]
    [--additional-headers=HEADER=VALUE]
    [--default-encryption-key=DEFAULT_ENCRYPTION_KEY,
      -k DEFAULT_ENCRYPTION_KEY]
    [--default-storage-class=DEFAULT_STORAGE_CLASS,
      -c DEFAULT_STORAGE_CLASS, -s DEFAULT_STORAGE_CLASS]
    [--enable-hierarchical-namespace] [--enable-per-object-retention]
    [--ip-filter-file=IP_FILTER_FILE] [--lifecycle-file=LIFECYCLE_FILE]
    [--location=LOCATION, -l LOCATION]
    [--[no-]pap, --[no-]public-access-prevention]
    [--placement=[REGION,...]]
    [--recovery-point-objective=SETTING, --rpo=SETTING]
    [--retention-period=RETENTION_PERIOD]
    [--soft-delete-duration=SOFT_DELETE_DURATION]
    [--[no-]uniform-bucket-level-access, -b]
    [--autoclass-terminal-storage-class=AUTOCLASS_TERMINAL_STORAGE_CLASS
      --[no-]enable-autoclass] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URL [URL ...]
   The URLs of the buckets to create.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-headers` | HEADER=VALUE |  | Includes arbitrary headers in storage API calls. Accepts a comma separated list of key=value pairs, e.g. header1=value1,header2=value2. Overrides the default storage/additional_headers property value for this command invocation. |
| `--default-encryption-key` | DEFAULT_ENCRYPTION_KEY, -k DEFAULT_ENCRYPTION_KEY |  | Set the default KMS key using the full path to the key, which has the following form: projects/[project-id]/locations/[location]/keyRings/[key-ring]/cryptoKeys/[my-key]. |
| `--default-storage-class` | DEFAULT_STORAGE_CLASS, -c DEFAULT_STORAGE_CLASS, -s DEFAULT_STORAGE_CLASS |  | Default storage class (https://cloud.google.com/storage/docs/storage-classes) for the bucket. If not specified, the default storage class used by Cloud Storage is "Standard". |
| `--enable-hierarchical-namespace` |  |  | Enable hierarchical namespace for the bucket. To use this flag, you must also use --uniform-bucket-level-access |
| `--enable-per-object-retention` |  |  | Enables each object in the bucket to have its own retention settings, which prevents deletion until stored for a specific length of time. |
| `--ip-filter-file` | IP_FILTER_FILE |  | Sets the IP filter for the bucket. The IP filter is a list of ip ranges that are allowed to access the bucket. For example, The following JSON document shows the IP filter configuration with mode enabled and list of public network sources and vpc network sources: { "mode": "Enabled", "publicNetworkSource": { "allowedIpCidrRanges": ["0.0.0.0/0"] }, "vpcNetworkSources": [ { "network": "projects/PROJECT_NAME/global/networks/NETWORK_NAME", "allowedIpCidrRanges": ["0.0.0.0/0"] }, ] } For more information about supported configurations, see Cloud Storage bucket IP filtering configurations (https://cloud.google.com/storage/docs/create-ip-filter#ip-filtering-configurations) |
| `--lifecycle-file` | LIFECYCLE_FILE |  | Sets the lifecycle management configuration on a bucket. For example, The following lifecycle management configuration JSON document specifies that all objects in this bucket that are more than 365 days old are deleted automatically: { "rule": [ { "action": {"type": "Delete"}, "condition": {"age": 365} } ] } |
| `--location` | LOCATION, -l LOCATION |  | Location (https://cloud.google.com/storage/docs/locations) for the bucket. If not specified, the location used by Cloud Storage is us. A bucket's location cannot be changed after creation. |
| `--[no-]pap, --[no-]public-access-prevention` |  |  | Sets public access prevention to "enforced". For details on how exactly public access is blocked, see: http://cloud.google.com/storage/docs/public-access-prevention. Use --public-access-prevention to enable and --no-public-access-prevention to disable. |
| `--placement` | [REGION,...] |  | A comma-separated list of regions that form the custom dual-region (https://cloud.google.com/storage/docs/locations#location-dr). Only regions within the same continent are or will ever be valid. Invalid location pairs (such as mixed-continent, or with unsupported regions) will return an error. |
| `--recovery-point-objective` | one of: ASYNC_TURBO, DEFAULT |  | Sets the recovery point objective (https://cloud.google.com/architecture/dr-scenarios-planning-guide#basics_of_dr_planning) of a bucket. This flag can only be used with multi-region and dual-region buckets. DEFAULT option is valid for multi-region and dual-regions buckets. ASYNC_TURBO option is only valid for dual-region buckets. If unspecified when the bucket is created, it defaults to DEFAULT for dual-region and multi-region buckets. For more information, see replication in Cloud Storage (https://cloud.google.com/storage/docs/availability-durability#cross-region-redundancy). SETTING must be one of: ASYNC_TURBO, DEFAULT. |
| `--retention-period` | RETENTION_PERIOD |  | Minimum retention period (https://cloud.google.com/storage/docs/bucket-lock#retention-periods) for objects stored in the bucket, for example --retention-period=P1Y1M1DT5S. Objects added to the bucket cannot be deleted until they've been stored for the specified length of time. Default is no retention period. Only available for Cloud Storage using the JSON API. |
| `--soft-delete-duration` | SOFT_DELETE_DURATION |  | Duration to retain soft-deleted objects. For example, "2w1d" is two weeks and one day. See gcloud topic datetimes for more information on the duration format. Setting 0 will disable soft delete policy on the bucket. Default is 7 days. |
| `--[no-]uniform-bucket-level-access, -b` |  |  | Turns on uniform bucket-level access setting. Default is False. Use --uniform-bucket-level-access to enable and --no-uniform-bucket-level-access to disable. |


**Examples:**
```bash
The following command creates 2 Cloud Storage buckets, one named my-bucket
and a second bucket named my-other-bucket:

    $ gcloud storage buckets create gs://my-bucket gs://my-other-bucket

The following command creates a bucket with the nearline default storage
class (https://cloud.google.com/storage/docs/storage-classes) in the asia
location (https://cloud.google.com/storage/docs/locations):

    $ gcloud storage buckets create gs://my-bucket \
        --default-storage-class=nearline --location=asia
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/buckets/create)

---
### `gcloud storage buckets delete`

Deletes Cloud Storage buckets

Deletes one or more Cloud Storage buckets.

**Synopsis:**
```
gcloud storage buckets delete URLS [URLS ...]
    [--additional-headers=HEADER=VALUE] [--continue-on-error, -c]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URLS [URLS ...]
   Specifies the URLs of the buckets to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-headers` | HEADER=VALUE |  | Includes arbitrary headers in storage API calls. Accepts a comma separated list of key=value pairs, e.g. header1=value1,header2=value2. Overrides the default storage/additional_headers property value for this command invocation. |
| `--continue-on-error, -c` |  |  | If any operations are unsuccessful, the command will exit with a non-zero exit status after completing the remaining operations. This flag takes effect only in sequential execution mode (i.e. processor and thread count are set to 1). Parallelism is default. |


**Examples:**
```bash
Delete a Google Cloud Storage bucket named "my-bucket":

    $ gcloud storage buckets delete gs://my-bucket

Delete two buckets:

    $ gcloud storage buckets delete gs://my-bucket gs://my-other-bucket
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/buckets/delete)

---
### `gcloud storage buckets describe`

Describes Cloud Storage buckets

Describe a Cloud Storage bucket.

**Synopsis:**
```
gcloud storage buckets describe URL [--additional-headers=HEADER=VALUE]
    [--raw] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URL
   Specifies URL of bucket to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-headers` | HEADER=VALUE |  | Includes arbitrary headers in storage API calls. Accepts a comma separated list of key=value pairs, e.g. header1=value1,header2=value2. Overrides the default storage/additional_headers property value for this command invocation. |
| `--raw` |  |  | Shows metadata in the format returned by the API instead of standardizing it. |


**Examples:**
```bash
Describe a Google Cloud Storage bucket named "my-bucket":

    $ gcloud storage buckets describe gs://my-bucket

Describe bucket with JSON formatting, only returning the "name" key:

    $ gcloud storage buckets describe gs://my-bucket \
        --format="json(name)"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/buckets/describe)

---
### `gcloud storage buckets get-iam-policy`

Get the IAM policy for a bucket

Get the IAM policy for a bucket. For more information, see Cloud Identity
and Access Management
(https://cloud.google.com/storage/docs/access-control/iam).

**Synopsis:**
```
gcloud storage buckets get-iam-policy URL [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URL
   Request IAM policy for this bucket.
```

**Examples:**
```bash
To get the IAM policy for BUCKET:

    $ gcloud storage buckets get-iam-policy gs://BUCKET

To output the IAM policy for BUCKET to a file:

    $ gcloud storage buckets get-iam-policy gs://BUCKET > policy.txt
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/buckets/get-iam-policy)

---
### `gcloud storage buckets list`

Lists Cloud Storage buckets

List Cloud Storage buckets.

**Synopsis:**
```
gcloud storage buckets list [URLS ...] [--additional-headers=HEADER=VALUE]
    [--raw] [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[URLS ...]
   Specifies URL of buckets to List.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-headers` | HEADER=VALUE |  | Includes arbitrary headers in storage API calls. Accepts a comma separated list of key=value pairs, e.g. header1=value1,header2=value2. Overrides the default storage/additional_headers property value for this command invocation. |
| `--raw` |  |  | Shows metadata in the format returned by the API instead of standardizing it. |


**Examples:**
```bash
List all Google Cloud Storage buckets in default project:

    $ gcloud storage buckets list

List buckets beginning with ``b'':

    $ gcloud storage buckets list gs://b*

List buckets with JSON formatting, only returning the name key:

    $ gcloud storage buckets list --format="json(name)"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/buckets/list)

---
### `gcloud storage buckets relocate`

Relocates bucket between different locations

Relocates a bucket between different locations.

**Synopsis:**
```
gcloud storage buckets relocate
    ([URL --location=LOCATION : --placement=[REGION,...]
      --dry-run] [--operation=OPERATION --finalize : --ttl=TTL])
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Exactly one of these must be specified:

  Arguments for initiating the bucket relocate operation.

    URL
       The URL of the bucket to relocate.

       This positional argument must be specified if any of the other
       arguments in this group are specified.

    --location=LOCATION
       The final location
       (https://cloud.google.com/storage/docs/locations) where the bucket
       will be relocated to. If no location is provided, Cloud Storage
       will use the default location, which is us.

       This flag argument must be specified if any of the other arguments
       in this group are specified.

    --placement=[REGION,...]
       A comma-separated list of regions that form the custom dual-region
       (https://cloud.google.com/storage/docs/locations#location-dr). Only
       regions within the same continent are or will ever be valid.
       Invalid location pairs (such as mixed-continent, or with
       unsupported regions) will return an error.

    --dry-run
       Prints the operations that the relocate command would perform
       without actually performing relocation. This is helpful to identify
       any issues that need to be detected asynchronously.

  Arguments for advancing the relocation operation.

    --operation=OPERATION
       Specify the relocation operation name to advance the relocation
       operation.The relocation operation name must include the Cloud
       Storage bucket and operation ID.

       This flag argument must be specified if any of the other arguments
       in this group are specified.

    --finalize
       Schedules the write lock to occur. Once activated, no further
       writes will be allowed to the associated bucket. This helps
       minimize disruption to bucket usage. For certain types of
       moves(between Multi Region and Custom Dual Regions), finalize is
       not required.

       This flag argument must be specified if any of the other arguments
       in this group are specified.

    --ttl=TTL
       Time to live for the relocation operation. Defaults to 12h if not
       provided.
```

**Examples:**
```bash
To move a bucket (gs://my-bucket) to the us-central1 location, use the
following command:

    $ gcloud storage buckets relocate gs://my-bucket \
      --location=us-central1

To move a bucket to a custom dual-region, use the following command:

    $ gcloud storage buckets relocate gs://my-bucket --location=us \
      --placement=us-central1,us-east1

To validate the operation without actually moving the bucket, use the
following command:

    $ gcloud storage buckets relocate gs://my-bucket \
      --location=us-central1 --dry-run

To schedule a write lock for the move, with ttl for reverting the write
lock after 7h, if the relocation has not succeeded, use the following
command:

    $ gcloud storage buckets relocate \
      --operation=projects/_/buckets/my-bucket/operations/C894F35J \
      --finalize --ttl=7h
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/buckets/relocate)

---
### `gcloud storage buckets remove-iam-policy-binding`

Remove an IAM policy binding from a bucket

Removes a policy binding from the IAM policy of a bucket, given a bucket
URL and the binding. For more information, see Cloud Identity and Access
Management (https://cloud.google.com/storage/docs/access-control/iam).

**Synopsis:**
```
gcloud storage buckets remove-iam-policy-binding URL --member=PRINCIPAL
    --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URL
   URL of bucket to remove IAM policy binding from.
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
To remove an IAM policy binding from the role of
roles/storage.objectCreator for the user john.doe@example.com on BUCKET:

    $ gcloud storage buckets remove-iam-policy-binding gs://BUCKET \
        --member=user:john.doe@example.com \
        --role=roles/storage.objectCreator
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/buckets/remove-iam-policy-binding)

---
### `gcloud storage buckets set-iam-policy`

Set the IAM policy for a bucket

Set the IAM policy for a bucket. For more information, see Cloud Identity
and Access Management
(https://cloud.google.com/storage/docs/access-control/iam).

**Synopsis:**
```
gcloud storage buckets set-iam-policy URLS [URLS ...] POLICY_FILE
    [--continue-on-error, -c] [--etag=ETAG, -e ETAG] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URLS [URLS ...]
   URLs for buckets to apply the IAM policy to. Can include wildcards.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--continue-on-error, -c` |  |  | If any operations are unsuccessful, the command will exit with a non-zero exit status after completing the remaining operations. This flag takes effect only in sequential execution mode (i.e. processor and thread count are set to 1). Parallelism is default. |
| `--etag` | ETAG, -e ETAG |  | Custom etag to set on IAM policy. API will reject etags that do not match this value, making it useful as a precondition during concurrent operations. |


**Examples:**
```bash
To set the IAM policy in POLICY-FILE on BUCKET:

    $ gcloud storage buckets set-iam-policy gs://BUCKET POLICY-FILE

To set the IAM policy in POLICY-FILE on all buckets beginning with "b":

    $ gcloud storage buckets set-iam-policy gs://b* POLICY-FILE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/buckets/set-iam-policy)

---
### `gcloud storage buckets update`

Update bucket settings

Update the settings for a bucket.

**Synopsis:**
```
gcloud storage buckets update [URL ...] [--additional-headers=HEADER=VALUE]
    [--clear-soft-delete] [--continue-on-error, -c]
    [--[no-]default-event-based-hold]
    [--default-storage-class=DEFAULT_STORAGE_CLASS]
    [--lock-retention-period] [--read-paths-from-stdin, -I]
    [--recovery-point-objective=SETTING, --rpo=SETTING]
    [--[no-]requester-pays] [--soft-delete-duration=SOFT_DELETE_DURATION]
    [--[no-]uniform-bucket-level-access] [--[no-]versioning]
    [--acl-file=ACL_FILE --add-acl-grant=[ACL_GRANT,...]
      --canned-acl=PREDEFINED_ACL, --predefined-acl=PREDEFINED_ACL,
      -a PREDEFINED_ACL --remove-acl-grant=REMOVE_ACL_GRANT]
    [--add-default-object-acl-grant=[DEFAULT_OBJECT_ACL_GRANT,...]
      --default-object-acl-file=DEFAULT_OBJECT_ACL_FILE
      --predefined-default-object-acl=PREDEFINED_DEFAULT_OBJECT_ACL
      --remove-default-object-acl-grant=REMOVE_DEFAULT_OBJECT_ACL_GRANT]
    [--clear-cors | --cors-file=CORS_FILE]
    [--clear-default-encryption-key
      | --default-encryption-key=DEFAULT_ENCRYPTION_KEY]
    [--clear-ip-filter | --ip-filter-file=IP_FILTER_FILE]
    [--clear-labels | --labels-file=LABELS_FILE
      | --remove-labels=[LABEL_KEYS,...]
      --update-labels=[LABEL_KEYS_AND_VALUES,...]]
    [--clear-lifecycle | --lifecycle-file=LIFECYCLE_FILE]
    [--clear-log-bucket | --log-bucket=LOG_BUCKET]
    [--clear-log-object-prefix | --log-object-prefix=LOG_OBJECT_PREFIX]
    [--clear-pap, --clear-public-access-prevention
      | --[no-]pap, --[no-]public-access-prevention]
    [--clear-retention-period | --retention-period=RETENTION_PERIOD]
    [--clear-web-error-page | --web-error-page=WEB_ERROR_PAGE]
    [--clear-web-main-page-suffix
      | --web-main-page-suffix=WEB_MAIN_PAGE_SUFFIX]
    [--autoclass-terminal-storage-class=AUTOCLASS_TERMINAL_STORAGE_CLASS
      --[no-]enable-autoclass] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[URL ...]
   Specifies the URLs of the buckets to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-headers` | HEADER=VALUE |  | Includes arbitrary headers in storage API calls. Accepts a comma separated list of key=value pairs, e.g. header1=value1,header2=value2. Overrides the default storage/additional_headers property value for this command invocation. |
| `--clear-soft-delete` |  |  | Clears bucket soft delete settings. Does not affect objects already in soft-deleted state. |
| `--continue-on-error, -c` |  |  | If any operations are unsuccessful, the command will exit with a non-zero exit status after completing the remaining operations. This flag takes effect only in sequential execution mode (i.e. processor and thread count are set to 1). Parallelism is default. |
| `--[no-]default-event-based-hold` |  |  | Sets the default value for an event-based hold on the bucket. By setting the default event-based hold on a bucket, newly-created objects inherit that value as their event-based hold (it is not applied retroactively). Use --default-event-based-hold to enable and --no-default-event-based-hold to disable. |
| `--default-storage-class` | DEFAULT_STORAGE_CLASS |  | Sets the default storage class for the bucket. |
| `--lock-retention-period` |  |  | Locks an unlocked retention policy on the buckets. Caution: A locked retention policy cannot be removed from a bucket or reduced in duration. Once locked, deleting the bucket is the only way to "remove" a retention policy. |
| `--read-paths-from-stdin, -I` |  |  | Read the list of URLs from stdin. |
| `--recovery-point-objective` | one of: ASYNC_TURBO, DEFAULT |  | Sets the recovery point objective (https://cloud.google.com/architecture/dr-scenarios-planning-guide#basics_of_dr_planning) of a bucket. This flag can only be used with multi-region and dual-region buckets. DEFAULT option is valid for multi-region and dual-regions buckets. ASYNC_TURBO option is only valid for dual-region buckets. If unspecified when the bucket is created, it defaults to DEFAULT for dual-region and multi-region buckets. For more information, see replication in Cloud Storage (https://cloud.google.com/storage/docs/availability-durability#cross-region-redundancy). SETTING must be one of: ASYNC_TURBO, DEFAULT. |
| `--[no-]requester-pays` |  |  | Allows you to configure a Cloud Storage bucket so that the requester pays all costs related to accessing the bucket and its objects. Use --requester-pays to enable and --no-requester-pays to disable. |
| `--soft-delete-duration` | SOFT_DELETE_DURATION |  | Duration to retain soft-deleted objects. For example, "2w1d" is two weeks and one day. |
| `--[no-]uniform-bucket-level-access` |  |  | Enables or disables uniform bucket-level access (https://cloud.google.com/storage/docs/bucket-policy-only) for the buckets. Use --uniform-bucket-level-access to enable and --no-uniform-bucket-level-access to disable. |
| `--[no-]versioning` |  |  | Allows you to configure a Cloud Storage bucket to keep old versions of objects. Use --versioning to enable and --no-versioning to disable. |
| `--acl-file` | ACL_FILE |  | Path to a local JSON or YAML formatted file containing a valid policy. See the ObjectAccessControls resource (https://cloud.google.com/storage/docs/json_api/v1/objectAccessControls) for a representation of JSON formatted files. The output of gcloud storage [buckets\|objects] describe --format="multi(acl:format=json)" is a valid file and can be edited for more fine-grained control. |
| `--add-acl-grant` | [ACL_GRANT,...] |  | Key-value pairs mirroring the JSON accepted by your cloud provider. For example, for Cloud Storage,--add-acl-grant=entity=user-tim@gmail.com,role=OWNER |
| `--canned-acl` | PREDEFINED_ACL, --predefined-acl=PREDEFINED_ACL, -a PREDEFINED_ACL |  | Applies predefined, or "canned," ACLs to a resource. See docs for a list of predefined ACL constants: https://cloud.google.com/storage/docs/access-control/lists#predefined-acl |
| `--remove-acl-grant` | REMOVE_ACL_GRANT |  | Key-value pairs mirroring the JSON accepted by your cloud provider. For example, for Cloud Storage, --remove-acl-grant=ENTITY, where ENTITY has a valid ACL entity format, such as user-tim@gmail.com, group-admins, allUsers, etc. |
| `--add-default-object-acl-grant` | [DEFAULT_OBJECT_ACL_GRANT,...] |  | Adds default object ACL grant. See --add-acl-grant help text for more details. |
| `--default-object-acl-file` | DEFAULT_OBJECT_ACL_FILE |  | Sets the default object ACL from file for the bucket. |
| `--predefined-default-object-acl` | PREDEFINED_DEFAULT_OBJECT_ACL |  | Apply a predefined set of default object access controls tobuckets |
| `--remove-default-object-acl-grant` | REMOVE_DEFAULT_OBJECT_ACL_GRANT |  | Removes default object ACL grant. See --remove-acl-grant help text for more details. |


**Examples:**
```bash
The following command updates the default storage class of a Cloud Storage
bucket named "my-bucket" to NEARLINE and sets requester pays to true:

    $ gcloud storage buckets update gs://my-bucket \
        --default-storage-class=NEARLINE --requester-pays

The following command updates the retention period of a Cloud Storage
bucket named "my-bucket" to one year and thirty-six minutes:

    $ gcloud storage buckets update gs://my-bucket \
        --retention-period=1y36m

The following command clears the retention period of a bucket:

    $ gcloud storage buckets update gs://my-bucket \
        --clear-retention-period
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/buckets/update)

---

## `gcloud storage buckets anywhere-caches` — manage Cloud Storage Anywhere Caches
### `gcloud storage buckets anywhere-caches create`

Create Anywhere Cache instances for a bucket

Create Anywhere Cache instances. Only one cache instance per zone can be
created for each bucket.

**Synopsis:**
```
gcloud storage buckets anywhere-caches create URL ZONE [ZONE ...]
    [--admission-policy=ADMISSION_POLICY] [--ttl=TTL]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URL
   Specifies the URL of the bucket where the Anywhere Cache should be
   created.

ZONE [ZONE ...]
   Specifies the name of the zonal locations where the Anywhere Cache
   should be created.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--admission-policy` | one of: ADMIT_ON_FIRST_MISS, ADMIT_ON_SECOND_MISS |  | The cache admission policy decides for each cache miss, whether to insert the missed block or not. ADMISSION_POLICY must be one of: ADMIT_ON_FIRST_MISS, ADMIT_ON_SECOND_MISS. |
| `--ttl` | TTL |  | Cache entry time-to-live. Default to 24h if not provided. |


**Examples:**
```bash
The following command creates an anywhere cache instance for bucket in
asia-south2-b zone:

    $ gcloud storage buckets anywhere-caches create gs://my-bucket \
        asia-south2-b

The following command creates anywhere cache instances for bucket in
asia-south2-b, and asia-east1-a zone:

    $ gcloud storage buckets anywhere-caches create gs://my-bucket \
        asia-south2-b asia-east1-a

The following command creates an anywhere cache instance for bucket in
asia-south2-b zone, with ttl for cache entry as 6 hours, and admission
policy as ADMIT_ON_SECOND_MISS:

    $ gcloud storage buckets anywhere-caches create gs://my-bucket \
        asia-south2-b --ttl=6h --admission-policy='ADMIT_ON_SECOND_MISS'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/buckets/anywhere-caches/create)

---
### `gcloud storage buckets anywhere-caches describe`

Returns details of Anywhere Cache instance of a bucket

Desribes a single Anywhere Cache instance if it exists.

**Synopsis:**
```
gcloud storage buckets anywhere-caches describe ID [--raw]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ID
   Identifier for a Anywhere Cache instance. It is a combination of
   bucket_name/anywhere_cache_id, For example : test-bucket/my-cache-id.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--raw` |  |  | Shows metadata in the format returned by the API instead of standardizing it. |


**Examples:**
```bash
The following command describes the anywhere cache instance of bucket
my-bucket having anywhere_cache_id my-cache-id:

    $ gcloud storage buckets anywhere-caches describe \
        my-bucket/my-cache-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/buckets/anywhere-caches/describe)

---
### `gcloud storage buckets anywhere-caches disable`

Disable Anywhere Cache instances

Disables one or more Anywhere Cache instances.

The cache instance will be set to DISABLED state. The existing entries can
be read from the cache but new entries will not be written to the cache.
The L4 SSD cache would not be deleted by the cache manager until the min
TTL (1h) has been reached (cache instance is kept for at least 1h). Google
Cloud Storage defines the min TTL which is applied to all cache instances.
Cach disablement could be canceled by using anywhere-caches resume command
before the instance is deleted.

**Synopsis:**
```
gcloud storage buckets anywhere-caches disable ID [ID ...]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ID [ID ...]
   Identifiers for a Anywhere Cache instance. They are combination of
   bucket_name/anywhere_cache_id. For example : test-bucket/my-cache-id.
```

**Examples:**
```bash
The following command disables the anywhere cache instance of bucket
my-bucket having anywhere_cache_id my-cache-id:

    $ gcloud storage buckets anywhere-caches disable \
        my-bucket/my-cache-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/buckets/anywhere-caches/disable)

---
### `gcloud storage buckets anywhere-caches list`

List all Anywhere Cache instances of a bucket

List all cache instances of this bucket.

**Synopsis:**
```
gcloud storage buckets anywhere-caches list URL [--raw]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URL
   Specifies the URL of the bucket for which anywhere cache instances
   should be listed.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--raw` |  |  | Shows metadata in the format returned by the API instead of standardizing it. |


**Examples:**
```bash
The following command lists all anywhere cache instances of bucket
gs://my-bucket:

    $ gcloud storage buckets anywhere-caches list gs://my-bucket
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/buckets/anywhere-caches/list)

---
### `gcloud storage buckets anywhere-caches pause`

Pause Anywhere Cache instances

The pause operation can be used to stop the data ingestion of a cache
instance in RUNNING state (read-only cache) until the Resume is invoked.

**Synopsis:**
```
gcloud storage buckets anywhere-caches pause ID [ID ...]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ID [ID ...]
   Identifiers for a Anywhere Cache instance. They are combination of
   bucket_name/anywhere_cache_id. For example : test-bucket/my-cache-id.
```

**Examples:**
```bash
The following command pause the anywhere cache instance of bucket my-bucket
having anywhere_cache_id my-cache-id:

    $ gcloud storage buckets anywhere-caches pause my-bucket/my-cache-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/buckets/anywhere-caches/pause)

---
### `gcloud storage buckets anywhere-caches resume`

Resume Anywhere Cache instances

Resume operation could be used to revert the Paused and Disabled state.
Once a paused/disabled cache is resumed, the cache will be set to
RUNNING/CREATING state: 1. RUNNING if the cache is active. 2. CREATING if
the cache is pending creation.

**Synopsis:**
```
gcloud storage buckets anywhere-caches resume ID [ID ...]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ID [ID ...]
   Identifiers for a Anywhere Cache instance. They are combination of
   bucket_name/anywhere_cache_id. For example : test-bucket/my-cache-id.
```

**Examples:**
```bash
The following command resume the anywhere cache instance of bucket
my-bucket having anywhere_cache_id my-cache-id:

    $ gcloud storage buckets anywhere-caches resume my-bucket/my-cache-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/buckets/anywhere-caches/resume)

---
### `gcloud storage buckets anywhere-caches update`

Update Anywhere Cache instances

Update one or more Anywhere Cache instances. A cache instance can be
updated if its state is created or pending creation.

**Synopsis:**
```
gcloud storage buckets anywhere-caches update ID [ID ...]
    [--admission-policy=ADMISSION_POLICY] [--ttl=TTL]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ID [ID ...]
   Identifiers for a Anywhere Cache Instance.They are combination of
   bucket_name/anywhere_cache_id. For example : test-bucket/my-cache-id.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--admission-policy` | one of: ADMIT_ON_FIRST_MISS, ADMIT_ON_SECOND_MISS |  | The cache admission policy decides for each cache miss, whether to insert the missed block or not. ADMISSION_POLICY must be one of: ADMIT_ON_FIRST_MISS, ADMIT_ON_SECOND_MISS. |
| `--ttl` | TTL |  | Cache entry time-to-live. Default to 24h if not provided. |


**Examples:**
```bash
The following command updates cache entry's ttl, and admisson policy of
anywhere cache instance in bucket my-bucket having anywhere_cache_id
my-cache-id:

    $ gcloud storage buckets anywhere-caches update \
        my-bucket/my-cache-id --ttl=6h \
        --admission-policy='ADMIT_ON_SECOND_MISS'

The following command updates cache entry's ttl of anywhere cache instances
in bucket bucket-1 and bucket-2 having anywhere_cache_id my-cache-id-1, and
my-cache-id-2 respectively:

    $ gcloud storage buckets anywhere-caches update \
        bucket-1/my-cache-id-1 bucket-2/my-cache-id-2 --ttl=6h
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/buckets/anywhere-caches/update)

---

## `gcloud storage buckets notifications` — manage Cloud Storage bucket notifications
### `gcloud storage buckets notifications create`

Create a notification configuration on a bucket

gcloud storage buckets notifications create creates a notification
configuration on a bucket, establishing a flow of event notifications from
Cloud Storage to a Cloud Pub/Sub topic. As part of creating this flow, it
also verifies that the destination Cloud Pub/Sub topic exists, creating it
if necessary, and verifies that the Cloud Storage bucket has permission to
publish events to that topic, granting the permission if necessary.

If a destination Cloud Pub/Sub topic is not specified with the -t flag,
Cloud Storage chooses a topic name in the default project whose ID is the
same as the bucket name. For example, if the default project ID specified
is default-project and the bucket being configured is gs://example-bucket,
the create command uses the Cloud Pub/Sub topic
projects/default-project/topics/example-bucket.

In order to enable notifications, your project's Cloud Storage service
agent (https://cloud.google.com/storage/docs/projects#service-accounts)
must have the IAM permission "pubsub.topics.publish". This command checks
to see if the destination Cloud Pub/Sub topic grants the service agent this
permission. If not, the create command attempts to grant it.

A bucket can have up to 100 total notification configurations and up to 10
notification configurations set to trigger for a specific event.

**Synopsis:**
```
gcloud storage buckets notifications create URL
    [--custom-attributes=[KEY=VALUE,...], -m [KEY=VALUE,...]]
    [--event-types=[NOTIFICATION_EVENT_TYPE,...],
      -e [NOTIFICATION_EVENT_TYPE,...]]
    [--object-prefix=OBJECT_PREFIX, -p OBJECT_PREFIX]
    [--payload-format=PAYLOAD_FORMAT, -f PAYLOAD_FORMAT; default="json"]
    [--skip-topic-setup, -s] [--topic=TOPIC, -t TOPIC]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URL
   URL of the bucket to create the notification configuration on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--custom-attributes` | [KEY=VALUE,...], -m [KEY=VALUE,...] |  | Specifies key:value attributes that are appended to the set of attributes sent to Cloud Pub/Sub for all events associated with this notification configuration. |
| `--event-types` | one of: OBJECT_ARCHIVE, OBJECT_DELETE, OBJECT_FINALIZE, OBJECT_METADATA_UPDATE |  | Specify event type filters for this notification configuration. Cloud Storage will send notifications of only these types. By default, Cloud Storage sends notifications for all event types. * OBJECT_FINALIZE: An object has been created. * OBJECT_METADATA_UPDATE: The metadata of an object has changed. * OBJECT_DELETE: An object has been permanently deleted. * OBJECT_ARCHIVE: A live version of an object has become a noncurrent version. NOTIFICATION_EVENT_TYPE must be one of: OBJECT_ARCHIVE, OBJECT_DELETE, OBJECT_FINALIZE, OBJECT_METADATA_UPDATE. |
| `--object-prefix` | OBJECT_PREFIX, -p OBJECT_PREFIX |  | Specifies a prefix path for this notification configuration. Cloud Storage will send notifications for only objects in the bucket whose names begin with the prefix. |
| `--payload-format` | one of: json, none | json | Specifies the payload format of notification messages. Notification details are available in the message attributes. 'none' sends no payload. PAYLOAD_FORMAT must be one of: json, none. |
| `--skip-topic-setup, -s` |  |  | Skips creation and permission assignment of the Cloud Pub/Sub topic. This is useful if the caller does not have permission to access the topic in question, or if the topic already exists and has the appropriate publish permission assigned. |
| `--topic` | TOPIC, -t TOPIC |  | Specifies the Cloud Pub/Sub topic to send notifications to. If not specified, this command chooses a topic whose project is your default project and whose ID is the same as the Cloud Storage bucket name. |


**Examples:**
```bash
Send notifications of all changes to the bucket example-bucket to the Cloud
Pub/Sub topic projects/default-project/topics/example-bucket:

    $ gcloud storage buckets notifications create gs://example-bucket

The same as the above but sends no notification payload:

    $ gcloud storage buckets notifications create \
        --payload-format=none gs://example-bucket

Include custom metadata in notification payloads:

    $ gcloud storage buckets notifications create \
        --custom-attributes=key1:value1,key2:value2 gs://example-bucket

Create a notification configuration that only sends an event when a new
object has been created or an object is deleted:

    $ gcloud storage buckets notifications create \
        --event-types=OBJECT_FINALIZE,OBJECT_DELETE gs://example-bucket

Create a topic and notification configuration that sends events only when
they affect objects with the prefix photos/:

    $ gcloud storage buckets notifications create \
        --object-prefix=photos/ gs://example-bucket

Specifies the destination topic ID files-to-process in the default project:

    $ gcloud storage buckets notifications create \
        --topic=files-to-process gs://example-bucket

The same as above but specifies a Cloud Pub/Sub topic belonging to the
specific cloud project example-project:

    $ gcloud storage buckets notifications create \
        --topic=projects/example-project/topics/files-to-process \
        gs://example-bucket

Skip creating a topic when creating the notification configuraiton:

    $ gcloud storage buckets notifications create \
        --skip-topic-setup gs://example-bucket
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/buckets/notifications/create)

---
### `gcloud storage buckets notifications delete`

Delete notification configurations from a bucket

gcloud storage buckets notifications delete deletes notification
configurations from a bucket. If a notification configuration name is
passed as a parameter, that configuration alone is deleted. If a bucket
name is passed, all notification configurations associated with the bucket
are deleted.

Cloud Pub/Sub topics associated with this notification configuration are
not deleted by this command. Those must be deleted separately, for example
with the command "gcloud pubsub topics delete".

**Synopsis:**
```
gcloud storage buckets notifications delete URLS [URLS ...]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URLS [URLS ...]
   Specifies notification configuration names or buckets.
```

**Examples:**
```bash
Delete a single notification configuration (with ID 3) in the bucket
example-bucket:

    $ gcloud storage buckets notifications delete \
        projects/_/buckets/example-bucket/notificationConfigs/3

Delete all notification configurations in the bucket example-bucket:

    $ gcloud storage buckets notifications delete gs://example-bucket
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/buckets/notifications/delete)

---
### `gcloud storage buckets notifications describe`

Show metadata for a notification configuration

gcloud storage buckets notifications describe prints populated metadata for
a notification configuration.

**Synopsis:**
```
gcloud storage buckets notifications describe URL [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URL
   The url of the notification configuration
```

**Examples:**
```bash
Describe a single notification configuration (with ID 3) in the bucket
example-bucket:

    $ gcloud storage buckets notifications describe \
        projects/_/buckets/example-bucket/notificationConfigs/3
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/buckets/notifications/describe)

---
### `gcloud storage buckets notifications list`

List the notification configurations belonging to a given bucket

gcloud storage buckets notifications list provides a list of notification
configurations belonging to a given bucket. The listed name of each
configuration can be used with the delete sub-command to delete that
specific notification config.

**Synopsis:**
```
gcloud storage buckets notifications list [URLS ...] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[URLS ...]
   Google Cloud Storage bucket paths. The path must begin with gs:// and
   may contain wildcard characters.
```

**Examples:**
```bash
Fetch the list of notification configs for the bucket example-bucket:

    $ gcloud storage buckets notifications list gs://example-bucket

Fetch the notification configs in all buckets matching a wildcard:

    $ gcloud storage buckets notifications list gs://example-*

Fetch all of the notification configs for buckets in the default project:

    $ gcloud storage buckets notifications list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/buckets/notifications/list)

---
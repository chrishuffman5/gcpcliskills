# gcloud transfer jobs

manage transfer jobs

### `gcloud transfer jobs create`

Create a Transfer Service transfer job

Create a Transfer Service transfer job, allowing you to transfer data to
Google Cloud Storage on a one-time or recurring basis.

**Synopsis:**
```
gcloud transfer jobs create SOURCE DESTINATION
    [--name=NAME --description=DESCRIPTION
      --source-creds-file=SOURCE_CREDS_FILE
      --source-agent-pool=SOURCE_AGENT_POOL
      --destination-agent-pool=DESTINATION_AGENT_POOL
      --intermediate-storage-path=INTERMEDIATE_STORAGE_PATH
      --manifest-file=MANIFEST_FILE] [--replication]
    [--event-stream-name=EVENT_STREAM_NAME
      --event-stream-starts=EVENT_STREAM_STARTS
      --event-stream-expires=EVENT_STREAM_EXPIRES]
    [--do-not-run --schedule-starts=SCHEDULE_STARTS
      --schedule-repeats-every=SCHEDULE_REPEATS_EVERY
      --schedule-repeats-until=SCHEDULE_REPEATS_UNTIL]
    [--include-prefixes=[INCLUDED_PREFIXES,...]
      --exclude-prefixes=[EXCLUDED_PREFIXES,...] --match-glob=MATCH_GLOB
      --include-modified-before-absolute=INCLUDE_MODIFIED_BEFORE_ABSOLUTE
      --include-modified-after-absolute=INCLUDE_MODIFIED_AFTER_ABSOLUTE
      --include-modified-before-relative=INCLUDE_MODIFIED_BEFORE_RELATIVE
      --include-modified-after-relative=INCLUDE_MODIFIED_AFTER_RELATIVE]
    [--overwrite-when=OVERWRITE_WHEN --delete-from=DELETE_FROM
      --preserve-metadata=[METADATA_FIELDS,...]
      --custom-storage-class=CUSTOM_STORAGE_CLASS]
    [--notification-pubsub-topic=NOTIFICATION_PUBSUB_TOPIC
      --notification-event-types=[EVENT_TYPES,...]
      --notification-payload-format=NOTIFICATION_PAYLOAD_FORMAT]
    [--[no-]enable-posix-transfer-logs --log-actions=[LOG_ACTIONS,...]
      --log-action-states=[LOG_ACTION_STATES,...]]
    [--source-endpoint=SOURCE_ENDPOINT
      --source-signing-region=SOURCE_SIGNING_REGION
      --source-auth-method=SOURCE_AUTH_METHOD
      --source-list-api=SOURCE_LIST_API
      --source-network-protocol=SOURCE_NETWORK_PROTOCOL
      --source-request-model=SOURCE_REQUEST_MODEL
      --s3-cloudfront-domain=S3_CLOUDFRONT_DOMAIN] [--no-async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SOURCE
   The source of your data. Available sources and formatting information:

   Public clouds -
   * [Google Cloud Storage] gs://example-bucket/example-folder/
   * [Amazon S3] s3://examplebucket/example-folder
   * [Azure Blob Storage or Data Lake Storage]
     http://examplestorageaccount.blob.core.windows.net/examplecontainer/examplefolder

   POSIX filesystem - Specify the posix:// scheme followed by the absolute
   path to the desired directory, starting from the root of the host
   machine (denoted by a leading slash). For example:
   * posix:///path/directory/

   A file transfer agent must be installed on the POSIX filesystem, and
   you need an agent pool flag on this jobs command to activate the agent.

   Hadoop Distributed File System (HDFS) - Specify the hdfs:// scheme
   followed by the absolute path to the desired directory, starting from
   the root of the file system (denoted by a leading slash). For example:
   * hdfs:///path/directory/

   Namenode details should not be included in the path specification, as
   they are required separately during the agent installation process.

   A file transfer agent must be installed, and you need an agent pool
   flag on this jobs command to activate the agent.

   Publicly-accessible objects - Specify the URL of a TSV file containing
   a list of URLs of publicly-accessible objects. For example:
   * http://example.com/tsvfile

DESTINATION
   The destination of your transferred data. Available destinations and
   formatting information:

   Google Cloud Storage - Specify the gs:// scheme; name of the bucket;
   and, if transferring to a folder, the path to the folder. For example:
   * gs://example-bucket/example-folder/

   POSIX filesystem - Specify the posix:// scheme followed by the absolute
   path to the desired directory, starting from the root of the host
   machine (denoted by a leading slash). For example:
   * posix:///path/directory/

   A file transfer agent must be installed on the POSIX filesystem, and
   you need an agent pool flag on this jobs command to activate the agent.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--name` | NAME |  | _[JOB INFORMATION]_ A unique identifier for the job. Referring to your source and destination is recommended. If left blank, the name is auto-generated upon submission of the job. |
| `--description` | DESCRIPTION |  | _[JOB INFORMATION]_ An optional description to help identify the job using details that don't fit in its name. |
| `--source-creds-file` | SOURCE_CREDS_FILE |  | _[JOB INFORMATION]_ Path to a local file on your machine that includes credentials for an Amazon S3 or Azure Blob Storage source (not required for Google Cloud Storage sources). If not specified for an S3 source, gcloud will check your system for an AWS config file. However, this flag must be specified to use AWS's "role_arn" auth service. For formatting, see: S3: https://cloud.google.com/storage-transfer/docs/reference/rest/v1/TransferSpec#AwsAccessKey Note: Be sure to put quotations around the JSON value strings. Azure: https://cloud.google.com/storage-transfer/docs/reference/rest/v1/TransferSpec#AzureCredentials |
| `--source-agent-pool` | SOURCE_AGENT_POOL |  | _[JOB INFORMATION]_ If using a POSIX filesystem source, specify the ID of the agent pool associated with source filesystem. |
| `--destination-agent-pool` | DESTINATION_AGENT_POOL |  | _[JOB INFORMATION]_ If using a POSIX filesystem destination, specify the ID of the agent pool associated with destination filesystem. |
| `--intermediate-storage-path` | INTERMEDIATE_STORAGE_PATH |  | _[JOB INFORMATION]_ If transferring between filesystems, specify the path to a folder in a Google Cloud Storage bucket (gs://example-bucket/example-folder) to use as intermediary storage. Recommended: Use an empty folder reserved for this transfer job to ensure transferred data doesn't interact with any of your existing Cloud Storage data. |
| `--manifest-file` | MANIFEST_FILE |  | _[JOB INFORMATION]_ Path to a .csv file containing a list of files to transfer from your source. For manifest files in Cloud Storage, specify the absolute path (e.g., gs://mybucket/manifest.csv). For manifest files stored in a source or destination POSIX file system, provide the relative path (e.g., source://path/to/manfest.csv or destination://path/to/manifest.csv). For manifest file formatting, see https://cloud.google.com/storage-transfer/docs/manifest. |
| `--replication` |  |  | _[REPLICATION OPTIONS]_ Enable replication to automatically copy all new and existing objects from the source to the destination. Note: Objects deleted from the source bucket will not be deleted from the destination bucket. Please note that it is an event-driven transfer. |
| `--event-stream-name` | EVENT_STREAM_NAME |  | _[https://cloud.google.com/sdk/gcloud/reference/topic/datetimes.]_ Specify an event stream that Storage Transfer Service can use to listen for when objects are created or updated. For Google Cloud Storage sources, specify a Cloud Pub/Sub subscription, using format "projects/yourproject/subscriptions/yoursubscription". For Amazon S3 sources, specify the Amazon Resource Name (ARN) of an Amazon Simple Queue Service (SQS) queue using format "arn:aws:sqs:region:account_id:queue_name". |
| `--event-stream-starts` | EVENT_STREAM_STARTS |  | _[https://cloud.google.com/sdk/gcloud/reference/topic/datetimes.]_ Set when to start listening for events UTC using the %Y-%m-%dT%H:%M:%S%z datetime format (e.g., 2020-04-12T06:42:12+04:00). If not set, the job will start running and listening for events upon the successful submission of the create job command. |
| `--event-stream-expires` | EVENT_STREAM_EXPIRES |  | _[https://cloud.google.com/sdk/gcloud/reference/topic/datetimes.]_ Set when to stop listening for events UTC using the %Y-%m-%dT%H:%M:%S%z datetime format (e.g., 2020-04-12T06:42:12+04:00). If not set, the job will continue running and listening for events indefinitely. |
| `--do-not-run` |  |  | _[https://cloud.google.com/sdk/gcloud/reference/topic/datetimes.]_ Disable default Transfer Service behavior of running job upon creation if no schedule is set. If this flag is specified, the job won't run until an operation is manually started or a schedule is added. |
| `--schedule-starts` | SCHEDULE_STARTS |  | _[https://cloud.google.com/sdk/gcloud/reference/topic/datetimes.]_ Set when the job will start using the %Y-%m-%dT%H:%M:%S%z datetime format (e.g., 2020-04-12T06:42:12+04:00). If not set, the job will run upon the successful submission of the create job command unless the --do-not-run flag is included. |
| `--schedule-repeats-every` | SCHEDULE_REPEATS_EVERY |  | _[https://cloud.google.com/sdk/gcloud/reference/topic/datetimes.]_ Set the frequency of the job using the absolute duration format (e.g., 1 month is p1m; 1 hour 30 minutes is 1h30m). If not set, the job will run once. |
| `--schedule-repeats-until` | SCHEDULE_REPEATS_UNTIL |  | _[https://cloud.google.com/sdk/gcloud/reference/topic/datetimes.]_ Set when the job will stop recurring using the %Y-%m-%dT%H:%M:%S%z datetime format (e.g., 2020-04-12T06:42:12+04:00). If specified, you must also include a value for the --schedule-repeats-every flag. If not specified, the job will continue to repeat as specified in its repeat-every field unless the job is manually disabled or you add this field later. |
| `--include-prefixes` | [INCLUDED_PREFIXES,...] |  | _[other conditions.]_ Include only objects that start with the specified prefix(es). Separate multiple prefixes with commas, omitting spaces after the commas (e.g., --include-prefixes=foo,bar). |
| `--exclude-prefixes` | [EXCLUDED_PREFIXES,...] |  | _[other conditions.]_ Exclude any objects that start with the prefix(es) entered. Separate multiple prefixes with commas, omitting spaces after the commas (e.g., --exclude-prefixes=foo,bar). |
| `--match-glob` | MATCH_GLOB |  | _[other conditions.]_ Include only objects that match the specified glob pattern. For more information about glob patterns, see https://docs.cloud.google.com/storage-transfer/docs/filter-by-glob-pattern |
| `--include-modified-before-absolute` | INCLUDE_MODIFIED_BEFORE_ABSOLUTE |  | _[other conditions.]_ Include objects last modified before an absolute date/time. Ex. by specifying '2020-01-01', the transfer would include objects last modified before January 1, 2020. Use the %Y-%m-%dT%H:%M:%S%z datetime format. |
| `--include-modified-after-absolute` | INCLUDE_MODIFIED_AFTER_ABSOLUTE |  | _[other conditions.]_ Include objects last modified after an absolute date/time. Ex. by specifying '2020-01-01', the transfer would include objects last modified after January 1, 2020. Use the %Y-%m-%dT%H:%M:%S%z datetime format. |
| `--include-modified-before-relative` | INCLUDE_MODIFIED_BEFORE_RELATIVE |  | _[other conditions.]_ Include objects that were modified before a relative date/time in the past. Ex. by specifying a duration of '10d', the transfer would include objects last modified more than 10 days before its start time. Use the absolute duration format (ex. 1m for 1 month; 1h30m for 1 hour 30 minutes). |
| `--include-modified-after-relative` | INCLUDE_MODIFIED_AFTER_RELATIVE |  | _[other conditions.]_ Include objects that were modified after a relative date/time in the past. Ex. by specifying a duration of '10d', the transfer would include objects last modified less than 10 days before its start time. Use the absolute duration format (ex. 1m for 1 month; 1h30m for 1 hour 30 minutes). |
| `--overwrite-when` | one of: always, different, never |  | _[TRANSFER OPTIONS]_ Determine when destination objects are overwritten by source objects. Options include: + 'different' - Overwrites files with the same name if the contents are different (e.g., if etags or checksums don't match) + 'always' - Overwrite destination file whenever source file has the same name -- even if they're identical + 'never' - Never overwrite destination file when source file has the same name OVERWRITE_WHEN must be one of: always, different, never. |
| `--delete-from` | one of: destination-if-unique, source-after-transfer |  | _[TRANSFER OPTIONS]_ By default, transfer jobs won't delete any data from your source or destination. These options enable you to delete data if needed for your use case. Options include: + 'destination-if-unique' - Delete files from destination if they're not also at source. Use to sync destination to source (i.e., make destination match source exactly) + 'source-after-transfer' - Delete files from source after they're transferred DELETE_FROM must be one of: destination-if-unique, source-after-transfer. |
| `--preserve-metadata` | one of: acl, gid, kms-key, mode, storage-class, symlink, temporary-hold, time-created, uid |  | _[TRANSFER OPTIONS]_ Specify object metadata values that can optionally be preserved. Example: --preserve-metadata=storage-class,uid For more info, see: https://cloud.google.com/storage-transfer/docs/metadata-preservation. METADATA_FIELDS must be one of: acl, gid, kms-key, mode, storage-class, symlink, temporary-hold, time-created, uid. |
| `--custom-storage-class` | CUSTOM_STORAGE_CLASS |  | _[TRANSFER OPTIONS]_ Specifies the storage class to set on objects being transferred to Cloud Storage buckets. If unspecified, the objects' storage class is set to the destination bucket default. Valid values are: + Any of the values listed in the Cloud Storage documentation: Available storage classes (https://cloud.google.com/storage/docs/storage-classes#classes). + preserve - Preserves each object's original storage class. Only supported for transfers between Cloud Storage buckets. Custom storage class settings are ignored if the destination bucket is Autoclass-enabled (https://cloud.google.com/storage/docs/autoclass). Objects transferred into Autoclass-enabled buckets are initially set to the STANDARD storage class. |
| `--notification-pubsub-topic` | NOTIFICATION_PUBSUB_TOPIC |  | _[changes via Cloud Pub/Sub.]_ Pub/Sub topic used for notifications. |
| `--notification-event-types` | one of: success, failed, aborted |  | _[changes via Cloud Pub/Sub.]_ Define which change of transfer operation status will trigger Pub/Sub notifications. Choices include 'success', 'failed', 'aborted'. To trigger notifications for all three status changes, you can leave this flag unspecified as long as you've specified a topic for the --notification-pubsub-topic flag. EVENT_TYPES must be one of: success, failed, aborted. |
| `--notification-payload-format` | one of: json, none |  | _[changes via Cloud Pub/Sub.]_ If 'none', no transfer operation details are included with notifications. If 'json', a json representation of the relevant transfer operation is included in notification messages (e.g., to see errors after an operation fails). NOTIFICATION_PAYLOAD_FORMAT must be one of: json, none. |
| `--[no-]enable-posix-transfer-logs` |  |  | _[command: gcloud logging read "resource.type=storage_transfer_job"]_ Sets whether to generate logs for transfers with a POSIX filesystem source. This setting will later be merged with other log configurations. Use --enable-posix-transfer-logs to enable and --no-enable-posix-transfer-logs to disable. |
| `--log-actions` | one of: copy, delete, find |  | _[command: gcloud logging read "resource.type=storage_transfer_job"]_ Define the transfer operation actions to report in logs. Separate multiple actions with commas, omitting spaces after the commas (e.g., --log-actions=find,copy). LOG_ACTIONS must be one of: copy, delete, find. |
| `--log-action-states` | one of: failed, skipped, succeeded |  | _[command: gcloud logging read "resource.type=storage_transfer_job"]_ The states in which the actions specified in --log-actions are logged. Separate multiple states with a comma, omitting the space after the comma (e.g., --log-action-states=succeeded,failed). LOG_ACTION_STATES must be one of: failed, skipped, succeeded. |
| `--source-endpoint` | SOURCE_ENDPOINT |  | _[ADDITIONAL OPTIONS]_ For transfers from S3-compatible sources, specify your storage system's endpoint. Check with your provider for formatting (ex. s3.us-east-1.amazonaws.com for Amazon S3). |
| `--source-signing-region` | SOURCE_SIGNING_REGION |  | _[ADDITIONAL OPTIONS]_ For transfers from S3-compatible sources, specify a region for signing requests. You can leave this unspecified if your storage provider doesn't require a signing region. |
| `--source-auth-method` | one of: AWS_SIGNATURE_V2, AWS_SIGNATURE_V4 |  | _[ADDITIONAL OPTIONS]_ For transfers from S3-compatible sources, choose a process for adding authentication information to S3 API requests. Refer to AWS's SigV4 (https://docs.aws.amazon.com/general/latest/gr/signature-version-4.html) and SigV2 (https://docs.aws.amazon.com/general/latest/gr/signature-version-2.html) documentation for more information. SOURCE_AUTH_METHOD must be one of: AWS_SIGNATURE_V2, AWS_SIGNATURE_V4. |
| `--source-list-api` | one of: LIST_OBJECTS, LIST_OBJECTS_V2 |  | _[ADDITIONAL OPTIONS]_ For transfers from S3-compatible sources, choose the version of the S3 listing API for returning objects from the bucket. Refer to AWS's ListObjectsV2 (https://docs.aws.amazon.com/AmazonS3/latest/API/API_ListObjectsV2.html) and ListObjects (https://docs.aws.amazon.com/AmazonS3/latest/API/API_ListObjects.html) documentation for more information. SOURCE_LIST_API must be one of: LIST_OBJECTS, LIST_OBJECTS_V2. |
| `--source-network-protocol` | one of: HTTP, HTTPS |  | _[ADDITIONAL OPTIONS]_ For transfers from S3-compatible sources, choose the network protocol agents should use for this job. SOURCE_NETWORK_PROTOCOL must be one of: HTTP, HTTPS. |
| `--source-request-model` | one of: PATH_STYLE, VIRTUAL_HOSTED_STYLE |  | _[ADDITIONAL OPTIONS]_ For transfers from S3-compatible sources, choose which addressing style to use. Determines if the bucket name is in the hostname or part of the URL. For example, https://s3.region.amazonaws.com/bucket-name/key-name for path style and Ex. https://bucket-name.s3.region.amazonaws.com/key-name for virtual-hosted style. SOURCE_REQUEST_MODEL must be one of: PATH_STYLE, VIRTUAL_HOSTED_STYLE. |
| `--s3-cloudfront-domain` | S3_CLOUDFRONT_DOMAIN |  | _[ADDITIONAL OPTIONS]_ For transfers from S3, optionally route egress traffic through a CloudFront instance. Supply the endpoint of the CloudFront instance: https://example.cloudfront.net. See documentation (https://cloud.google.com/storage-transfer/docs/s3-cloudfront) for more information. |
| `--no-async` |  |  | _[EXECUTION OPTIONS]_ For jobs set to run upon creation, this flag blocks other tasks in your terminal until the job's initial, immediate transfer operation has completed. If not included, tasks will run asynchronously. |


**Examples:**
```bash
To create a one-time, immediate transfer job to move data from Google Cloud
Storage bucket "foo" into the "baz" folder in Cloud Storage bucket "bar",
run:

    $ gcloud transfer jobs create gs://foo gs://bar/baz/

To create a transfer job to move data from an Amazon S3 bucket called "foo"
to a Google Cloud Storage bucket named "bar" that runs every day with
custom name "my-test-job", run:

    $ gcloud transfer jobs create s3://foo gs://bar --name=my-test-job \
        --source-creds-file=/examplefolder/creds.txt \
        --schedule-repeats-every=1d

To create a one-time, immediate transfer job to move data between Google
Cloud Storage buckets "foo" and "bar" with filters to include objects that
start with prefixes "baz" and "qux"; and objects modified in the 24 hours
before the transfer started, run:

    $ gcloud transfer jobs create gs://foo gs://bar/ \
        --include-prefixes=baz,qux --include-modified-after-relative=1d

To create a one-time, immediate transfer job to move data from a directory
with absolute path "/foo/bar/" in the filesystem associated with agent pool
"my-pool" into Google Cloud Storage bucket "example-bucket", run:

    $ gcloud transfer jobs create posix:///foo/bar/ \
        gs://example-bucket --source-agent-pool=my-pool
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/transfer/jobs/create)

---
### `gcloud transfer jobs delete`

Delete a Transfer Service transfer job

Delete a Transfer Service transfer job.

**Synopsis:**
```
gcloud transfer jobs delete NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of the job you want to delete.
```

**Examples:**
```bash
To delete job 'foo', run:

    $ gcloud transfer jobs delete foo
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/transfer/jobs/delete)

---
### `gcloud transfer jobs describe`

Get configuration and latest operation details about transfer job

Get configuration and latest operation details about a specific transfer
job.

**Synopsis:**
```
gcloud transfer jobs describe NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of the job you want to describe.
```

**Examples:**
```bash
To describe a job, run:

    $ gcloud transfer jobs describe JOB-NAME

If you're looking for recent error details, use the "latestOperationName"
returned by this command as input to the "operations describe" command:

    $ gcloud transfer jobs describe JOB-NAME \
        --format="json(latestOperationName)"

    $ gcloud transfer operations describe OPERATION-NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/transfer/jobs/describe)

---
### `gcloud transfer jobs list`

List Transfer Service transfer jobs

List Transfer Service transfer jobs in a given project to show their
configurations and latest operations.

**Synopsis:**
```
gcloud transfer jobs list [--limit=LIMIT]
    [--page-size=PAGE_SIZE; default=256] [--job-names=[JOB_NAMES,...]]
    [--job-statuses=[JOB_STATUSES,...]] [--expand-table]
    [--job-type=JOB_TYPE; default="transfer"] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--limit` | LIMIT |  | Return the first items from the API up to this limit. |
| `--page-size` | PAGE_SIZE | 256 | Retrieve batches of this many items from the API. |
| `--job-names` | [JOB_NAMES,...] |  | The names of the jobs you want to list. Separate multiple job names with commas (e.g., --job-names=foo,bar). If not specified, all jobs will be listed. |
| `--job-statuses` | [JOB_STATUSES,...] |  | List only jobs with the statuses you specify. Options include 'enabled', 'disabled', 'deleted' (case insensitive). Separate multiple statuses with commas (e.g., --job-statuses=enabled,deleted). If not specified, all jobs will be listed. |
| `--expand-table` |  |  | Include additional table columns (job name, source, destination, frequency, lastest operation name, job status) in command output. Tip: increase the size of your terminal before running the command. |
| `--job-type` | one of: transfer, replication | transfer | The type of the job you want to list. JOB_TYPE must be one of: transfer, replication. |


**Examples:**
```bash
To list all jobs in your current project, run:

    $ gcloud transfer jobs list

To list all disabled jobs in your project, run:

    $ gcloud transfer jobs list --job-statuses=disabled

To list jobs 'foo' and 'bar', run:

    $ gcloud transfer jobs list --job-names=foo,bar

To list all information about all jobs formatted as JSON, run:

    $ gcloud transfer jobs list --format=json

To list all information about jobs 'foo' and 'bar' formatted as YAML, run:

    $ gcloud transfer jobs list --job-names=foo,bar --format=YAML
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/transfer/jobs/list)

---
### `gcloud transfer jobs monitor`

Track progress in real time for a transfer job's latest operation

Track progress in real time for a transfer job's latest operation.

**Synopsis:**
```
gcloud transfer jobs monitor NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of the job you want to monitor (you'll see details for the
   job's latest operation).
```

**Examples:**
```bash
To monitor a job, run:

    $ gcloud transfer jobs monitor JOB-NAME

If you're looking for recent error details, use the "Operation name"
returned by this command as input to the "operations describe" command:

    $ gcloud transfer jobs monitor JOB-NAME

    $ gcloud transfer operations describe OPERATION-NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/transfer/jobs/monitor)

---
### `gcloud transfer jobs run`

Run a Transfer Service transfer job

Run a Transfer Service transfer job.

**Synopsis:**
```
gcloud transfer jobs run NAME [--no-async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of the job you want to run.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--no-async` |  |  | Blocks other tasks in your terminal until the transfer operation has completed. If not included, tasks will run asynchronously. |


**Examples:**
```bash
To run job 'foo', run:

    $ gcloud transfer jobs run foo
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/transfer/jobs/run)

---
### `gcloud transfer jobs update`

Update a Transfer Service transfer job

Update a Transfer Service transfer job.

**Synopsis:**
```
gcloud transfer jobs update NAME
    [--status=STATUS --source=SOURCE --destination=DESTINATION
      --clear-description --clear-source-creds-file
      --clear-source-agent-pool --clear-destination-agent-pool
      --clear-intermediate-storage-path --clear-manifest-file
      --description=DESCRIPTION --source-creds-file=SOURCE_CREDS_FILE
      --source-agent-pool=SOURCE_AGENT_POOL
      --destination-agent-pool=DESTINATION_AGENT_POOL
      --intermediate-storage-path=INTERMEDIATE_STORAGE_PATH
      --manifest-file=MANIFEST_FILE]
    [--event-stream-name=EVENT_STREAM_NAME
      --event-stream-starts=EVENT_STREAM_STARTS
      --event-stream-expires=EVENT_STREAM_EXPIRES --clear-event-stream]
    [--clear-schedule --schedule-starts=SCHEDULE_STARTS
      --schedule-repeats-every=SCHEDULE_REPEATS_EVERY
      --schedule-repeats-until=SCHEDULE_REPEATS_UNTIL]
    [--clear-include-prefixes --clear-exclude-prefixes --clear-match-glob
      --clear-include-modified-before-absolute
      --clear-include-modified-after-absolute
      --clear-include-modified-before-relative
      --clear-include-modified-after-relative
      --include-prefixes=[INCLUDED_PREFIXES,...]
      --exclude-prefixes=[EXCLUDED_PREFIXES,...] --match-glob=MATCH_GLOB
      --include-modified-before-absolute=INCLUDE_MODIFIED_BEFORE_ABSOLUTE
      --include-modified-after-absolute=INCLUDE_MODIFIED_AFTER_ABSOLUTE
      --include-modified-before-relative=INCLUDE_MODIFIED_BEFORE_RELATIVE
      --include-modified-after-relative=INCLUDE_MODIFIED_AFTER_RELATIVE]
    [--clear-delete-from --clear-preserve-metadata
      --clear-custom-storage-class --overwrite-when=OVERWRITE_WHEN
      --delete-from=DELETE_FROM --preserve-metadata=[METADATA_FIELDS,...]
      --custom-storage-class=CUSTOM_STORAGE_CLASS]
    [--clear-notification-config --clear-notification-event-types
      --notification-pubsub-topic=NOTIFICATION_PUBSUB_TOPIC
      --notification-event-types=[EVENT_TYPES,...]
      --notification-payload-format=NOTIFICATION_PAYLOAD_FORMAT]
    [--clear-log-config --[no-]enable-posix-transfer-logs
      --log-actions=[LOG_ACTIONS,...]
      --log-action-states=[LOG_ACTION_STATES,...]]
    [--source-endpoint=SOURCE_ENDPOINT
      --source-signing-region=SOURCE_SIGNING_REGION
      --source-auth-method=SOURCE_AUTH_METHOD
      --source-list-api=SOURCE_LIST_API
      --source-network-protocol=SOURCE_NETWORK_PROTOCOL
      --source-request-model=SOURCE_REQUEST_MODEL
      --s3-cloudfront-domain=S3_CLOUDFRONT_DOMAIN --clear-source-endpoint
      --clear-source-signing-region --clear-source-auth-method
      --clear-source-list-api --clear-source-network-protocol
      --clear-source-request-model --clear-s3-cloudfront-domain]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the transfer job you'd like to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--status` | one of: deleted, disabled, enabled |  | _[JOB INFORMATION]_ Specify this flag to change the status of the job. Options include 'enabled', 'disabled', 'deleted'. STATUS must be one of: deleted, disabled, enabled. |
| `--source` | SOURCE |  | _[JOB INFORMATION]_ The source of your data. Available sources and formatting information: Public clouds - + [Google Cloud Storage] gs://example-bucket/example-folder/ + [Amazon S3] s3://examplebucket/example-folder + [Azure Blob Storage or Data Lake Storage] http://examplestorageaccount.blob.core.windows.net/examplecontainer/examplefolder POSIX filesystem - Specify the posix:// scheme followed by the absolute path to the desired directory, starting from the root of the host machine (denoted by a leading slash). For example: + posix:///path/directory/ A file transfer agent must be installed on the POSIX filesystem, and you need an agent pool flag on this jobs command to activate the agent. Hadoop Distributed File System (HDFS) - Specify the hdfs:// scheme followed by the absolute path to the desired directory, starting from the root of the file system (denoted by a leading slash). For example: + hdfs:///path/directory/ Namenode details should not be included in the path specification, as they are required separately during the agent installation process. A file transfer agent must be installed, and you need an agent pool flag on this jobs command to activate the agent. Publicly-accessible objects - Specify the URL of a TSV file containing a list of URLs of publicly-accessible objects. For example: + http://example.com/tsvfile |
| `--destination` | DESTINATION |  | _[JOB INFORMATION]_ The destination of your transferred data. Available destinations and formatting information: Google Cloud Storage - Specify the gs:// scheme; name of the bucket; and, if transferring to a folder, the path to the folder. For example: + gs://example-bucket/example-folder/ POSIX filesystem - Specify the posix:// scheme followed by the absolute path to the desired directory, starting from the root of the host machine (denoted by a leading slash). For example: + posix:///path/directory/ A file transfer agent must be installed on the POSIX filesystem, and you need an agent pool flag on this jobs command to activate the agent. |
| `--clear-description` |  |  | _[JOB INFORMATION]_ Remove the description from the transfer job. |
| `--clear-source-creds-file` |  |  | _[JOB INFORMATION]_ Remove the source creds file from the transfer job. |
| `--clear-source-agent-pool` |  |  | _[JOB INFORMATION]_ Remove the source agent pool from the transfer job. |
| `--clear-destination-agent-pool` |  |  | _[JOB INFORMATION]_ Remove the destination agent pool from the transfer job. |
| `--clear-intermediate-storage-path` |  |  | _[JOB INFORMATION]_ Remove the intermediate storage path from the transfer job. |
| `--clear-manifest-file` |  |  | _[JOB INFORMATION]_ Remove the manifest file from the transfer job. |
| `--description` | DESCRIPTION |  | _[JOB INFORMATION]_ An optional description to help identify the job using details that don't fit in its name. |
| `--source-creds-file` | SOURCE_CREDS_FILE |  | _[JOB INFORMATION]_ Path to a local file on your machine that includes credentials for an Amazon S3 or Azure Blob Storage source (not required for Google Cloud Storage sources). If not specified for an S3 source, gcloud will check your system for an AWS config file. However, this flag must be specified to use AWS's "role_arn" auth service. For formatting, see: S3: https://cloud.google.com/storage-transfer/docs/reference/rest/v1/TransferSpec#AwsAccessKey Note: Be sure to put quotations around the JSON value strings. Azure: https://cloud.google.com/storage-transfer/docs/reference/rest/v1/TransferSpec#AzureCredentials |
| `--source-agent-pool` | SOURCE_AGENT_POOL |  | _[JOB INFORMATION]_ If using a POSIX filesystem source, specify the ID of the agent pool associated with source filesystem. |
| `--destination-agent-pool` | DESTINATION_AGENT_POOL |  | _[JOB INFORMATION]_ If using a POSIX filesystem destination, specify the ID of the agent pool associated with destination filesystem. |
| `--intermediate-storage-path` | INTERMEDIATE_STORAGE_PATH |  | _[JOB INFORMATION]_ If transferring between filesystems, specify the path to a folder in a Google Cloud Storage bucket (gs://example-bucket/example-folder) to use as intermediary storage. Recommended: Use an empty folder reserved for this transfer job to ensure transferred data doesn't interact with any of your existing Cloud Storage data. |
| `--manifest-file` | MANIFEST_FILE |  | _[JOB INFORMATION]_ Path to a .csv file containing a list of files to transfer from your source. For manifest files in Cloud Storage, specify the absolute path (e.g., gs://mybucket/manifest.csv). For manifest files stored in a source or destination POSIX file system, provide the relative path (e.g., source://path/to/manfest.csv or destination://path/to/manifest.csv). For manifest file formatting, see https://cloud.google.com/storage-transfer/docs/manifest. |
| `--event-stream-name` | EVENT_STREAM_NAME |  | _[https://cloud.google.com/sdk/gcloud/reference/topic/datetimes.]_ Specify an event stream that Storage Transfer Service can use to listen for when objects are created or updated. For Google Cloud Storage sources, specify a Cloud Pub/Sub subscription, using format "projects/yourproject/subscriptions/yoursubscription". For Amazon S3 sources, specify the Amazon Resource Name (ARN) of an Amazon Simple Queue Service (SQS) queue using format "arn:aws:sqs:region:account_id:queue_name". |
| `--event-stream-starts` | EVENT_STREAM_STARTS |  | _[https://cloud.google.com/sdk/gcloud/reference/topic/datetimes.]_ Set when to start listening for events UTC using the %Y-%m-%dT%H:%M:%S%z datetime format (e.g., 2020-04-12T06:42:12+04:00). If not set, the job will start running and listening for events upon the successful submission of the create job command. |
| `--event-stream-expires` | EVENT_STREAM_EXPIRES |  | _[https://cloud.google.com/sdk/gcloud/reference/topic/datetimes.]_ Set when to stop listening for events UTC using the %Y-%m-%dT%H:%M:%S%z datetime format (e.g., 2020-04-12T06:42:12+04:00). If not set, the job will continue running and listening for events indefinitely. |
| `--clear-event-stream` |  |  | _[https://cloud.google.com/sdk/gcloud/reference/topic/datetimes.]_ Remove the job's entire event stream configuration by clearing all scheduling all event stream flags. The job will no longer listen for events unless a new configuratin is specified. |
| `--clear-schedule` |  |  | _[https://cloud.google.com/sdk/gcloud/reference/topic/datetimes.]_ Remove the job's entire schedule by clearing all scheduling flags. The job will no longer run unless an operation is manually started or a new schedule is specified. |
| `--schedule-starts` | SCHEDULE_STARTS |  | _[https://cloud.google.com/sdk/gcloud/reference/topic/datetimes.]_ Set when the job will start using the %Y-%m-%dT%H:%M:%S%z datetime format (e.g., 2020-04-12T06:42:12+04:00). If not set, the job will run upon the successful submission of the create job command unless the --do-not-run flag is included. |
| `--schedule-repeats-every` | SCHEDULE_REPEATS_EVERY |  | _[https://cloud.google.com/sdk/gcloud/reference/topic/datetimes.]_ Set the frequency of the job using the absolute duration format (e.g., 1 month is p1m; 1 hour 30 minutes is 1h30m). If not set, the job will run once. |
| `--schedule-repeats-until` | SCHEDULE_REPEATS_UNTIL |  | _[https://cloud.google.com/sdk/gcloud/reference/topic/datetimes.]_ Set when the job will stop recurring using the %Y-%m-%dT%H:%M:%S%z datetime format (e.g., 2020-04-12T06:42:12+04:00). If specified, you must also include a value for the --schedule-repeats-every flag. If not specified, the job will continue to repeat as specified in its repeat-every field unless the job is manually disabled or you add this field later. |
| `--clear-include-prefixes` |  |  | _[other conditions.]_ Remove the list of object prefixes to include from the object conditions. |
| `--clear-exclude-prefixes` |  |  | _[other conditions.]_ Remove the list of object prefixes to exclude from the object conditions. |
| `--clear-match-glob` |  |  | _[other conditions.]_ Remove the glob pattern from the object conditions. |
| `--clear-include-modified-before-absolute` |  |  | _[other conditions.]_ Remove the maximum modification datetime from the object conditions. |
| `--clear-include-modified-after-absolute` |  |  | _[other conditions.]_ Remove the minimum modification datetime from the object conditions. |
| `--clear-include-modified-before-relative` |  |  | _[other conditions.]_ Remove the maximum duration since modification from the object conditions. |
| `--clear-include-modified-after-relative` |  |  | _[other conditions.]_ Remove the minimum duration since modification from the object conditions. |
| `--include-prefixes` | [INCLUDED_PREFIXES,...] |  | _[other conditions.]_ Include only objects that start with the specified prefix(es). Separate multiple prefixes with commas, omitting spaces after the commas (e.g., --include-prefixes=foo,bar). |
| `--exclude-prefixes` | [EXCLUDED_PREFIXES,...] |  | _[other conditions.]_ Exclude any objects that start with the prefix(es) entered. Separate multiple prefixes with commas, omitting spaces after the commas (e.g., --exclude-prefixes=foo,bar). |
| `--match-glob` | MATCH_GLOB |  | _[other conditions.]_ Include only objects that match the specified glob pattern. For more information about glob patterns, see https://docs.cloud.google.com/storage-transfer/docs/filter-by-glob-pattern |
| `--include-modified-before-absolute` | INCLUDE_MODIFIED_BEFORE_ABSOLUTE |  | _[other conditions.]_ Include objects last modified before an absolute date/time. Ex. by specifying '2020-01-01', the transfer would include objects last modified before January 1, 2020. Use the %Y-%m-%dT%H:%M:%S%z datetime format. |
| `--include-modified-after-absolute` | INCLUDE_MODIFIED_AFTER_ABSOLUTE |  | _[other conditions.]_ Include objects last modified after an absolute date/time. Ex. by specifying '2020-01-01', the transfer would include objects last modified after January 1, 2020. Use the %Y-%m-%dT%H:%M:%S%z datetime format. |
| `--include-modified-before-relative` | INCLUDE_MODIFIED_BEFORE_RELATIVE |  | _[other conditions.]_ Include objects that were modified before a relative date/time in the past. Ex. by specifying a duration of '10d', the transfer would include objects last modified more than 10 days before its start time. Use the absolute duration format (ex. 1m for 1 month; 1h30m for 1 hour 30 minutes). |
| `--include-modified-after-relative` | INCLUDE_MODIFIED_AFTER_RELATIVE |  | _[other conditions.]_ Include objects that were modified after a relative date/time in the past. Ex. by specifying a duration of '10d', the transfer would include objects last modified less than 10 days before its start time. Use the absolute duration format (ex. 1m for 1 month; 1h30m for 1 hour 30 minutes). |
| `--clear-delete-from` |  |  | _[TRANSFER OPTIONS]_ Remove a specified deletion option from the transfer job. If this flag is specified, the transfer job won't delete any data from your source or destination. |
| `--clear-preserve-metadata` |  |  | _[TRANSFER OPTIONS]_ Skips preserving optional metadata fields of objects being transferred. |
| `--clear-custom-storage-class` |  |  | _[TRANSFER OPTIONS]_ Reverts to using destination default storage class. |
| `--overwrite-when` | one of: always, different, never |  | _[TRANSFER OPTIONS]_ Determine when destination objects are overwritten by source objects. Options include: + 'different' - Overwrites files with the same name if the contents are different (e.g., if etags or checksums don't match) + 'always' - Overwrite destination file whenever source file has the same name -- even if they're identical + 'never' - Never overwrite destination file when source file has the same name OVERWRITE_WHEN must be one of: always, different, never. |
| `--delete-from` | one of: destination-if-unique, source-after-transfer |  | _[TRANSFER OPTIONS]_ By default, transfer jobs won't delete any data from your source or destination. These options enable you to delete data if needed for your use case. Options include: + 'destination-if-unique' - Delete files from destination if they're not also at source. Use to sync destination to source (i.e., make destination match source exactly) + 'source-after-transfer' - Delete files from source after they're transferred DELETE_FROM must be one of: destination-if-unique, source-after-transfer. |
| `--preserve-metadata` | one of: acl, gid, kms-key, mode, storage-class, symlink, temporary-hold, time-created, uid |  | _[TRANSFER OPTIONS]_ Specify object metadata values that can optionally be preserved. Example: --preserve-metadata=storage-class,uid For more info, see: https://cloud.google.com/storage-transfer/docs/metadata-preservation. METADATA_FIELDS must be one of: acl, gid, kms-key, mode, storage-class, symlink, temporary-hold, time-created, uid. |
| `--custom-storage-class` | CUSTOM_STORAGE_CLASS |  | _[TRANSFER OPTIONS]_ Specifies the storage class to set on objects being transferred to Cloud Storage buckets. If unspecified, the objects' storage class is set to the destination bucket default. Valid values are: + Any of the values listed in the Cloud Storage documentation: Available storage classes (https://cloud.google.com/storage/docs/storage-classes#classes). + preserve - Preserves each object's original storage class. Only supported for transfers between Cloud Storage buckets. Custom storage class settings are ignored if the destination bucket is Autoclass-enabled (https://cloud.google.com/storage/docs/autoclass). Objects transferred into Autoclass-enabled buckets are initially set to the STANDARD storage class. |
| `--clear-notification-config` |  |  | _[changes via Cloud Pub/Sub.]_ Remove the job's full notification configuration to no longer receive notifications via Cloud Pub/Sub. |
| `--clear-notification-event-types` |  |  | _[changes via Cloud Pub/Sub.]_ Remove the event types from the notification config. |
| `--notification-pubsub-topic` | NOTIFICATION_PUBSUB_TOPIC |  | _[changes via Cloud Pub/Sub.]_ Pub/Sub topic used for notifications. |
| `--notification-event-types` | one of: success, failed, aborted |  | _[changes via Cloud Pub/Sub.]_ Define which change of transfer operation status will trigger Pub/Sub notifications. Choices include 'success', 'failed', 'aborted'. To trigger notifications for all three status changes, you can leave this flag unspecified as long as you've specified a topic for the --notification-pubsub-topic flag. EVENT_TYPES must be one of: success, failed, aborted. |
| `--notification-payload-format` | one of: json, none |  | _[changes via Cloud Pub/Sub.]_ If 'none', no transfer operation details are included with notifications. If 'json', a json representation of the relevant transfer operation is included in notification messages (e.g., to see errors after an operation fails). NOTIFICATION_PAYLOAD_FORMAT must be one of: json, none. |
| `--clear-log-config` |  |  | _[command: gcloud logging read "resource.type=storage_transfer_job"]_ Remove the job's full logging config. |
| `--[no-]enable-posix-transfer-logs` |  |  | _[command: gcloud logging read "resource.type=storage_transfer_job"]_ Sets whether to generate logs for transfers with a POSIX filesystem source. This setting will later be merged with other log configurations. Use --enable-posix-transfer-logs to enable and --no-enable-posix-transfer-logs to disable. |
| `--log-actions` | one of: copy, delete, find |  | _[command: gcloud logging read "resource.type=storage_transfer_job"]_ Define the transfer operation actions to report in logs. Separate multiple actions with commas, omitting spaces after the commas (e.g., --log-actions=find,copy). LOG_ACTIONS must be one of: copy, delete, find. |
| `--log-action-states` | one of: failed, skipped, succeeded |  | _[command: gcloud logging read "resource.type=storage_transfer_job"]_ The states in which the actions specified in --log-actions are logged. Separate multiple states with a comma, omitting the space after the comma (e.g., --log-action-states=succeeded,failed). LOG_ACTION_STATES must be one of: failed, skipped, succeeded. |
| `--source-endpoint` | SOURCE_ENDPOINT |  | _[ADDITIONAL OPTIONS]_ For transfers from S3-compatible sources, specify your storage system's endpoint. Check with your provider for formatting (ex. s3.us-east-1.amazonaws.com for Amazon S3). |
| `--source-signing-region` | SOURCE_SIGNING_REGION |  | _[ADDITIONAL OPTIONS]_ For transfers from S3-compatible sources, specify a region for signing requests. You can leave this unspecified if your storage provider doesn't require a signing region. |
| `--source-auth-method` | one of: AWS_SIGNATURE_V2, AWS_SIGNATURE_V4 |  | _[ADDITIONAL OPTIONS]_ For transfers from S3-compatible sources, choose a process for adding authentication information to S3 API requests. Refer to AWS's SigV4 (https://docs.aws.amazon.com/general/latest/gr/signature-version-4.html) and SigV2 (https://docs.aws.amazon.com/general/latest/gr/signature-version-2.html) documentation for more information. SOURCE_AUTH_METHOD must be one of: AWS_SIGNATURE_V2, AWS_SIGNATURE_V4. |
| `--source-list-api` | one of: LIST_OBJECTS, LIST_OBJECTS_V2 |  | _[ADDITIONAL OPTIONS]_ For transfers from S3-compatible sources, choose the version of the S3 listing API for returning objects from the bucket. Refer to AWS's ListObjectsV2 (https://docs.aws.amazon.com/AmazonS3/latest/API/API_ListObjectsV2.html) and ListObjects (https://docs.aws.amazon.com/AmazonS3/latest/API/API_ListObjects.html) documentation for more information. SOURCE_LIST_API must be one of: LIST_OBJECTS, LIST_OBJECTS_V2. |
| `--source-network-protocol` | one of: HTTP, HTTPS |  | _[ADDITIONAL OPTIONS]_ For transfers from S3-compatible sources, choose the network protocol agents should use for this job. SOURCE_NETWORK_PROTOCOL must be one of: HTTP, HTTPS. |
| `--source-request-model` | one of: PATH_STYLE, VIRTUAL_HOSTED_STYLE |  | _[ADDITIONAL OPTIONS]_ For transfers from S3-compatible sources, choose which addressing style to use. Determines if the bucket name is in the hostname or part of the URL. For example, https://s3.region.amazonaws.com/bucket-name/key-name for path style and Ex. https://bucket-name.s3.region.amazonaws.com/key-name for virtual-hosted style. SOURCE_REQUEST_MODEL must be one of: PATH_STYLE, VIRTUAL_HOSTED_STYLE. |
| `--s3-cloudfront-domain` | S3_CLOUDFRONT_DOMAIN |  | _[ADDITIONAL OPTIONS]_ For transfers from S3, optionally route egress traffic through a CloudFront instance. Supply the endpoint of the CloudFront instance: https://example.cloudfront.net. See documentation (https://cloud.google.com/storage-transfer/docs/s3-cloudfront) for more information. |
| `--clear-source-endpoint` |  |  | _[ADDITIONAL OPTIONS]_ Removes source endpoint. |
| `--clear-source-signing-region` |  |  | _[ADDITIONAL OPTIONS]_ Removes source signing region. |
| `--clear-source-auth-method` |  |  | _[ADDITIONAL OPTIONS]_ Removes source auth method. |
| `--clear-source-list-api` |  |  | _[ADDITIONAL OPTIONS]_ Removes source list API. |
| `--clear-source-network-protocol` |  |  | _[ADDITIONAL OPTIONS]_ Removes source network protocol. |
| `--clear-source-request-model` |  |  | _[ADDITIONAL OPTIONS]_ Removes source request model. |
| `--clear-s3-cloudfront-domain` |  |  | _[ADDITIONAL OPTIONS]_ Removes S3 CloudFront domain. |


**Examples:**
```bash
To disable transfer job 'foo', run:

    $ gcloud transfer jobs update foo --status=disabled

To remove the schedule for transfer job 'foo' so that it will only run when
you manually start it, run:

    $ gcloud transfer jobs update foo --clear-schedule

To clear the values from the include=prefixes object condition in transfer
job 'foo', run:

    $ gcloud transfer jobs update foo --clear-include-prefixes
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/transfer/jobs/update)

---
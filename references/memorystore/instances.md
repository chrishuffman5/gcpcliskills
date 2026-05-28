# gcloud memorystore instances

manage Instance resources

### `gcloud memorystore instances backup`

Backup instances

**Synopsis:**
```
gcloud memorystore instances backup (INSTANCE : --location=LOCATION)
    [--async] [--backup-id=BACKUP_ID] [--ttl=TTL] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Instance resource name using the form:
projects/{project_id}/locations/{location_id}/instances/{instance_id}
where location_id refers to a Google Cloud region. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the instance resource.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--backup-id` | BACKUP_ID |  | The id of the backup to be created. If not specified, the default value ([YYYYMMDDHHMMSS][Shortened Instance UID] is used. |
| `--ttl` | TTL |  | TTL for the backup to expire. Value range is 1 day to 100 years. If not specified, the default value is 100 years. |


**Examples:**
```bash
To backup all instances, run:

    $ gcloud memorystore instances backup
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/memorystore/instances/backup)

---
### `gcloud memorystore instances create`

Create a Memorystore instance

Create a Memorystore instance.

A service connection policy for service class gcp-memorystore must already
exist for the location and network. Refer to creation prerequisites
(https://cloud.google.com/memorystore/docs/valkey/networking#prerequisites_required_before_creating_an_instance)
for more details.

**Synopsis:**
```
gcloud memorystore instances create INSTANCE [--async]
    [--async-instance-endpoints-deletion-enabled]
    [--authorization-mode=AUTHORIZATION_MODE]
    [--deletion-protection-enabled] [--endpoints=[connections=CONNECTIONS]]
    [--engine-configs=[ENGINE_CONFIGS,...]]
    [--engine-version=ENGINE_VERSION] [--labels=[LABELS,...]]
    [--location=LOCATION]
    [--maintenance-policy-weekly-window=[day=DAY],[startTime=STARTTIME]]
    [--mode=MODE] [--node-type=NODE_TYPE] [--ondemand-maintenance]
    [--psc-auto-connections=[network=NETWORK],
      [port=PORT],[projectId=PROJECTID]] [--replica-count=REPLICA_COUNT]
    [--request-id=REQUEST_ID] [--shard-count=SHARD_COUNT]
    [--simulate-maintenance-event]
    [--transit-encryption-mode=TRANSIT_ENCRYPTION_MODE]
    [--aof-config-append-fsync=AOF_CONFIG_APPEND_FSYNC
      --persistence-config-mode=PERSISTENCE_CONFIG_MODE
      --rdb-config-snapshot-period=RDB_CONFIG_SNAPSHOT_PERIOD
      --rdb-config-snapshot-start-time=RDB_CONFIG_SNAPSHOT_START_TIME]
    [--automated-backup-config-mode=AUTOMATED_BACKUP_CONFIG_MODE
      --automated-backup-config-retention=AUTOMATED_BACKUP_CONFIG_RETENTION
      (--fixed-frequency-schedule-start-time-hours=FIXED_FREQUENCY_SCHEDULE_START_TIME_HOURS --fixed-frequency-schedule-start-time-minutes=FIXED_FREQUENCY_SCHEDULE_START_TIME_MINUTES --fixed-frequency-schedule-start-time-nanos=FIXED_FREQUENCY_SCHEDULE_START_TIME_NANOS --fixed-frequency-schedule-start-time-seconds=FIXED_FREQUENCY_SCHEDULE_START_TIME_SECONDS)]
    [--cross-instance-replication-config-role=CROSS_INSTANCE_REPLICATION_CONFIG_ROLE : --cross-instance-replication-config-secondary-instances=[instance=INSTANCE] --primary-instance=PRIMARY_INSTANCE]
    [--gcs-source-uris=[GCS_SOURCE_URIS,...]
      | --managed-backup-source=MANAGED_BACKUP_SOURCE]
    [--kms-key=KMS_KEY : --key-ring=KEY_RING]
    [--zone-distribution-config=ZONE_DISTRIBUTION_CONFIG
      --zone-distribution-config-mode=ZONE_DISTRIBUTION_CONFIG_MODE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Identifier. Unique name of the instance. Format:
projects/{project}/locations/{location}/instances/{instance} This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --location on the command line.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--authorization-mode` | one of: auth-disabled Authorization disabled |  | _[instance endpoint are deleted.]_ Authorization mode of the instance. AUTHORIZATION_MODE must be one of: auth-disabled Authorization disabled. iam-auth IAM basic authorization. |
| `--endpoints` | [connections=CONNECTIONS] |  | _[If set to true deletion of the instance will fail.]_ Endpoints for the instance. connections A group of PSC connections. They are created in the same VPC network, one for each service attachment in the cluster. pscAutoConnection Detailed information of a PSC connection that is created through service connectivity automation. network The network where the PSC endpoints are created, in the form of projects/{project_id}/global/networks/{network_id}. port port will only be set for Primary/Reader or Discovery endpoint. projectId The consumer project_id where PSC connections are established. This should be the same project_id that the instance is being created in. Shorthand Example: --endpoints=connections=[{pscAutoConnection={network=string,port=int,projectId=string}}] --endpoints=connections=[{pscAutoConnection={network=string,port=int,projectId=string}}] JSON Example: --endpoints='[{"connections": [{"pscAutoConnection": {"network": "string", "port": int, "projectId": "string"}}]}]' File Example: --endpoints=path_to_file.(yaml\|json) |
| `--engine-configs` | [ENGINE_CONFIGS,...] |  | _[If set to true deletion of the instance will fail.]_ User-provided engine configurations for the instance. KEY Sets KEY value. VALUE Sets VALUE value. Shorthand Example: --engine-configs=string=string JSON Example: --engine-configs='{"string": "string"}' File Example: --engine-configs=path_to_file.(yaml\|json) |
| `--engine-version` | ENGINE_VERSION |  | _[If set to true deletion of the instance will fail.]_ Engine version of the instance. |
| `--labels` | [LABELS,...] |  | _[If set to true deletion of the instance will fail.]_ Labels to represent user-provided metadata. KEY Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. VALUE Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Shorthand Example: --labels=string=string JSON Example: --labels='{"string": "string"}' File Example: --labels=path_to_file.(yaml\|json) |
| `--location` | LOCATION |  | _[If set to true deletion of the instance will fail.]_ For resources [instance, kms-key, primary-instance], provides fallback value for resource location attribute. When the resource's full URI path is not provided, location will fallback to this flag value. |
| `--mode` | one of: cluster Instance is in cluster mode |  | _[--maintenance-policy-weekly-window=path_to_file.(yaml\|json)]_ The mode config for the instance. MODE must be one of: cluster Instance is in cluster mode. cluster-disabled Cluster mode is disabled for the instance. standalone Deprecated: Use CLUSTER_DISABLED instead. |
| `--node-type` | one of: highmem-medium High memory medium |  | _[--maintenance-policy-weekly-window=path_to_file.(yaml\|json)]_ Machine type for individual nodes of the instance. NODE_TYPE must be one of: highmem-medium High memory medium. highmem-xlarge High memory extra large. shared-core-nano Shared core nano. standard-small Standard small. |
| `--psc-auto-connections` | [network=NETWORK],[port=PORT],[projectId=PROJECTID] |  | _[Ondemand maintenance for the instance.]_ Deprecated: Use the endpoints.connections.psc_auto_connection value instead. network The network where the PSC endpoints are created, in the form of projects/{project_id}/global/networks/{network_id}. port port will only be set for Primary/Reader or Discovery endpoint. projectId The consumer project_id where PSC connections are established. This should be the same project_id that the instance is being created in. Shorthand Example: --psc-auto-connections=network=string,port=int,projectId=string --psc-auto-connections=network=string,port=int,projectId=string JSON Example: --psc-auto-connections='[{"network": "string", "port": int, "projectId": "string"}]' File Example: --psc-auto-connections=path_to_file.(yaml\|json) |
| `--request-id` | REQUEST_ID |  | _[replicas.]_ An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes since the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |
| `--shard-count` | SHARD_COUNT |  | _[replicas.]_ Number of shards for the instance. |
| `--transit-encryption-mode` | one of: server-authentication Server-managed encryption is used for in-transit encryption |  | _[Simulate a maintenance event.]_ In-transit encryption mode of the instance. TRANSIT_ENCRYPTION_MODE must be one of: server-authentication Server-managed encryption is used for in-transit encryption. transit-encryption-disabled In-transit encryption is disabled. |


**Examples:**
```bash
To create a three shard Memorystore instance my-instance in project
my-project and location us-central1, run:

    $ gcloud memorystore instances create my-instance \
        --project=my-project --location=us-central1 --shard-count=3 \
        --psc-auto-connections="network=NETWORK,projectId=PROJECT_ID"

To create a three shard Memorystore instance my-instance in project
my-project, location us-central1, with one replica per shard, and TLS
enabled, run:

    $ gcloud memorystore instances create my-instance \
        --project=my-project --location=us-central1 --shard-count=3 \
        --psc-auto-connections="network=NETWORK,projectId=PROJECT_ID" \
        --transit-encryption-mode=server-authentication \
        --replica-count=1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/memorystore/instances/create)

---
### `gcloud memorystore instances delete`

Delete a Memorystore instance

Delete a Memorystore instance.

**Synopsis:**
```
gcloud memorystore instances delete (INSTANCE : --location=LOCATION)
    [--async] [--request-id=REQUEST_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The name of the instance to delete. Format:
projects/{project}/locations/{location}/instances/{instance} The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the instance resource.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes after the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To delete Memorystore instance my-instance in project my-project and
location us-central1, run:

    $ gcloud memorystore instances delete my-instance \
        --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/memorystore/instances/delete)

---
### `gcloud memorystore instances describe`

Get details of a Memorystore instance

Get details of a Memorystore instance.

**Synopsis:**
```
gcloud memorystore instances describe (INSTANCE : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The name of the instance to retrieve. Format:
projects/{project}/locations/{location}/instances/{instance} The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the instance resource.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To get the details of Memorystore instance my-instance in project
my-project and location us-central, run:

    $ gcloud memorystore instances describe my-instance \
        --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/memorystore/instances/describe)

---
### `gcloud memorystore instances get-certificate-authority`

Get certificate authority details of a Memorystore instance

Get certificate authority details of a Memorystore instance.

**Synopsis:**
```
gcloud memorystore instances get-certificate-authority
    (INSTANCE : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The name of the Memorystore instance. Format:
projects/{project}/locations/{location}/instances/{instance} The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location ID of the instance resource.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To get the certificate authority for instance my-instance in project
my-project and location us-central1, run:

    $ gcloud memorystore instances get-certificate-authority \
        my-instance --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/memorystore/instances/get-certificate-authority)

---
### `gcloud memorystore instances list`

List all Memorystore instances in a specified project and location

List all Memorystore instances in a specified project and location.

**Synopsis:**
```
gcloud memorystore instances list --location=LOCATION [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all Memorystore instances in project my-project and location
us-central, run:

    $ gcloud memorystore instances list --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/memorystore/instances/list)

---
### `gcloud memorystore instances reschedule-maintenance`

Reschedule maintenance window for an instance

Reschedule maintenance window for an instance.

**Synopsis:**
```
gcloud memorystore instances reschedule-maintenance
    (INSTANCE : --location=LOCATION) --reschedule-type=RESCHEDULE_TYPE
    [--async] [--schedule-time=SCHEDULE_TIME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Name of the instance to reschedule maintenance for:
projects/{project}/locations/{location_id}/instances/{instance} The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the instance resource.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--reschedule-type` | one of: immediate If the user wants to schedule the maintenance to happen now |  | If reschedule type is SPECIFIC_TIME, schedule_time must be set. RESCHEDULE_TYPE must be one of: immediate If the user wants to schedule the maintenance to happen now. specific-time If the user wants to reschedule the maintenance to a specific time. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--schedule-time` | SCHEDULE_TIME |  | Timestamp when the maintenance shall be rescheduled to if reschedule_type=SPECIFIC_TIME, in RFC 3339 format. Example: 2012-11-15T16:19:00.094Z. |


**Examples:**
```bash
To reschedule maintenance window for an instance with the name my-instance
in region us-central-1 with immediate, run:
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/memorystore/instances/reschedule-maintenance)

---
### `gcloud memorystore instances update`

Update the configuration of a Memorystore instance

Update the configuration of a Memorystore instance.

**Synopsis:**
```
gcloud memorystore instances update INSTANCE [--async]
    [--[no-]async-instance-endpoints-deletion-enabled]
    [--[no-]deletion-protection-enabled] [--engine-version=ENGINE_VERSION]
    [--location=LOCATION] [--maintenance-version=MAINTENANCE_VERSION]
    [--mode=MODE] [--node-type=NODE_TYPE] [--[no-]ondemand-maintenance]
    [--replica-count=REPLICA_COUNT] [--request-id=REQUEST_ID]
    [--shard-count=SHARD_COUNT] [--[no-]simulate-maintenance-event]
    [--aof-config-append-fsync=AOF_CONFIG_APPEND_FSYNC
      --clear-persistence-config
      --persistence-config-mode=PERSISTENCE_CONFIG_MODE
      --rdb-config-snapshot-period=RDB_CONFIG_SNAPSHOT_PERIOD
      --rdb-config-snapshot-start-time=RDB_CONFIG_SNAPSHOT_START_TIME]
    [--automated-backup-config-mode=AUTOMATED_BACKUP_CONFIG_MODE
      --automated-backup-config-retention=AUTOMATED_BACKUP_CONFIG_RETENTION
      --clear-automated-backup-config
      --fixed-frequency-schedule-start-time-hours=FIXED_FREQUENCY_SCHEDULE_START_TIME_HOURS --fixed-frequency-schedule-start-time-minutes=FIXED_FREQUENCY_SCHEDULE_START_TIME_MINUTES --fixed-frequency-schedule-start-time-nanos=FIXED_FREQUENCY_SCHEDULE_START_TIME_NANOS --fixed-frequency-schedule-start-time-seconds=FIXED_FREQUENCY_SCHEDULE_START_TIME_SECONDS]
    [--clear-cross-instance-replication-config
      --cross-instance-replication-config-role=CROSS_INSTANCE_REPLICATION_CONFIG_ROLE --clear-primary-instance | --primary-instance=PRIMARY_INSTANCE --cross-instance-replication-config-secondary-instances=[instance=INSTANCE] | --add-cross-instance-replication-config-secondary-instances=[instance=INSTANCE] --clear-cross-instance-replication-config-secondary-instances | --remove-cross-instance-replication-config-secondary-instances=[instance=INSTANCE]]
    [--clear-maintenance-policy
      --maintenance-policy-weekly-window=[day=DAY],[startTime=STARTTIME]
      | --add-maintenance-policy-weekly-window=[day=DAY],
      [startTime=STARTTIME] --clear-maintenance-policy-weekly-window
      | --remove-maintenance-policy-weekly-window=[day=DAY],
      [startTime=STARTTIME]]
    [--endpoints=[connections=CONNECTIONS]
      | --add-endpoints=[connections=CONNECTIONS] --clear-endpoints
      | --remove-endpoints=[connections=CONNECTIONS]]
    [--engine-configs=[ENGINE_CONFIGS,...]
      | --update-engine-configs=[UPDATE_ENGINE_CONFIGS,...]
      --clear-engine-configs
      | --remove-engine-configs=REMOVE_ENGINE_CONFIGS]
    [--key-ring=KEY_RING --clear-kms-key | --kms-key=KMS_KEY]
    [--labels=[LABELS,...]
      | --update-labels=[UPDATE_LABELS,...] --clear-labels
      | --remove-labels=REMOVE_LABELS] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Identifier. Unique name of the instance. Format:
projects/{project}/locations/{location}/instances/{instance} This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --location on the command line.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--engine-version` | ENGINE_VERSION |  | _[--no-deletion-protection-enabled to disable.]_ Engine version of the instance. |
| `--location` | LOCATION |  | _[--no-deletion-protection-enabled to disable.]_ For resources [instance, kms-key, primary-instance], provides fallback value for resource location attribute. When the resource's full URI path is not provided, location will fallback to this flag value. |
| `--mode` | one of: cluster Instance is in cluster mode |  | _[determined by the available_maintenance_versions field.]_ The mode config for the instance. MODE must be one of: cluster Instance is in cluster mode. cluster-disabled Cluster mode is disabled for the instance. standalone Deprecated: Use CLUSTER_DISABLED instead. |
| `--node-type` | one of: highmem-medium High memory medium |  | _[determined by the available_maintenance_versions field.]_ Machine type for individual nodes of the instance. NODE_TYPE must be one of: highmem-medium High memory medium. highmem-xlarge High memory extra large. shared-core-nano Shared core nano. standard-small Standard small. |
| `--request-id` | REQUEST_ID |  | _[replicas.]_ An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes since the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |
| `--shard-count` | SHARD_COUNT |  | _[replicas.]_ Number of shards for the instance. |


**Examples:**
```bash
To update Memorystore instance my-instance in project my-project and
location us-central1 to six shards, run:

    $ gcloud memorystore instances update `my-instance` \
        --project=my-project --location=us-central1 --shard-count=6

To update Memorystore instance my-instance in project my-project and
location us-central1 to use a maxmemory-policy of allkeys-lru, run:

    $ gcloud memorystore instances update `my-instance` \
        --project=my-project --location=us-central1 \
        --update-engine-configs=maxmemory-policy=allkeys-lru
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/memorystore/instances/update)

---
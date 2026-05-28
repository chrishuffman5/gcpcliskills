# gcloud redis clusters

manage Memorystore for Redis Cluster instances

### `gcloud redis clusters add-cluster-endpoints`

Add more cluster endpoints

This is required to enable multi-vpc for Redis cluster.

To add one cluster endpoint to an existing Redis cluster, two PSC
connections MUST be added as a pair: one for the Redis cluster's discovery
service attachment and the other for the additional service attachment.

Multiple cluster endpoints COULD be added simultaneously.

This command can fail for the following reasons:
  o The cluster specified does not exist.
  o The number of connections provided to a cluster endpoint are not in
    pairs.
  o One of the connections is not found.

**Synopsis:**
```
gcloud redis clusters add-cluster-endpoints (CLUSTER : --region=REGION)
    --cluster-endpoint=[psc-connection=PSC-CONNECTION] [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - Arguments and flags that specify the Memorystore Redis
cluster you want to update. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument cluster on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CLUSTER
     ID of the cluster or fully qualified identifier for the cluster.

     To set the cluster attribute:
     + provide the argument cluster on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the Redis region of the cluster. Overrides the default
     redis/region property value for this command invocation.

     To set the region attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property redis/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cluster-endpoint` | [psc-connection=PSC-CONNECTION] |  | Required, Resource details of a redis cluster endpoint. psc-connection Sets psc-connection value. address Sets address value. forwarding-rule Sets forwarding-rule value. network Sets network value. psc-connection-id Sets psc-connection-id value. service-attachment Sets service-attachment value. Shorthand Example: --cluster-endpoint=psc-connection=[{address=string,forwarding-rule=string,network=string,psc-connection-id=string,service-attachment=string}] --cluster-endpoint=psc-connection=[{address=string,forwarding-rule=string,network=string,psc-connection-id=string,service-attachment=string}] JSON Example: --cluster-endpoint='[{"psc-connection": [{"address": "string", "forwarding-rule": "string", "network": "string", "psc-connection-id": "string", "service-attachment": "string"}]}]' File Example: --cluster-endpoint=path_to_file.(yaml\|json) |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To connect redis cluster to one additional VPC, run:

    $ gcloud redis clusters add-cluster-endpoints my-redis-cluster \
        add-cluster-endpoints \
        --cluster-endpoint='["psc-connection":[{"psc-connection-id":"$ID\
    ","address":"$IP","network":"projects/$PROJECT/global/networks/$NETW\
    ORK","forwarding-rule":"projects/$PROJECT/regions/us-east1/forwardin\
    gRules/$FR_NAME","service-attachment":"projects/$PROJECT/regions/$RE\
    GION/serviceAttachments/$SA_NAME"},{$ADDITIONAL_PSC_CONNECTION}]]' \
        --cluster_endpoint=$ADDITIONAL_CLUSTER_ENDPOINT \
        $PSCConnectionID SHOULD be extracted from forwarding rules. \
        E.g. 75311697652483351
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/redis/clusters/add-cluster-endpoints)

---
### `gcloud redis clusters create`

Create a new Memorystore for Redis Cluster instance

Create a new Memorystore for Redis Cluster instance, and uses Private
Service Connect service connectivity automation to automate connectivity
for instances.

This command can fail for the following reasons:
  o A cluster with the same name already exists.
  o The active account does not have permission to create clusters.
  o Some required APIs not enabled yet.
  o No connection policy defined yet on the network and in the region a
    cluster will be created.
  o Miss the steps for creating and configuring a service account (to
    grant permissions) in both host project and service project, if a
    shared VPC network is used.

Refer to
https://cloud.google.com/memorystore/docs/cluster/networking#prerequisites_required_before_creating_a_cluster
for prerequisites.

**Synopsis:**
```
gcloud redis clusters create (CLUSTER : --region=REGION)
    [--aof-append-fsync=AOF_APPEND_FSYNC] [--async] [--auth-mode=AUTH_MODE]
    [--automated-backup-mode=AUTOMATED_BACKUP_MODE]
    [--automated-backup-start-time=AUTOMATED_BACKUP_START_TIME]
    [--automated-backup-ttl=AUTOMATED_BACKUP_TTL]
    [--cross-cluster-replication-role=CROSS_CLUSTER_REPLICATION_ROLE]
    [--deletion-protection] [--kms-key=KMS_KEY] [--labels=[KEY=VALUE,...]]
    [--maintenance-window-day=MAINTENANCE_WINDOW_DAY]
    [--maintenance-window-hour=MAINTENANCE_WINDOW_HOUR] [--network=NETWORK]
    [--node-type=NODE_TYPE] [--persistence-mode=PERSISTENCE_MODE]
    [--primary-cluster=PRIMARY_CLUSTER]
    [--rdb-snapshot-period=RDB_SNAPSHOT_PERIOD]
    [--rdb-snapshot-start-time=RDB_SNAPSHOT_START_TIME]
    [--redis-config=[KEY=VALUE,...]] [--replica-count=REPLICA_COUNT]
    [--shard-count=SHARD_COUNT]
    [--transit-encryption-mode=TRANSIT_ENCRYPTION_MODE] [--zone=ZONE]
    [--zone-distribution-mode=ZONE_DISTRIBUTION_MODE]
    [--import-gcs-object-uris=[IMPORT_GCS_OBJECT_URIS,...]
      | --import-managed-backup=IMPORT_MANAGED_BACKUP]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - Arguments and flags that specify the cluster you want
to create. Your cluster ID must be 1 to 63 characters and use only
lowercase letters, numbers, or hyphens. It must start with a lowercase
letter and end with a lowercase letter or number. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument cluster on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CLUSTER
     ID of the cluster or fully qualified identifier for the cluster.

     To set the cluster attribute:
     + provide the argument cluster on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the Redis region of the cluster. Overrides the default
     redis/region property value for this command invocation.

     To set the region attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property redis/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--aof-append-fsync` | one of: always Redis explicitly calls fsync for every write command |  | Fsync configuration. AOF_APPEND_FSYNC must be one of: always Redis explicitly calls fsync for every write command. everysec (default) Redis explicitly calls fsync every second. no Redis will not explicitly call fsync. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--auth-mode` | one of: disabled Authorization is disabled for the cluster |  | Available authorization mode of a Redis cluster. AUTH_MODE must be one of: disabled Authorization is disabled for the cluster. iam-auth IAM basic authorization is enabled for the cluster. |
| `--automated-backup-mode` | one of: disabled (default) Automated backup is disabled |  | Automated backup mode. AUTOMATED_BACKUP_MODE must be one of: disabled (default) Automated backup is disabled. enabled Automated backup is enabled. |
| `--automated-backup-start-time` | AUTOMATED_BACKUP_START_TIME |  | One-hour window when you want automated-backup operations to start. Specify the time in the format HH:00 on a 24-hour cycle in UTC time. |
| `--automated-backup-ttl` | AUTOMATED_BACKUP_TTL |  | Time to live for automated backups. A backup will be deleted automatically after the TTL is reached. It ranges from 1 day to 365 days. For example, "10d" for 10 days. If not specified, the default value is 35 days. |
| `--cross-cluster-replication-role` | CROSS_CLUSTER_REPLICATION_ROLE |  | The role of the cluster in cross cluster replication. CROSS_CLUSTER_REPLICATION_ROLE must be (only one value is supported): secondary Create a secondary cluster. |
| `--deletion-protection` |  |  | Enable deletion protection for the Redis Cluster. Use --deletion-protection/--no-deletion-protection to enable/disable it. |
| `--kms-key` | KMS_KEY |  | The resource name of the customer-managed encryption key (CMEK) to use for the cluster. It must use this format: projects/PROJECT_ID/locations/LOCATION/keyRings/KEY_RING/cryptoKeys/CRYPTO_KEY. The key must be in the same region as the cluster. Otherwise, the create operation fails. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--maintenance-window-day` | one of: friday, monday, saturday, sunday, thursday, tuesday, wednesday |  | Day of week when the window starts, e.g. sunday. MAINTENANCE_WINDOW_DAY must be one of: friday, monday, saturday, sunday, thursday, tuesday, wednesday. |
| `--maintenance-window-hour` | MAINTENANCE_WINDOW_HOUR |  | Hour of day (0 to 23) for the start of maintenance window, in UTC time zone. |
| `--network` | NETWORK |  | The network used to create your instance. It must use the format: projects/NETWORK_PROJECT_ID/global/networks/NETWORK_ID. The network ID used here must match the network ID used by the service connection policy. Otherwise, the create operation fails |
| `--node-type` | one of: redis-highmem-medium, redis-highmem-xlarge, redis-shared-core-nano, redis-standard-small |  | Node Type of the redis cluster Node. NODE_TYPE must be one of: redis-highmem-medium, redis-highmem-xlarge, redis-shared-core-nano, redis-standard-small. |
| `--persistence-mode` | PERSISTENCE_MODE |  | Operation mode for persistence. PERSISTENCE_MODE must be one of: aof AOF-based persistence disabled Persistence mode is disabled rdb RDB-based persistence |
| `--primary-cluster` | PRIMARY_CLUSTER |  | The primary cluster that the secondary cluster will replicate from. It must use the format: projects/PROJECT_ID/locations/REGION/clusters/CLUSTER_ID. It must refer to an existing cluster. Otherwise, the create operation fails. |
| `--rdb-snapshot-period` | RDB_SNAPSHOT_PERIOD |  | Attempted period between RDB snapshots. RDB_SNAPSHOT_PERIOD must be one of: 12h 12 hours 1h 1 hour 24h (default) 24 hours 6h 6 hours |
| `--rdb-snapshot-start-time` | RDB_SNAPSHOT_START_TIME |  | Date and time of the first snapshot in the ISO 1801 format, and alignment time for future snapshots. For example, 2024-01-01T01:00:00Z. If not specified, the current time will be used. |
| `--redis-config` | [KEY=VALUE,...] |  | A list of Redis config KEY=VALUE pairs to set on the Redis Cluster according to http://redis.io/topics/config. Currently the supported Redis configs are: maxmemory-clients, maxmemory, maxmemory-policy, notify-keyspace-events, slowlog-log-slower-than, maxclients. |
| `--replica-count` | REPLICA_COUNT |  | The replica count of each shard. |
| `--shard-count` | SHARD_COUNT |  | The shard count of the cluster. |
| `--transit-encryption-mode` | one of: disabled In-transit encryption is disabled for the cluster |  | Transit encryption mode used for the Redis cluster. If not provided, encryption is disabled for the cluster. TRANSIT_ENCRYPTION_MODE must be one of: disabled In-transit encryption is disabled for the cluster. server-authentication The cluster uses server managed encryption for in-transit encryption. |
| `--zone` | ZONE |  | The zone used to allocate the cluster nodes. Applicable only if the zone-distribution-mode is set to single-zone. |
| `--zone-distribution-mode` | one of: multi-zone Allocate cluster nodes across multiple zones |  | Determines how the cluster nodes are distributed across zones. ZONE_DISTRIBUTION_MODE must be one of: multi-zone Allocate cluster nodes across multiple zones. single-zone Allocate cluster nodes in a single zone. |


**Examples:**
```bash
To create a cluster with name my-redis-cluster in region us-central1 with 3
shards and with a discovery endpoint created on network "default", run:

    $ gcloud redis clusters create my-redis-cluster \
        --region=us-central1 --shard-count=3 \
        --network=projects/NETWORK_PROJECT_ID/global/networks/default
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/redis/clusters/create)

---
### `gcloud redis clusters create-backup`

Create a backup of a Redis cluster

Create a backup of a Redis cluster. The backup can be used to seed a new
cluster or exported to a Google Cloud Storage bucket.

The created backup will be added into the backup collection associated with
the cluster. Describe the cluster to get the backup collection name.

**Synopsis:**
```
gcloud redis clusters create-backup (CLUSTER : --region=REGION) [--async]
    [--backup-id=BACKUP_ID] [--ttl=TTL] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - Arguments and flags that specify the Memorystore Redis
cluster to create a backup for. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument cluster on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CLUSTER
     ID of the cluster or fully qualified identifier for the cluster.

     To set the cluster attribute:
     + provide the argument cluster on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the Redis region of the cluster. Overrides the default
     redis/region property value for this command invocation.

     To set the region attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property redis/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--backup-id` | BACKUP_ID |  | The ID of the backup. |
| `--ttl` | TTL |  | The time to live for the backup. The backup will be deleted automatically after the TTL is reached. For example, "10d" for 10 days. The minimum value is 1 day. If not specified, the default value is 100 years. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/redis/clusters/create-backup)

---
### `gcloud redis clusters delete`

Delete a Memorystore for Redis Cluster instance

Delete a Memorystore for Redis Cluster instance.

This command can fail for the following reasons:
  o The cluster specified does not exist.
  o The active account does not have permission to access the given
    cluster.

**Synopsis:**
```
gcloud redis clusters delete (CLUSTER : --region=REGION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - Arguments and flags that specify the cluster you want
to delete. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument cluster on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CLUSTER
     ID of the cluster or fully qualified identifier for the cluster.

     To set the cluster attribute:
     + provide the argument cluster on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the Redis region of the cluster. Overrides the default
     redis/region property value for this command invocation.

     To set the region attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property redis/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a cluster with the name my-redis-cluster in your default region,
run:

    $ gcloud redis clusters delete my-redis-cluster
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/redis/clusters/delete)

---
### `gcloud redis clusters describe`

Show metadata for a Memorystore for Redis Cluster instance

Show metadata for a Memorystore for Redis Cluster instance.

Displays all metadata associated with a cluster given a valid cluster name.

This command can fail for the following reasons:
  o The cluster specified does not exist.
  o The active account does not have permission to access the given
    cluster.

**Synopsis:**
```
gcloud redis clusters describe (CLUSTER : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - Arguments and flags that specify the cluster you want
to describe. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument cluster on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CLUSTER
     ID of the cluster or fully qualified identifier for the cluster.

     To set the cluster attribute:
     + provide the argument cluster on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the Redis region of the cluster. Overrides the default
     redis/region property value for this command invocation.

     To set the region attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property redis/region.
```

**Examples:**
```bash
To display the metadata for a cluster with the name my-redis-cluster in the
default region, run:

    $ gcloud redis clusters describe my-redis-cluster
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/redis/clusters/describe)

---
### `gcloud redis clusters detach`

Detach a secondary cluster

Detach a secondary cluster from the primary cluster.

After detachment, the secondary cluster becomes an independent cluster,
i.e. it stops replicating from the primary cluster and it now accepts both
read and write requests.

This command is only supported on secondary clusters.

**Synopsis:**
```
gcloud redis clusters detach (CLUSTER : --region=REGION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - Arguments and flags that specify the Memorystore Redis
cluster you want to update. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument cluster on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CLUSTER
     ID of the cluster or fully qualified identifier for the cluster.

     To set the cluster attribute:
     + provide the argument cluster on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the Redis region of the cluster. Overrides the default
     redis/region property value for this command invocation.

     To set the region attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property redis/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To detach a secondary cluster with name my-secondary-cluster in region
us-central1, run:

    $ gcloud redis clusters detach my-secondary-cluster \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/redis/clusters/detach)

---
### `gcloud redis clusters detach-secondaries`

Detach one or more secondary clusters from the primary cluster

Detach one or more secondary clusters from the primary cluster.

After detachment, the secondary clusters become independent clusters, i.e.
they stop replicating from the primary cluster and will now accept both
read and write requests.

This command is only supported on primary clusters.

**Synopsis:**
```
gcloud redis clusters detach-secondaries (CLUSTER : --region=REGION)
    --clusters-to-detach=CLUSTERS_TO_DETACH [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - Arguments and flags that specify the Memorystore Redis
cluster you want to update. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument cluster on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CLUSTER
     ID of the cluster or fully qualified identifier for the cluster.

     To set the cluster attribute:
     + provide the argument cluster on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the Redis region of the cluster. Overrides the default
     redis/region property value for this command invocation.

     To set the region attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property redis/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--clusters-to-detach` | CLUSTERS_TO_DETACH |  | Comma separated list of secondary clusters to detach from the primary cluster. Each element in the list should be in the format: projects/PROJECT_ID/locations/REGION/clusters/CLUSTER_ID. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To detach the secondary clusters my-secondary-cluster1 and
my-secondary-cluster2 from the primary cluster my-primary-cluster, run:

    $ gcloud redis clusters detach-secondaries my-primary-cluster \
        --region=us-central1 \
        --clusters-to-detach=projects/my-project/locations/us-east1/\
    clusters/my-secondary-cluster1,projects/my-project/locations/\
    asia-east1/clusters/my-secondary-cluster2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/redis/clusters/detach-secondaries)

---
### `gcloud redis clusters get-cluster-certificate-authority`

Get the certificate authority information for a Memorystore for Redis Cluster instance

Get the certificate authority information for a Memorystore for Redis
Cluster instance.

This command can fail for the following reasons:
  o The cluster specified does not exist.
  o The active account does not have permission to access the given
    cluster.

**Synopsis:**
```
gcloud redis clusters get-cluster-certificate-authority
    (CLUSTER : --region=REGION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - Arguments and flags that specify the cluster. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument cluster on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CLUSTER
     ID of the cluster or fully qualified identifier for the cluster.

     To set the cluster attribute:
     + provide the argument cluster on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the Redis region of the cluster. Overrides the default
     redis/region property value for this command invocation.

     To set the region attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property redis/region.
```

**Examples:**
```bash
To get the metadata for a cluster with the name my-redis-cluster in the
default region, run:

    $ gcloud redis clusters get-cluster-certificate-authority \
        my-redis-cluster
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/redis/clusters/get-cluster-certificate-authority)

---
### `gcloud redis clusters list`

List Memorystore for Redis Cluster instances

List all clusters under the specified project and region.

To specify the maximum number of clusters to list, use the --limit flag.

**Synopsis:**
```
gcloud redis clusters list [--region=REGION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[* set the property core/project.]_ ID of the region or fully qualified identifier for the region. To set the region attribute: + provide the argument --region on the command line; + set the property redis/region. |


**Examples:**
```bash
To list up to five clusters, run:

    $ gcloud redis clusters list --limit=5
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/redis/clusters/list)

---
### `gcloud redis clusters remove-cluster-endpoints`

Remove existing Memorystore cluster endpoints

To remove one cluster endpoint from an existing Redis cluster, two PSC
connections MUST be removed as a pair: one to the Redis cluster's discovery
service attachment and the other to its additional service attachment.

Multiple cluster endpoints COULD be removed simultaneously.

This command can fail for the following reasons:
  o The cluster specified does not exist.
  o Some connections in the to be removed list do not exist.

**Synopsis:**
```
gcloud redis clusters remove-cluster-endpoints (CLUSTER : --region=REGION)
    --cluster-endpoint=[psc-connection=PSC-CONNECTION] [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - Arguments and flags that specify the Memorystore Redis
cluster you want to update. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument cluster on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CLUSTER
     ID of the cluster or fully qualified identifier for the cluster.

     To set the cluster attribute:
     + provide the argument cluster on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the Redis region of the cluster. Overrides the default
     redis/region property value for this command invocation.

     To set the region attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property redis/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cluster-endpoint` | [psc-connection=PSC-CONNECTION] |  | Required, Resource details of a redis cluster endpoint. psc-connection Sets psc-connection value. psc-connection-id Sets psc-connection-id value. Shorthand Example: --cluster-endpoint=psc-connection=[{psc-connection-id=string}] --cluster-endpoint=psc-connection=[{psc-connection-id=string}] JSON Example: --cluster-endpoint='[{"psc-connection": [{"psc-connection-id": "string"}]}]' File Example: --cluster-endpoint=path_to_file.(yaml\|json) |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To remove an endpoint from redis cluster, run:

    $ gcloud redis clusters remove-cluster-endpoints my-redis-cluster \
        remove-cluster-endpoints \
        --cluster-endpoint='["psc-connection":[{"psc-connection-id":"$PS\
    C_CONNECTION_ID"},{$ADDITIONAL_PSC_CONNECTION}]]' \
        --cluster_endpoint=$ADDITIONAL_CLUSTER_ENDPOINT \
        $PSCConnectionID SHOULD be extracted from forwarding rules. \
        E.g. 75311697652483351
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/redis/clusters/remove-cluster-endpoints)

---
### `gcloud redis clusters reschedule-maintenance`

Reschedule maintenance window for a Memorystore for Redis Cluster instance

Reschedule maintenance window for a Memorystore for Redis Cluster instance.

**Synopsis:**
```
gcloud redis clusters reschedule-maintenance (CLUSTER : --region=REGION)
    --reschedule-type=RESCHEDULE_TYPE [--async]
    [--schedule-time=SCHEDULE_TIME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - Arguments and flags that specify the Cloud Memorystore
for Redis cluster instance you want to reschedule maintenance window. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument cluster on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CLUSTER
     ID of the cluster or fully qualified identifier for the cluster.

     To set the cluster attribute:
     + provide the argument cluster on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the Redis region of the cluster. Overrides the default
     redis/region property value for this command invocation.

     To set the region attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property redis/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--reschedule-type` | one of: immediate Reschedule the maintenance to perform now |  | Reschedule type to use for the reschedule maintenance window. RESCHEDULE_TYPE must be one of: immediate Reschedule the maintenance to perform now. specific-time Reschedule the maintenance to a specific time. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--schedule-time` | SCHEDULE_TIME |  | Time in RFC3339 format, for example: 2012-11-15T16:19:00.094Z |


**Examples:**
```bash
To reschedule maintenance window for an instance with the name
'my-redis-cluster' in region 'us-central-1' with immediate, run:

    $ gcloud redis clusters reschedule-maintenance my-redis-cluster \
        --region=us-central1 --reschedule-type=IMMEDIATE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/redis/clusters/reschedule-maintenance)

---
### `gcloud redis clusters switchover`

Switchover to a secondary cluster

This command promotes the secondary cluster to become the new primary
cluster. The old primary and other secondary clusters will automatically
become the secondary clusters of this cluster.

After the successful completion of this operation, the new primary cluster
will accept both read and write requests.

This command is only supported on secondary clusters.

**Synopsis:**
```
gcloud redis clusters switchover (CLUSTER : --region=REGION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - Arguments and flags that specify the Memorystore Redis
cluster you want to update. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument cluster on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CLUSTER
     ID of the cluster or fully qualified identifier for the cluster.

     To set the cluster attribute:
     + provide the argument cluster on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the Redis region of the cluster. Overrides the default
     redis/region property value for this command invocation.

     To set the region attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property redis/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To switchover to a secondary cluster with name my-secondary-cluster in
region us-central1, run:

    $ gcloud redis clusters switchover my-secondary-cluster \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/redis/clusters/switchover)

---
### `gcloud redis clusters update`

Update Memorystore Cluster for Redis instance

Update the metadata and/or configuration parameters of a Redis cluster.

This command can fail for the following reasons:
  o The cluster specified does not exist.
  o The active account does not have permission to update the given
    cluster.

**Synopsis:**
```
gcloud redis clusters update (CLUSTER : --region=REGION)
    [--aof-append-fsync=AOF_APPEND_FSYNC] [--async]
    [--automated-backup-mode=AUTOMATED_BACKUP_MODE]
    [--automated-backup-start-time=AUTOMATED_BACKUP_START_TIME]
    [--automated-backup-ttl=AUTOMATED_BACKUP_TTL] [--deletion-protection]
    [--maintenance-version=MAINTENANCE_VERSION] [--node-type=NODE_TYPE]
    [--persistence-mode=PERSISTENCE_MODE]
    [--rdb-snapshot-period=RDB_SNAPSHOT_PERIOD]
    [--rdb-snapshot-start-time=RDB_SNAPSHOT_START_TIME]
    [--remove-redis-config=[KEY,...]] [--replica-count=REPLICA_COUNT]
    [--shard-count=SHARD_COUNT] [--simulate-maintenance-event]
    [--update-labels=[KEY=VALUE,...]] [--update-redis-config=KEY=VALUE]
    [--clear-labels | --remove-labels=[KEY,...]]
    [--maintenance-window-any
      | --maintenance-window-day=MAINTENANCE_WINDOW_DAY
      --maintenance-window-hour=MAINTENANCE_WINDOW_HOUR]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - Arguments and flags that specify the Memorystore Redis
cluster you want to update. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument cluster on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CLUSTER
     ID of the cluster or fully qualified identifier for the cluster.

     To set the cluster attribute:
     + provide the argument cluster on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the Redis region of the cluster. Overrides the default
     redis/region property value for this command invocation.

     To set the region attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property redis/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--aof-append-fsync` | one of: always Redis explicitly calls fsync for every write command |  | Fsync configuration. AOF_APPEND_FSYNC must be one of: always Redis explicitly calls fsync for every write command. everysec (default) Redis explicitly calls fsync every second. no Redis will not explicitly call fsync. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--automated-backup-mode` | one of: disabled (default) Automated backup is disabled |  | Automated backup mode. AUTOMATED_BACKUP_MODE must be one of: disabled (default) Automated backup is disabled. enabled Automated backup is enabled. |
| `--automated-backup-start-time` | AUTOMATED_BACKUP_START_TIME |  | One-hour window when you want automated-backup operations to start. Specify the time in the format HH:00 on a 24-hour cycle in UTC time. |
| `--automated-backup-ttl` | AUTOMATED_BACKUP_TTL |  | Time to live for automated backups. A backup will be deleted automatically after the TTL is reached. It ranges from 1 day to 365 days. For example, "10d" for 10 days. If not specified, the default value is 35 days. |
| `--deletion-protection` |  |  | Enable deletion protection for the Redis Cluster. Use --deletion-protection/--no-deletion-protection to enable/disable it. |
| `--maintenance-version` | MAINTENANCE_VERSION |  | The maintenance version of the cluster. |
| `--node-type` | one of: redis-highmem-medium, redis-highmem-xlarge, redis-shared-core-nano, redis-standard-small |  | Node Type of the redis cluster Node. NODE_TYPE must be one of: redis-highmem-medium, redis-highmem-xlarge, redis-shared-core-nano, redis-standard-small. |
| `--persistence-mode` | PERSISTENCE_MODE |  | Operation mode for persistence. PERSISTENCE_MODE must be one of: aof AOF-based persistence disabled Persistence mode is disabled rdb RDB-based persistence |
| `--rdb-snapshot-period` | RDB_SNAPSHOT_PERIOD |  | Attempted period between RDB snapshots. RDB_SNAPSHOT_PERIOD must be one of: 12h 12 hours 1h 1 hour 24h (default) 24 hours 6h 6 hours |
| `--rdb-snapshot-start-time` | RDB_SNAPSHOT_START_TIME |  | Date and time of the first snapshot in the ISO 1801 format, and alignment time for future snapshots. For example, 2024-01-01T01:00:00Z. If not specified, the current time will be used. |
| `--remove-redis-config` | [KEY,...] |  | A list of Redis Cluster config parameters to remove. Removing a non-existent config parameter is silently ignored. |
| `--replica-count` | REPLICA_COUNT |  | The replica count of each shard. |
| `--shard-count` | SHARD_COUNT |  | The shard count of the cluster. |
| `--simulate-maintenance-event` |  |  | Trigger a simulation for maintenance event. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--update-redis-config` | KEY=VALUE |  | A list of Redis Cluster config KEY=VALUE pairs to update. If a config parameter is already set, its value is modified; otherwise a new Redis config parameter is added. |


**Examples:**
```bash
To update a Redis cluster with 5 shard and 2 replica, run:

    $ gcloud redis clusters update my-redis-cluster --shard-count=5 \
        --replica-count=2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/redis/clusters/update)

---

## `gcloud redis clusters backup-collections` — manage backup collections of Memorystore for Redis Cluster instances
### `gcloud redis clusters backup-collections describe`

Show metadata for a backup collection

Show metadata for a backup collection.

Displays all metadata associated with a backup collection.

This command can fail for the following reasons:
  o The backup collection specified does not exist.
  o The active account does not have permission to access the given
    backup collection.

**Synopsis:**
```
gcloud redis clusters backup-collections describe
    (BACKUP_COLLECTION : --region=REGION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup collection resource - Arguments and flags that specify the backup
collection you want to describe. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument backup_collection on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP_COLLECTION
     ID of the backup collection or fully qualified identifier for the
     backup collection.

     To set the backup_collection attribute:
     + provide the argument backup_collection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the Redis region of the backup collection. Overrides the
     default redis/region property value for this command invocation.

     To set the region attribute:
     + provide the argument backup_collection on the command line with a
       fully specified name;
     + provide the argument --region on the command line;
     + set the property redis/region.
```

**Examples:**
```bash
To display the metadata for a backup collection with the name
my-backup-collection in the us-central1 region, run:

    $ {commmand} my-backup-collection --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/redis/clusters/backup-collections/describe)

---
### `gcloud redis clusters backup-collections list`

List backup collections in a region

List all backup collections under the specified project and region.

To specify the maximum number of results, use the --limit flag.

**Synopsis:**
```
gcloud redis clusters backup-collections list [--region=REGION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[* set the property core/project.]_ ID of the region or fully qualified identifier for the region. To set the region attribute: + provide the argument --region on the command line; + set the property redis/region. |


**Examples:**
```bash
To list up to 5 backup collections in the us-central1 region, run:

    $ gcloud redis clusters backup-collections list \
        --region=us-central1 --limit=5
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/redis/clusters/backup-collections/list)

---

## `gcloud redis clusters backups` — manage backups of Memorystore for Redis Cluster instances
### `gcloud redis clusters backups delete`

Delete a Memorystore for Redis Cluster backup

Delete a Memorystore for Redis Cluster backup.

This command can fail for the following reasons:
  o The backup specified does not exist.
  o The active account does not have permission to access the given
    backup.

**Synopsis:**
```
gcloud redis clusters backups delete
    (BACKUP : --backup-collection=BACKUP_COLLECTION --region=REGION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - Arguments and flags that specify the Redis backup you
want to delete. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP
     ID of the backup or fully qualified identifier for the backup.

     To set the backup attribute:
     + provide the argument backup on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --backup-collection=BACKUP_COLLECTION
     The name of the Redis cluster backup collection.

     To set the backup-collection attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --backup-collection on the command line.

  --region=REGION
     The name of the Redis region of the backup. Overrides the default
     redis/region property value for this command invocation.

     To set the region attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property redis/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a backup with the name my-backup under backup collection
my-backup-collection in us-central1 region, run:

    $ gcloud redis clusters backups delete my-backup \
        --backup-collection=my-backup-collection --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/redis/clusters/backups/delete)

---
### `gcloud redis clusters backups describe`

Show metadata for a Memorystore for Redis Cluster backup

Show metadata for a Memorystore for Redis Cluster backup.

Displays all metadata associated with a backup given a valid backup name.

This command can fail for the following reasons:
  o The backup specified does not exist.
  o The active account does not have permission to access the given
    backup.

**Synopsis:**
```
gcloud redis clusters backups describe
    (BACKUP : --backup-collection=BACKUP_COLLECTION --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - Arguments and flags that specify the backup you want to
describe. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP
     ID of the backup or fully qualified identifier for the backup.

     To set the backup attribute:
     + provide the argument backup on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --backup-collection=BACKUP_COLLECTION
     The name of the Redis cluster backup collection.

     To set the backup-collection attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --backup-collection on the command line.

  --region=REGION
     The name of the Redis region of the backup. Overrides the default
     redis/region property value for this command invocation.

     To set the region attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property redis/region.
```

**Examples:**
```bash
To display the metadata for a backup named my-backup, under my-collection
backup collection, in us-central1 region, run:

    $ gcloud redis clusters backups describe my-backup \
        --backup_collection=my-collection --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/redis/clusters/backups/describe)

---
### `gcloud redis clusters backups export`

Export a Redis cluster backup to a Google Cloud Storage bucket

This command exports a Redis cluster backup to a Google Cloud Storage
bucket. A new folder will be created in the bucket with the backup name.
And the backup files will be stored in the folder.

**Synopsis:**
```
gcloud redis clusters backups export
    (BACKUP : --backup-collection=BACKUP_COLLECTION --region=REGION)
    --gcs-bucket=GCS_BUCKET [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - Arguments and flags that specify the Redis backup you
want to export. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP
     ID of the backup or fully qualified identifier for the backup.

     To set the backup attribute:
     + provide the argument backup on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --backup-collection=BACKUP_COLLECTION
     The name of the Redis cluster backup collection.

     To set the backup-collection attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --backup-collection on the command line.

  --region=REGION
     The name of the Redis region of the backup. Overrides the default
     redis/region property value for this command invocation.

     To set the region attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property redis/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--gcs-bucket` | GCS_BUCKET |  | The name of the Google Cloud Storage bucket to export the backup to. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To export a backup with name my-backup under backup collection
my-collection in us-central region to my-bucket Google Cloud Storage
bucket, run:

    $ gcloud redis clusters backups export my-backup \
        --backup-collection=my-collection --region=us-central1 \
        --bucket-name=my-bucket
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/redis/clusters/backups/export)

---
### `gcloud redis clusters backups list`

List backups under a backup collection in a region

List backups under a backup collection in a region.

To specify the maximum number of results, use the --limit flag.

**Synopsis:**
```
gcloud redis clusters backups list
    (--backup-collection=BACKUP_COLLECTION : --region=REGION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--backup-collection` | BACKUP_COLLECTION |  | _[This must be specified.]_ ID of the backup collection or fully qualified identifier for the backup collection. To set the backup-collection attribute: + provide the argument --backup-collection on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--region` | REGION |  | _[This must be specified.]_ The name of the Redis region of the backup collection. Overrides the default redis/region property value for this command invocation. To set the region attribute: + provide the argument --backup-collection on the command line with a fully specified name; + provide the argument --region on the command line; + set the property redis/region. |


**Examples:**
```bash
To list up to 5 backups in the us-central1 region, run:

    $ gcloud redis clusters backups list \
        --backup-collection=my-collection --region=us-central1 --limit=5
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/redis/clusters/backups/list)

---
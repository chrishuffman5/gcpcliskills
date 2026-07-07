# gcloud compute target-pools

control Compute Engine target pools for network load balancing

### `gcloud compute target-pools add-health-checks`

Add a legacy HTTP health check to a target pool

gcloud compute target-pools add-health-checks is used to add a legacy HTTP
health check to a target pool. Legacy health checks are used to determine
the health status of instances in the target pool. Only one health check
can be attached to a target pool, so this command will fail if there as
already a health check attached to the target pool. For more information on
health checks and load balancing, see
https://cloud.google.com/compute/docs/load-balancing-and-autoscaling/

**Synopsis:**
```
gcloud compute target-pools add-health-checks NAME
    --http-health-check=HTTP_HEALTH_CHECK [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of the target pool to which to add the health check.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--http-health-check` | HTTP_HEALTH_CHECK |  | Specifies an HTTP health check object to add to the target pool. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the target pool to add health checks to. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-pools/add-health-checks)

---
### `gcloud compute target-pools add-instances`

Add instances to a target pool

gcloud compute target-pools add-instances is used to add one or more
instances to a target pool. For more information on health checks and load
balancing, see
https://cloud.google.com/compute/docs/load-balancing-and-autoscaling/

**Synopsis:**
```
gcloud compute target-pools add-instances NAME
    --instances=INSTANCE,[INSTANCE,...] [--instances-zone=INSTANCES_ZONE]
    [--region=REGION] [--zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of the target pool to which to add the instances.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instances` | INSTANCE,[INSTANCE,...] |  | Specifies a list of instances to add to the target pool. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instances-zone` | INSTANCES_ZONE |  | Zone of the instances to add to the target pool. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |
| `--region` | REGION |  | Region of the target pool to operate on. If not specified, it will be set to the region of the instances. Overrides the default compute/region property value for this command invocation. |
| `--zone` | ZONE |  | Zone of the instances to add to the target pool. DEPRECATED, use --instances-zone. If not specified, you will be prompted to select a zone. Overrides the default compute/zone property value for this command invocation. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-pools/add-instances)

---
### `gcloud compute target-pools create`

Define a load-balanced pool of virtual machine instances

gcloud compute target-pools create is used to create a target pool. A
target pool resource defines a group of instances that can receive incoming
traffic from forwarding rules. When a forwarding rule directs traffic to a
target pool, Compute Engine picks an instance from the target pool based on
a hash of the source and destination IP addresses and ports. For more
information on load balancing, see
https://cloud.google.com/compute/docs/load-balancing-and-autoscaling/

To add instances to a target pool, use 'gcloud compute target-pools
add-instances'.

**Synopsis:**
```
gcloud compute target-pools create NAME [--backup-pool=BACKUP_POOL]
    [--description=DESCRIPTION] [--failover-ratio=FAILOVER_RATIO]
    [--health-check=HEALTH_CHECK] [--http-health-check=HTTP_HEALTH_CHECK]
    [--region=REGION] [--session-affinity=SESSION_AFFINITY; default="NONE"]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of the target pool.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--backup-pool` | BACKUP_POOL |  | Together with --failover-ratio, this flag defines the fallback behavior of the target pool (primary pool) to be created by this command. If the ratio of the healthy instances in the primary pool is at or below the specified --failover-ratio value, then traffic arriving at the load-balanced IP address will be directed to the backup pool. If this flag is provided, then --failover-ratio is required. |
| `--description` | DESCRIPTION |  | An optional description of this target pool. |
| `--failover-ratio` | FAILOVER_RATIO |  | Together with --backup-pool, defines the fallback behavior of the target pool (primary pool) to be created by this command. If the ratio of the healthy instances in the primary pool is at or below this number, traffic arriving at the load-balanced IP address will be directed to the backup pool. For example, if 0.4 is chosen as the failover ratio, then traffic will fail over to the backup pool if more than 40% of the instances become unhealthy. If not set, the traffic will be directed the instances in this pool in the force mode, where traffic will be spread to the healthy instances with the best effort, or to all instances when no instance is healthy. If this flag is provided, then --backup-pool is required. |
| `--health-check` | HEALTH_CHECK |  | DEPRECATED, use --http-health-check. Specifies an HTTP health check resource to use to determine the health of instances in this pool. If no health check is specified, traffic will be sent to all instances in this target pool as if the instances were healthy, but the health status of this pool will appear as unhealthy as a warning that this target pool does not have a health check. |
| `--http-health-check` | HTTP_HEALTH_CHECK |  | Specifies an HTTP health check resource to use to determine the health of instances in this pool. If no health check is specified, traffic will be sent to all instances in this target pool as if the instances were healthy, but the health status of this pool will appear as unhealthy as a warning that this target pool does not have a health check. |
| `--region` | REGION |  | Region of the target pool to create. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--session-affinity` | one of: CLIENT_IP Route requests to instances based on the hash of the client's IP address | NONE | The type of session affinity to use. Supports both TCP and UDP. SESSION_AFFINITY must be one of: CLIENT_IP Route requests to instances based on the hash of the client's IP address. CLIENT_IP_PROTO Connections from the same client IP with the same IP protocol will go to the same VM in the pool while that VM remains healthy. NONE Session affinity is disabled. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-pools/create)

---
### `gcloud compute target-pools delete`

Delete target pools

gcloud compute target-pools delete deletes one or more Compute Engine
target pools.

**Synopsis:**
```
gcloud compute target-pools delete NAME [NAME ...] [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME [NAME ...]
   Names of the target pools to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the target pools to delete. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-pools/delete)

---
### `gcloud compute target-pools describe`

Describe a Compute Engine target pool

gcloud compute target-pools describe displays all data associated with a
Compute Engine target pool in a project.

**Synopsis:**
```
gcloud compute target-pools describe NAME [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of the target pool.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the target pool to describe. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-pools/describe)

---
### `gcloud compute target-pools get-health`

Get the health of instances in a target pool

gcloud compute target-pools get-health displays the health of instances in
a target pool.

**Synopsis:**
```
gcloud compute target-pools get-health NAME [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of the target pool.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the target pool to get health information for. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-pools/get-health)

---
### `gcloud compute target-pools list`

List Google Compute Engine target pools

gcloud compute target-pools list displays all Google Compute Engine target
pools in a project.

By default, target pools from all regions are listed. The results can be
narrowed down using a filter: --filter="region:( REGION ... )".

**Synopsis:**
```
gcloud compute target-pools list [NAME ...] [--regexp=REGEXP, -r REGEXP]
    [--regions=REGION,[REGION,...]] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[NAME ...]
   (DEPRECATED) If provided, show details for the specified names and/or
   URIs of resources.

   Argument NAME is deprecated. Use --filter="name=( 'NAME' ... )"
   instead.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--regexp` | REGEXP, -r REGEXP |  | (DEPRECATED) Regular expression to filter the names of the results on. Any names that do not match the entire regular expression will be filtered out. Flag --regexp is deprecated. Use --filter="name~'REGEXP'" instead. |
| `--regions` | REGION,[REGION,...] |  | If provided, only resources from the given regions are queried. |


**Examples:**
```bash
To list all target pools in a project in table form, run:

    $ gcloud compute target-pools list

To list the URIs of all target pools in a project, run:

    $ gcloud compute target-pools list --uri

To list all target pools in the us-central1 and europe-west1 regions, run:

    $ gcloud compute target-pools list \
        --filter="region:( us-central1 europe-west1 )"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-pools/list)

---
### `gcloud compute target-pools remove-health-checks`

Remove an HTTP health check from a target pool

gcloud compute target-pools remove-health-checks is used to remove an HTTP
health check from a target pool. Health checks are used to determine the
health status of instances in the target pool. For more information on
health checks and load balancing, see
https://cloud.google.com/compute/docs/load-balancing-and-autoscaling/

**Synopsis:**
```
gcloud compute target-pools remove-health-checks NAME
    --http-health-check=HTTP_HEALTH_CHECK [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of the target pool from which to remove the health check.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--http-health-check` | HTTP_HEALTH_CHECK |  | Specifies an HTTP health check object to remove from the target pool. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the target pool to remove health checks from. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-pools/remove-health-checks)

---
### `gcloud compute target-pools remove-instances`

Remove instances from a target pool

gcloud compute target-pools remove-instances is used to remove one or more
instances from a target pool. For more information on health checks and
load balancing, see
https://cloud.google.com/compute/docs/load-balancing-and-autoscaling/

**Synopsis:**
```
gcloud compute target-pools remove-instances NAME
    --instances=INSTANCE,[INSTANCE,...] [--instances-zone=INSTANCES_ZONE]
    [--region=REGION] [--zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of the target pool from which to remove the instances.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instances` | INSTANCE,[INSTANCE,...] |  | Specifies a list of instances to remove from the target pool. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instances-zone` | INSTANCES_ZONE |  | Zone of the instances to remove from the target pool. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |
| `--region` | REGION |  | Region of the target pool to operate on. If not specified, it will be set to the region of the instances. Overrides the default compute/region property value for this command invocation. |
| `--zone` | ZONE |  | Zone of the instances to remove from the target pool. DEPRECATED, use --instances-zone. If not specified, you will be prompted to select a zone. Overrides the default compute/zone property value for this command invocation. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-pools/remove-instances)

---
### `gcloud compute target-pools set-backup`

Set a backup pool for a target pool

gcloud compute target-pools set-backup is used to set a backup target pool
for a primary target pool, which defines the fallback behavior of the
primary pool. If the ratio of the healthy instances in the primary pool is
at or below the specified --failover-ratio value, then traffic arriving at
the load-balanced IP address will be directed to the backup pool.

**Synopsis:**
```
gcloud compute target-pools set-backup NAME
    (--backup-pool=BACKUP_POOL | --no-backup-pool)
    [--failover-ratio=FAILOVER_RATIO] [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of the target pool for which to set the backup pool.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--backup-pool` | BACKUP_POOL |  | _[Exactly one of these must be specified:]_ Name of the target pool that will serve as backup. |
| `--no-backup-pool` |  |  | _[Exactly one of these must be specified:]_ Unsets the backup pool. This disables failover. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--failover-ratio` | FAILOVER_RATIO |  | The new failover ratio value for the target pool. This must be a float in the range of [0, 1]. |
| `--region` | REGION |  | Region of the target pool to set a backup pool for. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To cause TARGET-POOL (in region us-central1) to fail over to BACKUP-POOL
when more than half of the TARGET-POOL instances are unhealthy, run:

    $ gcloud compute target-pools set-backup TARGET-POOL \
        --backup-pool=BACKUP-POOL --failover-ratio=0.5 \
        --region=us-central1

To remove BACKUP-POOL as a backup to TARGET-POOL, run:

    $ gcloud compute target-pools set-backup TARGET-POOL \
        --backup-pool='' --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-pools/set-backup)

---
### `gcloud compute target-pools update`

Update a Compute Engine target pool

gcloud compute target-pools update updates a Compute Engine target pool.

**Synopsis:**
```
gcloud compute target-pools update NAME [--region=REGION]
    [--security-policy=SECURITY_POLICY]
    [--security-policy-region=SECURITY_POLICY_REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of the target pool.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the target pool to update. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--security-policy` | SECURITY_POLICY |  | The security policy that will be set for this target pool. To remove the policy from this target pool set the policy to an empty string. |
| `--security-policy-region` | SECURITY_POLICY_REGION |  | Region of the security policy to operate on. Overrides the default compute/region property value for this command invocation. |


**Examples:**
```bash
To update the security policy run this:

    $ gcloud compute target-pools update TARGET_POOL \
        --security-policy='my-policy'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-pools/update)

---
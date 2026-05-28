# gcloud dataproc clusters

create and manage Dataproc clusters

### `gcloud dataproc clusters create`

Create a cluster

Create a cluster.

**Synopsis:**
```
gcloud dataproc clusters create (CLUSTER : --region=REGION)
    [--action-on-failed-primary-workers=ACTION_ON_FAILED_PRIMARY_WORKERS]
    [--async] [--autoscaling-policy=AUTOSCALING_POLICY] [--bucket=BUCKET]
    [--cluster-type=TYPE] [--confidential-compute]
    [--dataproc-metastore=DATAPROC_METASTORE]
    [--delete-max-idle=DELETE_MAX_IDLE]
    [--driver-pool-accelerator=[type=TYPE,[count=COUNT],...]]
    [--driver-pool-boot-disk-size=DRIVER_POOL_BOOT_DISK_SIZE]
    [--driver-pool-boot-disk-type=DRIVER_POOL_BOOT_DISK_TYPE]
    [--driver-pool-id=DRIVER_POOL_ID]
    [--driver-pool-local-ssd-interface=DRIVER_POOL_LOCAL_SSD_INTERFACE]
    [--driver-pool-machine-type=DRIVER_POOL_MACHINE_TYPE]
    [--driver-pool-min-cpu-platform=PLATFORM]
    [--driver-pool-size=DRIVER_POOL_SIZE] [--enable-component-gateway]
    [--initialization-action-timeout=TIMEOUT; default="10m"]
    [--initialization-actions=CLOUD_STORAGE_URI,[...]]
    [--labels=[KEY=VALUE,...]]
    [--master-accelerator=[type=TYPE,[count=COUNT],...]]
    [--master-boot-disk-provisioned-iops=MASTER_BOOT_DISK_PROVISIONED_IOPS]
    [--master-boot-disk-provisioned-throughput=MASTER_BOOT_DISK_PROVISIONED_THROUGHPUT]
    [--master-boot-disk-size=MASTER_BOOT_DISK_SIZE]
    [--master-boot-disk-type=MASTER_BOOT_DISK_TYPE]
    [--master-local-ssd-interface=MASTER_LOCAL_SSD_INTERFACE]
    [--master-machine-type=MASTER_MACHINE_TYPE]
    [--master-min-cpu-platform=PLATFORM]
    [--min-secondary-worker-fraction=MIN_SECONDARY_WORKER_FRACTION]
    [--node-group=NODE_GROUP]
    [--num-driver-pool-local-ssds=NUM_DRIVER_POOL_LOCAL_SSDS]
    [--num-master-local-ssds=NUM_MASTER_LOCAL_SSDS]
    [--num-masters=NUM_MASTERS]
    [--num-secondary-worker-local-ssds=NUM_SECONDARY_WORKER_LOCAL_SSDS]
    [--num-worker-local-ssds=NUM_WORKER_LOCAL_SSDS]
    [--optional-components=[COMPONENT,...]]
    [--private-ipv6-google-access-type=PRIVATE_IPV6_GOOGLE_ACCESS_TYPE]
    [--properties=[PREFIX:PROPERTY=VALUE,...]]
    [--secondary-worker-accelerator=[type=TYPE,[count=COUNT],...]]
    [--secondary-worker-boot-disk-size=SECONDARY_WORKER_BOOT_DISK_SIZE]
    [--secondary-worker-boot-disk-type=SECONDARY_WORKER_BOOT_DISK_TYPE]
    [--secondary-worker-local-ssd-interface=SECONDARY_WORKER_LOCAL_SSD_INTERFACE]
    [--secondary-worker-machine-types=type=MACHINE_TYPE[,
      type=MACHINE_TYPE...][,rank=RANK]]
    [--secondary-worker-standard-capacity-base=SECONDARY_WORKER_STANDARD_CAPACITY_BASE]
    [--secondary-worker-standard-capacity-percent-above-base=SECONDARY_WORKER_STANDARD_CAPACITY_PERCENT_ABOVE_BASE]
    [--shielded-integrity-monitoring] [--shielded-secure-boot]
    [--shielded-vtpm] [--stop-max-idle=STOP_MAX_IDLE]
    [--temp-bucket=TEMP_BUCKET] [--tier=TIER]
    [--worker-accelerator=[type=TYPE,[count=COUNT],...]]
    [--worker-boot-disk-provisioned-iops=WORKER_BOOT_DISK_PROVISIONED_IOPS]
    [--worker-boot-disk-provisioned-throughput=WORKER_BOOT_DISK_PROVISIONED_THROUGHPUT]
    [--worker-boot-disk-size=WORKER_BOOT_DISK_SIZE]
    [--worker-boot-disk-type=WORKER_BOOT_DISK_TYPE]
    [--worker-local-ssd-interface=WORKER_LOCAL_SSD_INTERFACE]
    [--worker-min-cpu-platform=PLATFORM] [--zone=ZONE, -z ZONE]
    [--delete-expiration-time=DELETE_EXPIRATION_TIME
      | --delete-max-age=DELETE_MAX_AGE]
    [--gce-pd-kms-key=GCE_PD_KMS_KEY
      : --gce-pd-kms-key-keyring=GCE_PD_KMS_KEY_KEYRING
      --gce-pd-kms-key-location=GCE_PD_KMS_KEY_LOCATION
      --gce-pd-kms-key-project=GCE_PD_KMS_KEY_PROJECT]
    [--identity-config-file=IDENTITY_CONFIG_FILE
      | --secure-multi-tenancy-user-mapping=SECURE_MULTI_TENANCY_USER_MAPPING]
    [--image=IMAGE | --image-version=VERSION]
    [--kerberos-config-file=KERBEROS_CONFIG_FILE | --enable-kerberos
      --kerberos-root-principal-password-uri=KERBEROS_ROOT_PRINCIPAL_PASSWORD_URI [--kerberos-kms-key=KERBEROS_KMS_KEY : --kerberos-kms-key-keyring=KERBEROS_KMS_KEY_KEYRING --kerberos-kms-key-location=KERBEROS_KMS_KEY_LOCATION --kerberos-kms-key-project=KERBEROS_KMS_KEY_PROJECT]]
    [--kms-key=KMS_KEY : --kms-keyring=KMS_KEYRING
      --kms-location=KMS_LOCATION --kms-project=KMS_PROJECT]
    [--metadata=KEY=VALUE,[KEY=VALUE,...]
      --resource-manager-tags=KEY=VALUE,[KEY=VALUE,...]
      --scopes=SCOPE,[SCOPE,...] --service-account=SERVICE_ACCOUNT
      --tags=TAG,[TAG,...] --network=NETWORK | --subnet=SUBNET
      --reservation=RESERVATION
      --reservation-affinity=RESERVATION_AFFINITY; default="any"]
    [[--metric-sources=[METRIC_SOURCE,...]
      : --metric-overrides=[METRIC_SOURCE:INSTANCE:GROUP:METRIC,...]
      | --metric-overrides-file=METRIC_OVERRIDES_FILE]]
    [--no-address | --public-ip-address]
    [--single-node | --min-num-workers=MIN_NUM_WORKERS
      --num-secondary-workers=NUM_SECONDARY_WORKERS
      --num-workers=NUM_WORKERS
      --secondary-worker-type=TYPE; default="preemptible"]
    [--stop-expiration-time=STOP_EXPIRATION_TIME
      | --stop-max-age=STOP_MAX_AGE]
    [--worker-machine-type=WORKER_MACHINE_TYPE
      | --worker-machine-types=type=MACHINE_TYPE[,
      type=MACHINE_TYPE...][,rank=RANK]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - The name of the cluster to create. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

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
     Dataproc region for the cluster. Each Dataproc region constitutes an
     independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--action-on-failed-primary-workers` | ACTION_ON_FAILED_PRIMARY_WORKERS |  | Failure action to take when primary workers fail during cluster creation. ACTION_ON_FAILED_PRIMARY_WORKERS must be one of: DELETE delete the failed primary workers FAILURE_ACTION_UNSPECIFIED failure action is not specified NO_ACTION take no action |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--autoscaling-policy` | AUTOSCALING_POLICY |  | ID of the autoscaling policy or fully qualified identifier for the autoscaling policy. To set the autoscaling_policy attribute: * provide the argument --autoscaling-policy on the command line. |
| `--bucket` | BUCKET |  | The Google Cloud Storage bucket to use by default to stage job dependencies, miscellaneous config files, and job driver console output when using this cluster. |
| `--cluster-type` | one of: standard, single-node, zero-scale |  | The type of cluster. TYPE must be one of: standard, single-node, zero-scale. |
| `--confidential-compute` |  |  | Enables Confidential VM. See https://cloud.google.com/compute/confidential-vm/docs for more information. Note that Confidential VM can only be enabled when the machine types are N2D (https://cloud.google.com/compute/docs/machine-types#n2d_machine_types) and the image is SEV Compatible. |
| `--dataproc-metastore` | DATAPROC_METASTORE |  | Specify the name of a Dataproc Metastore service to be used as an external metastore in the format: "projects/{project-id}/locations/{region}/services/{service-name}". |
| `--delete-max-idle` | DELETE_MAX_IDLE |  | The duration after the last job completes to auto-delete the cluster, such as "2h" or "1d". See $ gcloud topic datetimes for information on duration formats. |
| `--driver-pool-accelerator` | [type=TYPE,[count=COUNT],...] |  | Attaches accelerators, such as GPUs, to the driver-pool instance(s). type The specific type of accelerator to attach to the instances, such as nvidia-tesla-t4 for NVIDIA T4. Use gcloud compute accelerator-types list to display available accelerator types. count The number of accelerators to attach to each instance. The default value is 1. |
| `--driver-pool-boot-disk-size` | DRIVER_POOL_BOOT_DISK_SIZE |  | The size of the boot disk. The value must be a whole number followed by a size unit of KB for kilobyte, MB for megabyte, GB for gigabyte, or TB for terabyte. For example, 10GB will produce a 10 gigabyte disk. The minimum size a boot disk can have is 10 GB. Disk size must be a multiple of 1 GB. |
| `--driver-pool-boot-disk-type` | DRIVER_POOL_BOOT_DISK_TYPE |  | The type of the boot disk. The value must be pd-balanced, pd-ssd, or pd-standard. |
| `--driver-pool-id` | DRIVER_POOL_ID |  | Custom identifier for the DRIVER Node Group being created. If not provided, a random string is generated. |
| `--driver-pool-local-ssd-interface` | DRIVER_POOL_LOCAL_SSD_INTERFACE |  | Interface to use to attach local SSDs to cluster driver pool node(s). |
| `--driver-pool-machine-type` | DRIVER_POOL_MACHINE_TYPE |  | The type of machine to use for the cluster driver pool nodes. Defaults to server-specified. |
| `--driver-pool-min-cpu-platform` | PLATFORM |  | When specified, the VM is scheduled on the host with a specified CPU architecture or a more recent CPU platform that's available in that zone. To list available CPU platforms in a zone, run: $ gcloud compute zones describe ZONE CPU platform selection may not be available in a zone. Zones that support CPU platform selection provide an availableCpuPlatforms field, which contains the list of available CPU platforms in the zone (see Availability of CPU platforms for more information). |
| `--driver-pool-size` | DRIVER_POOL_SIZE |  | The size of the cluster driver pool. |
| `--enable-component-gateway` |  |  | Enable access to the web UIs of selected components on the cluster through the component gateway. |
| `--initialization-action-timeout` | TIMEOUT | 10m | The maximum duration of each initialization action. See $ gcloud topic datetimes for information on duration formats. |
| `--initialization-actions` | CLOUD_STORAGE_URI,[...] |  | A list of Google Cloud Storage URIs of executables to run on each node in the cluster. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--master-accelerator` | [type=TYPE,[count=COUNT],...] |  | Attaches accelerators, such as GPUs, to the master instance(s). type The specific type of accelerator to attach to the instances, such as nvidia-tesla-t4 for NVIDIA T4. Use gcloud compute accelerator-types list to display available accelerator types. count The number of accelerators to attach to each instance. The default value is 1. |
| `--master-boot-disk-provisioned-iops` | MASTER_BOOT_DISK_PROVISIONED_IOPS |  | Indicates the IOPS (https://cloud.google.com/compute/docs/disks/hyperdisks#iops) to provision for the disk. This sets the limit for disk I/O operations per second. This is only supported if the bootdisk type is hyperdisk-balanced (https://cloud.google.com/compute/docs/disks/hyperdisks). |
| `--master-boot-disk-provisioned-throughput` | MASTER_BOOT_DISK_PROVISIONED_THROUGHPUT |  | Indicates the throughput (https://cloud.google.com/compute/docs/disks/hyperdisks#throughput) to provision for the disk. This sets the limit for throughput in MiB per second. This is only supported if the bootdisk type is hyperdisk-balanced (https://cloud.google.com/compute/docs/disks/hyperdisks). |
| `--master-boot-disk-size` | MASTER_BOOT_DISK_SIZE |  | The size of the boot disk. The value must be a whole number followed by a size unit of KB for kilobyte, MB for megabyte, GB for gigabyte, or TB for terabyte. For example, 10GB will produce a 10 gigabyte disk. The minimum size a boot disk can have is 10 GB. Disk size must be a multiple of 1 GB. |
| `--master-boot-disk-type` | MASTER_BOOT_DISK_TYPE |  | The type of the boot disk. The value must be pd-balanced, pd-ssd, or pd-standard. |
| `--master-local-ssd-interface` | MASTER_LOCAL_SSD_INTERFACE |  | Interface to use to attach local SSDs to master node(s) in a cluster. |
| `--master-machine-type` | MASTER_MACHINE_TYPE |  | The type of machine to use for the master. Defaults to server-specified. |
| `--master-min-cpu-platform` | PLATFORM |  | When specified, the VM is scheduled on the host with a specified CPU architecture or a more recent CPU platform that's available in that zone. To list available CPU platforms in a zone, run: $ gcloud compute zones describe ZONE CPU platform selection may not be available in a zone. Zones that support CPU platform selection provide an availableCpuPlatforms field, which contains the list of available CPU platforms in the zone (see Availability of CPU platforms for more information). |
| `--min-secondary-worker-fraction` | MIN_SECONDARY_WORKER_FRACTION |  | Minimum fraction of secondary worker nodes required to create the cluster. If it is not met, cluster creation will fail. Must be a decimal value between 0 and 1. The number of required secondary workers is calculated by ceil(min-secondary-worker-fraction * num_secondary_workers). Defaults to 0.0001. |
| `--node-group` | NODE_GROUP |  | The name of the sole-tenant node group to create the cluster on. Can be a short name ("node-group-name") or in the format "projects/{project-id}/zones/{zone}/nodeGroups/{node-group-name}". |
| `--num-driver-pool-local-ssds` | NUM_DRIVER_POOL_LOCAL_SSDS |  | The number of local SSDs to attach to each cluster driver pool node. |
| `--num-master-local-ssds` | NUM_MASTER_LOCAL_SSDS |  | The number of local SSDs to attach to the master in a cluster. |
| `--num-masters` | NUM_MASTERS |  | The number of master nodes in the cluster. Number of Masters Cluster Mode 1 Standard 3 High Availability |
| `--num-secondary-worker-local-ssds` | NUM_SECONDARY_WORKER_LOCAL_SSDS |  | The number of local SSDs to attach to each preemptible worker in a cluster. |
| `--num-worker-local-ssds` | NUM_WORKER_LOCAL_SSDS |  | The number of local SSDs to attach to each worker in a cluster. |
| `--optional-components` | [COMPONENT,...] |  | List of optional components to be installed on cluster machines. The following page documents the optional components that can be installed: https://cloud.google.com/dataproc/docs/concepts/configuring-clusters/optional-components. |
| `--private-ipv6-google-access-type` | one of: inherit-subnetwork, outbound, bidirectional |  | The private IPv6 Google access type for the cluster. PRIVATE_IPV6_GOOGLE_ACCESS_TYPE must be one of: inherit-subnetwork, outbound, bidirectional. |
| `--properties` | [PREFIX:PROPERTY=VALUE,...] |  | Specifies configuration properties for installed packages, such as Hadoop and Spark. Properties are mapped to configuration files by specifying a prefix, such as "core:io.serializations". The following are supported prefixes and their mappings: Prefix File Purpose of file capacity-scheduler capacity-scheduler.xml Hadoop YARN Capacity Scheduler configuration core core-site.xml Hadoop general configuration distcp distcp-default.xml Hadoop Distributed Copy configuration hadoop-env hadoop-env.sh Hadoop specific environment variables hdfs hdfs-site.xml Hadoop HDFS configuration hive hive-site.xml Hive configuration mapred mapred-site.xml Hadoop MapReduce configuration mapred-env mapred-env.sh Hadoop MapReduce specific environment variables pig pig.properties Pig configuration spark spark-defaults.conf Spark configuration spark-env spark-env.sh Spark specific environment variables yarn yarn-site.xml Hadoop YARN configuration yarn-env yarn-env.sh Hadoop YARN specific environment variables See https://cloud.google.com/dataproc/docs/concepts/configuring-clusters/cluster-properties for more information. |
| `--secondary-worker-accelerator` | [type=TYPE,[count=COUNT],...] |  | Attaches accelerators, such as GPUs, to the secondary-worker instance(s). type The specific type of accelerator to attach to the instances, such as nvidia-tesla-t4 for NVIDIA T4. Use gcloud compute accelerator-types list to display available accelerator types. count The number of accelerators to attach to each instance. The default value is 1. |
| `--secondary-worker-boot-disk-size` | SECONDARY_WORKER_BOOT_DISK_SIZE |  | The size of the boot disk. The value must be a whole number followed by a size unit of KB for kilobyte, MB for megabyte, GB for gigabyte, or TB for terabyte. For example, 10GB will produce a 10 gigabyte disk. The minimum size a boot disk can have is 10 GB. Disk size must be a multiple of 1 GB. |
| `--secondary-worker-boot-disk-type` | SECONDARY_WORKER_BOOT_DISK_TYPE |  | The type of the boot disk. The value must be pd-balanced, pd-ssd, or pd-standard. |
| `--secondary-worker-local-ssd-interface` | SECONDARY_WORKER_LOCAL_SSD_INTERFACE |  | Interface to use to attach local SSDs to each secondary worker in a cluster. |
| `--secondary-worker-machine-types` | type=MACHINE_TYPE[,type=MACHINE_TYPE...][,rank=RANK] |  | Types of machines with optional rank for secondary workers to use. Defaults to server-specified.eg. --secondary-worker-machine-types="type=e2-standard-8,type=t2d-standard-8,rank=0" |
| `--secondary-worker-standard-capacity-base` | SECONDARY_WORKER_STANDARD_CAPACITY_BASE |  | This flag sets the base number of Standard VMs to use for secondary workers (https://cloud.google.com/dataproc/docs/concepts/compute/secondary-vms#preemptible_and_non-preemptible_secondary_workers). Dataproc will create only standard VMs until it reaches this number, then it will mix Spot and Standard VMs according to SECONDARY_WORKER_STANDARD_CAPACITY_PERCENT_ABOVE_BASE. |
| `--secondary-worker-standard-capacity-percent-above-base` | SECONDARY_WORKER_STANDARD_CAPACITY_PERCENT_ABOVE_BASE |  | When combining Standard and Spot VMs for secondary-workers (https://cloud.google.com/dataproc/docs/concepts/compute/secondary-vms#preemptible_and_non-preemptible_secondary_workers) once the number of Standard VMs specified by SECONDARY_WORKER_STANDARD_CAPACITY_BASE has been used, this flag specifies the percentage of the total number of additional Standard VMs secondary workers will use. Spot VMs will be used for the remaining percentage. |
| `--shielded-integrity-monitoring` |  |  | Enables monitoring and attestation of the boot integrity of the cluster's VMs. vTPM (virtual Trusted Platform Module) must also be enabled. A TPM is a hardware module that can be used for different security operations, such as remote attestation, encryption, and sealing of keys. |
| `--shielded-secure-boot` |  |  | The cluster's VMs will boot with secure boot enabled. |
| `--shielded-vtpm` |  |  | The cluster's VMs will boot with the TPM (Trusted Platform Module) enabled. A TPM is a hardware module that can be used for different security operations, such as remote attestation, encryption, and sealing of keys. |
| `--stop-max-idle` | STOP_MAX_IDLE |  | The duration after the last job completes to auto-stop the cluster, such as "2h" or "1d". See $ gcloud topic datetimes for information on duration formats. |
| `--temp-bucket` | TEMP_BUCKET |  | The Google Cloud Storage bucket to use by default to store ephemeral cluster and jobs data, such as Spark and MapReduce history files. |
| `--tier` | one of: premium, standard |  | Cluster tier. TIER must be one of: premium, standard. |
| `--worker-accelerator` | [type=TYPE,[count=COUNT],...] |  | Attaches accelerators, such as GPUs, to the worker instance(s). type The specific type of accelerator to attach to the instances, such as nvidia-tesla-t4 for NVIDIA T4. Use gcloud compute accelerator-types list to display available accelerator types. count The number of accelerators to attach to each instance. The default value is 1. |
| `--worker-boot-disk-provisioned-iops` | WORKER_BOOT_DISK_PROVISIONED_IOPS |  | Indicates the IOPS (https://cloud.google.com/compute/docs/disks/hyperdisks#iops) to provision for the disk. This sets the limit for disk I/O operations per second. This is only supported if the bootdisk type is hyperdisk-balanced (https://cloud.google.com/compute/docs/disks/hyperdisks). |
| `--worker-boot-disk-provisioned-throughput` | WORKER_BOOT_DISK_PROVISIONED_THROUGHPUT |  | Indicates the throughput (https://cloud.google.com/compute/docs/disks/hyperdisks#throughput) to provision for the disk. This sets the limit for throughput in MiB per second. This is only supported if the bootdisk type is hyperdisk-balanced (https://cloud.google.com/compute/docs/disks/hyperdisks). |
| `--worker-boot-disk-size` | WORKER_BOOT_DISK_SIZE |  | The size of the boot disk. The value must be a whole number followed by a size unit of KB for kilobyte, MB for megabyte, GB for gigabyte, or TB for terabyte. For example, 10GB will produce a 10 gigabyte disk. The minimum size a boot disk can have is 10 GB. Disk size must be a multiple of 1 GB. |
| `--worker-boot-disk-type` | WORKER_BOOT_DISK_TYPE |  | The type of the boot disk. The value must be pd-balanced, pd-ssd, or pd-standard. |
| `--worker-local-ssd-interface` | WORKER_LOCAL_SSD_INTERFACE |  | Interface to use to attach local SSDs to each worker in a cluster. |
| `--worker-min-cpu-platform` | PLATFORM |  | When specified, the VM is scheduled on the host with a specified CPU architecture or a more recent CPU platform that's available in that zone. To list available CPU platforms in a zone, run: $ gcloud compute zones describe ZONE CPU platform selection may not be available in a zone. Zones that support CPU platform selection provide an availableCpuPlatforms field, which contains the list of available CPU platforms in the zone (see Availability of CPU platforms for more information). |
| `--zone` | ZONE, -z ZONE |  | The compute zone (e.g. us-central1-a) for the cluster. If empty and --region is set to a value other than global, the server will pick a zone in the region. Overrides the default compute/zone property value for this command invocation. |
| `--metric-sources` | one of: FLINK, HDFS, HIVEMETASTORE, HIVESERVER2, MONITORING_AGENT_DEFAULTS, SPARK, SPARK_HISTORY_SERVER, YARN |  | _[be one of: any, none, specific.]_ Specifies a list of cluster Metric Sources (https://cloud.google.com/dataproc/docs/guides/monitoring#available_oss_metrics) to collect custom metrics. METRIC_SOURCE must be one of: FLINK, HDFS, HIVEMETASTORE, HIVESERVER2, MONITORING_AGENT_DEFAULTS, SPARK, SPARK_HISTORY_SERVER, YARN. |


**Examples:**
```bash
To create a cluster, run:

    $ gcloud dataproc clusters create my-cluster --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/clusters/create)

---
### `gcloud dataproc clusters delete`

Delete a cluster

Delete a cluster.

**Synopsis:**
```
gcloud dataproc clusters delete (CLUSTER : --region=REGION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - The name of the cluster to delete. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

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
     Dataproc region for the cluster. Each Dataproc region constitutes an
     independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a cluster, run:

    $ gcloud dataproc clusters delete my-cluster --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/clusters/delete)

---
### `gcloud dataproc clusters describe`

View the details of a cluster

View the details of a cluster.

**Synopsis:**
```
gcloud dataproc clusters describe (CLUSTER : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - The name of the cluster to describe. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

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
     Dataproc region for the cluster. Each Dataproc region constitutes an
     independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Examples:**
```bash
To view the details of a cluster, run:

    $ gcloud dataproc clusters describe my-cluster --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/clusters/describe)

---
### `gcloud dataproc clusters diagnose`

Run a detailed diagnostic on a cluster

Run a detailed diagnostic on a cluster.

**Synopsis:**
```
gcloud dataproc clusters diagnose (CLUSTER : --region=REGION)
    [--end-time=END_TIME] [--job-ids=JOB_IDS] [--start-time=START_TIME]
    [--tarball-access=TARBALL_ACCESS] [--tarball-gcs-dir=TARBALL_GCS_DIR]
    [--yarn-application-ids=YARN_APPLICATION_IDS] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - The name of the cluster to diagnose. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

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
     Dataproc region for the cluster. Each Dataproc region constitutes an
     independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--end-time` | END_TIME |  | Time instant to stop the diagnosis at (in %Y-%m-%dT%H:%M:%S.%fZ format). |
| `--job-ids` | JOB_IDS |  | A list of jobs on which to perform the diagnosis. |
| `--start-time` | START_TIME |  | Time instant to start the diagnosis from (in %Y-%m-%dT%H:%M:%S.%fZ format). |
| `--tarball-access` | one of: GOOGLE_CLOUD_SUPPORT, GOOGLE_DATAPROC_DIAGNOSE |  | Target access privileges for diagnostic tarball. TARBALL_ACCESS must be one of: GOOGLE_CLOUD_SUPPORT, GOOGLE_DATAPROC_DIAGNOSE. |
| `--tarball-gcs-dir` | TARBALL_GCS_DIR |  | The output Cloud Storage directory for the diagnostic tarball. If not specified, a task-specific directory in the cluster's staging bucket will be used. |
| `--yarn-application-ids` | YARN_APPLICATION_IDS |  | A list of yarn applications on which to perform the diagnosis. |


**Examples:**
```bash
To diagnose a cluster, run:

    $ gcloud dataproc clusters diagnose my-cluster --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/clusters/diagnose)

---
### `gcloud dataproc clusters export`

Export a cluster

Exports an existing cluster's configuration to a file. This configuration
can then be used to create new clusters using the import command.

**Synopsis:**
```
gcloud dataproc clusters export (CLUSTER : --region=REGION)
    [--destination=DESTINATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - The name of the cluster to export. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

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
     Dataproc region for the cluster. Each Dataproc region constitutes an
     independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | Path to a YAML file where the configuration will be exported. Alternatively, you may omit this flag to write to standard output. |


**Examples:**
```bash
To export a cluster to a YAML file, run:

    $ gcloud dataproc clusters export my-cluster --region=us-central1 \
        --destination=cluster.yaml

To export a cluster to standard output, run:

    $ gcloud dataproc clusters export my-cluster --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/clusters/export)

---
### `gcloud dataproc clusters get-iam-policy`

Get IAM policy for a cluster

Gets the IAM policy for a cluster, given a cluster name.

**Synopsis:**
```
gcloud dataproc clusters get-iam-policy (CLUSTER : --region=REGION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - The name of the cluster to retrieve the policy for. The
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
     Dataproc region for the cluster. Each Dataproc region constitutes an
     independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Examples:**
```bash
The following command prints the IAM policy for a cluster with the name
example-cluster-name-1:

    $ gcloud dataproc clusters get-iam-policy example-cluster-name-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/clusters/get-iam-policy)

---
### `gcloud dataproc clusters import`

Import a cluster

This will create a new cluster with the given configuration. If a cluster
with this name already exists, an error will be thrown.

**Synopsis:**
```
gcloud dataproc clusters import (CLUSTER : --region=REGION) [--async]
    [--source=SOURCE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - The name of the cluster to import. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

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
     Dataproc region for the cluster. Each Dataproc region constitutes an
     independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--source` | SOURCE |  | Path to a YAML file containing configuration export data. Alternatively, you may omit this flag to read from standard input. |


**Examples:**
```bash
To import a cluster from a YAML file, run:

    $ gcloud dataproc clusters import my-cluster --region=us-central1 \
        --source=cluster.yaml

To import a cluster from standard output, run:

    $ gcloud dataproc clusters import my-cluster --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/clusters/import)

---
### `gcloud dataproc clusters list`

View a list of clusters in a project

View a list of clusters in a project. An optional filter can be used to
constrain the clusters returned. Filters are case-sensitive and have the
following syntax:

    field = value [AND [field = value]] ...

where field is one of status.state, clusterName, or labels.[KEY], and [KEY]
is a label key. value can be * to match all values. status.state can be one
of the following: ACTIVE, INACTIVE, CREATING, RUNNING, ERROR, DELETING, or
UPDATING. ACTIVE contains the CREATING, UPDATING, and RUNNING states.
INACTIVE contains the DELETING and ERROR states. clusterName is the name of
the cluster provided at creation time. Only the logical AND operator is
supported; space-separated items are treated as having an implicit AND
operator.

**Synopsis:**
```
gcloud dataproc clusters list [--region=REGION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE; default=100]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Dataproc region to use. Each Dataproc region constitutes an independent resource namespace constrained to deploying instances into Compute Engine zones inside the region. Overrides the default dataproc/region property value for this command invocation. |


**Examples:**
```bash
To see the list of all clusters in Dataproc's 'us-central1' region, run:

    $ gcloud dataproc clusters list --region='us-central1'

To show a cluster in Dataproc's 'global' region with the name 'mycluster',
run:

    $ gcloud dataproc clusters list --region='global' \
        --filter='clusterName = mycluster'

To see the list of all clusters in Dataproc's 'global' region with
specified labels, run:

    $ gcloud dataproc clusters list --region='global' \
        --filter='labels.env = staging AND
      labels.starred = *'

To see a list of all active clusters in Dataproc's 'europe-west1' region
with specified labels, run:

    $ gcloud dataproc clusters list --region='europe-west1' \
        --filter='status.state = ACTIVE AND
      labels.env = staging AND labels.starred = *'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/clusters/list)

---
### `gcloud dataproc clusters set-iam-policy`

Set IAM policy for a cluster

Sets the IAM policy for a cluster, given a cluster name and the policy.

**Synopsis:**
```
gcloud dataproc clusters set-iam-policy (CLUSTER : --region=REGION)
    POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - The name of the cluster to set the policy on. The
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
     Dataproc region for the cluster. Each Dataproc region constitutes an
     independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.
```

**Examples:**
```bash
The following command sets the IAM policy for a cluster with the name
example-cluster-name-1 using policy.yaml:

    $ gcloud dataproc clusters set-iam-policy example-cluster-name-1 \
        policy.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/clusters/set-iam-policy)

---
### `gcloud dataproc clusters start`

Start a cluster

Start a cluster.

**Synopsis:**
```
gcloud dataproc clusters start (CLUSTER : --region=REGION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - The name of the cluster to start. The arguments in this
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
     Dataproc region for the cluster. Each Dataproc region constitutes an
     independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To start a cluster, run:

    $ gcloud dataproc clusters start my-cluster --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/clusters/start)

---
### `gcloud dataproc clusters stop`

Stop a cluster

Stop a cluster.

**Synopsis:**
```
gcloud dataproc clusters stop (CLUSTER : --region=REGION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - The name of the cluster to stop. The arguments in this
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
     Dataproc region for the cluster. Each Dataproc region constitutes an
     independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To stop a cluster, run:

    $ gcloud dataproc clusters stop my-cluster --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/clusters/stop)

---
### `gcloud dataproc clusters update`

Update labels and/or the number of worker nodes in a cluster

Update the number of worker nodes and/or the labels in a cluster.

**Synopsis:**
```
gcloud dataproc clusters update (CLUSTER : --region=REGION) [--async]
    [--graceful-decommission-timeout=GRACEFUL_DECOMMISSION_TIMEOUT]
    [--min-secondary-worker-fraction=MIN_SECONDARY_WORKER_FRACTION]
    [--num-secondary-workers=NUM_SECONDARY_WORKERS]
    [--num-workers=NUM_WORKERS] [--update-labels=[KEY=VALUE,...]]
    [--autoscaling-policy=AUTOSCALING_POLICY | --disable-autoscaling]
    [--clear-labels | --remove-labels=[KEY,...]]
    [--delete-expiration-time=DELETE_EXPIRATION_TIME
      | --delete-max-age=DELETE_MAX_AGE | --no-delete-max-age]
    [--delete-max-idle=DELETE_MAX_IDLE | --no-delete-max-idle]
    [--identity-config-file=IDENTITY_CONFIG_FILE
      | --add-user-mappings=[KEY=VALUE,...]
      --remove-user-mappings=[KEY,...]]
    [--stop-expiration-time=STOP_EXPIRATION_TIME
      | --stop-max-age=STOP_MAX_AGE | --no-stop-max-age]
    [--stop-max-idle=STOP_MAX_IDLE | --no-stop-max-idle]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - The name of the cluster to update. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

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
     Dataproc region for the cluster. Each Dataproc region constitutes an
     independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--graceful-decommission-timeout` | GRACEFUL_DECOMMISSION_TIMEOUT |  | The graceful decommission timeout for decommissioning Node Managers in the cluster, used when removing nodes. Graceful decommissioning allows removing nodes from the cluster without interrupting jobs in progress. Timeout specifies how long to wait for jobs in progress to finish before forcefully removing nodes (and potentially interrupting jobs). Timeout defaults to 0 if not set (for forceful decommission), and the maximum allowed timeout is 1 day. See $ gcloud topic datetimes for information on duration formats. |
| `--min-secondary-worker-fraction` | MIN_SECONDARY_WORKER_FRACTION |  | Minimum fraction of new secondary worker nodes added in a scale up update operation, required to update the cluster. If it is not met, cluster updation will rollback the addition of secondary workers. Must be a decimal value between 0 and 1. Defaults to 0.0001. |
| `--num-secondary-workers` | NUM_SECONDARY_WORKERS |  | The new number of secondary worker nodes in the cluster. |
| `--num-workers` | NUM_WORKERS |  | The new number of worker nodes in the cluster. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To resize a cluster, run:

    $ gcloud dataproc clusters update my-cluster --region=us-central1 \
        --num-workers=5

To change the number preemptible workers in a cluster, run:

    $ gcloud dataproc clusters update my-cluster --region=us-central1 \
        --num-preemptible-workers=5

To add the label 'customer=acme' to a cluster, run:

    $ gcloud dataproc clusters update my-cluster --region=us-central1 \
        --update-labels=customer=acme

To update the label 'customer=ackme' to 'customer=acme', run:

    $ gcloud dataproc clusters update my-cluster --region=us-central1 \
        --update-labels=customer=acme

To remove the label whose key is 'customer', run:

    $ gcloud dataproc clusters update my-cluster --region=us-central1 \
        --remove-labels=customer
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/clusters/update)

---

## `gcloud dataproc clusters gke` — create Dataproc GKE-based virtual clusters
### `gcloud dataproc clusters gke create`

Create a GKE-based virtual cluster

Create a GKE-based virtual cluster.

**Synopsis:**
```
gcloud dataproc clusters gke create (CLUSTER : --region=REGION)
    --spark-engine-version=SPARK_ENGINE_VERSION
    (--gke-cluster=GKE_CLUSTER
      : --gke-cluster-location=GKE_CLUSTER_LOCATION) [--async]
    [--namespace=NAMESPACE] [--pools=[KEY=VALUE[;VALUE],...]]
    [--properties=[PREFIX:PROPERTY=VALUE,...]] [--setup-workload-identity]
    [--staging-bucket=STAGING_BUCKET]
    [--history-server-cluster=HISTORY_SERVER_CLUSTER
      : --history-server-cluster-region=HISTORY_SERVER_CLUSTER_REGION]
    [--metastore-service=METASTORE_SERVICE
      : --metastore-service-location=METASTORE_SERVICE_LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - The name of the cluster to create. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

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
     Dataproc region for the cluster. Each Dataproc region constitutes an
     independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--spark-engine-version` | SPARK_ENGINE_VERSION |  | The version of the Spark engine to run on this cluster. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--namespace` | NAMESPACE |  | The name of the Kubernetes namespace to deploy Dataproc system components in. This namespace does not need to exist. |
| `--pools` | [KEY=VALUE[;VALUE],...] |  | Each --pools flag represents a GKE node pool associated with the virtual cluster. It is comprised of a CSV in the form KEY=VALUE[;VALUE], where certain keys may have multiple values. The following KEYs must be specified: ----------------------------------------------------------------------------------------------------------- KEY Type Example Description ------ ---------------- ------------------------ ---------------------------------------------------------- name string `my-node-pool` Name of the node pool. roles repeated string `default;spark-driver` Roles that this node pool should perform. Valid values are `default`, `controller`, `spark-driver`, `spark-executor`. ----------------------------------------------------------------------------------------------------------- The following KEYs may be specified: ---------------------------------------------------------------------------------------------------------------------------------------------------------------- KEY Type Example Description --------------- ---------------- --------------------------------------------- --------------------------------------------------------------------------------- machineType string `n1-standard-8` Compute Engine machine type to use. preemptible boolean `false` If true, then this node pool uses preemptible VMs. This cannot be true on the node pool with the `controllers` role (or `default` role if `controllers` role is not specified). localSsdCount int `2` The number of local SSDs to attach to each node. accelerator repeated string `nvidia-tesla-a100=1` Accelerators to attach to each node. In the format NAME=COUNT. minCpuPlatform string `Intel Skylake` Minimum CPU platform for each node. bootDiskKmsKey string `projects/project-id/locations/us-central1 The Customer Managed Encryption Key (CMEK) used to encrypt /keyRings/keyRing-name/cryptoKeys/key-name` the boot disk attached to each node in the node pool. locations repeated string `us-west1-a;us-west1-c` Zones within the location of the GKE cluster. All `--pools` flags for a Dataproc cluster must have identical locations. min int `0` Minimum number of nodes per zone that this node pool can scale down to. max int `10` Maximum number of nodes per zone that this node pool can scale up to. ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `--properties` | [PREFIX:PROPERTY=VALUE,...] |  | Specifies configuration properties for installed packages, such as Spark. Properties are mapped to configuration files by specifying a prefix, such as "core:io.serializations". |
| `--setup-workload-identity` |  |  | Sets up the GKE Workload Identity for your Dataproc on GKE cluster. Note that running this requires elevated permissions as it will manipulate IAM policies on the Google Service Accounts that will be used by your Dataproc on GKE cluster. |
| `--staging-bucket` | STAGING_BUCKET |  | The Cloud Storage bucket to use to stage job dependencies, miscellaneous config files, and job driver console output when using this cluster. |


**Examples:**
```bash
Create a Dataproc on GKE cluster in us-central1 on a GKE cluster in the
same project and region with default values:

    $ gcloud dataproc clusters gke create my-cluster \
        --region=us-central1 --gke-cluster=my-gke-cluster \
        --spark-engine-version=latest --pools='name=dp,roles=default'

Create a Dataproc on GKE cluster in us-central1 on a GKE cluster in the
same project and zone us-central1-f with default values:

    $ gcloud dataproc clusters gke create my-cluster \
        --region=us-central1 --gke-cluster=my-gke-cluster \
        --gke-cluster-location=us-central1-f \
        --spark-engine-version=3.1 --pools='name=dp,roles=default'

Create a Dataproc on GKE cluster in us-central1 with machine type
'e2-standard-4', autoscaling 5-15 nodes per zone.

    $ gcloud dataproc clusters gke create my-cluster \
        --region='us-central1' \
        --gke-cluster='projects/my-project/locations/us-central1/cluster\
    s/my-gke-cluster' --spark-engine-version=dataproc-1.5 \
        --pools='name=dp-default,roles=default,machineType=e2-standard-4\
    ,min=5,max=15'

Create a Dataproc on GKE cluster in us-central1 with two distinct node
pools.

    $ gcloud dataproc clusters gke create my-cluster \
        --region='us-central1' --gke-cluster='my-gke-cluster' \
        --spark-engine-version='dataproc-2.0' \
        --pools='name=dp-default,roles=default,machineType=e2-standard-4\
    ' \
        --pools='name=workers,roles=spark-drivers;spark-executors,machin\
    eType=n2-standard-8
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/clusters/gke/create)

---
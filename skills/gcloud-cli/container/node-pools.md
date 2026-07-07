# gcloud container node-pools

create and delete operations for Google Kubernetes Engine node pools

### `gcloud container node-pools complete-upgrade`

Complete a node pool upgrade

Complete a node pool upgrade.

Complete upgrade is a method used to skip the remaining node pool soaking
phase during blue-green node pool upgrades.

**Synopsis:**
```
gcloud container node-pools complete-upgrade NAME [--cluster=CLUSTER]
    [--location=LOCATION | --region=REGION | --zone=ZONE, -z ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the node pool for which the upgrade is to be completed.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cluster` | CLUSTER |  | Cluster to which the node pool belongs. Overrides the default container/cluster property value for this command invocation. |


**Examples:**
```bash
To complete an active upgrade in node-pool-1 in the cluster sample-cluster,
run:

    $ gcloud container node-pools complete-upgrade node-pool-1 \
        --cluster=sample-cluster
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/node-pools/complete-upgrade)

---
### `gcloud container node-pools create`

Create a node pool in a running cluster

gcloud container node-pools create facilitates the creation of a node pool
in a Google Kubernetes Engine cluster. A variety of options exists to
customize the node configuration and the number of nodes created.

**Synopsis:**
```
gcloud container node-pools create NAME
    [--accelerator=[type=TYPE,[count=COUNT,
      gpu-driver-version=GPU_DRIVER_VERSION,
      gpu-partition-size=GPU_PARTITION_SIZE,
      gpu-sharing-strategy=GPU_SHARING_STRATEGY,
      max-shared-clients-per-gpu=MAX_SHARED_CLIENTS_PER_GPU],...]]
    [--additional-node-network=[network=NETWORK_NAME,
      subnetwork=SUBNETWORK_NAME,...]]
    [--additional-pod-network=[subnetwork=SUBNETWORK_NAME,
      pod-ipv4-range=SECONDARY_RANGE_NAME,
      [max-pods-per-node=NUM_PODS],...]] [--async]
    [--autoscaled-rollout-policy=[wait-for-drain-duration=WAIT-FOR-DRAIN-DURATION]]
    [--boot-disk-kms-key=BOOT_DISK_KMS_KEY]
    [--boot-disk-provisioned-iops=BOOT_DISK_PROVISIONED_IOPS]
    [--boot-disk-provisioned-throughput=BOOT_DISK_PROVISIONED_THROUGHPUT]
    [--cluster=CLUSTER] [--confidential-node-type=CONFIDENTIAL_NODE_TYPE]
    [--containerd-config-from-file=PATH_TO_FILE]
    [--data-cache-count=DATA_CACHE_COUNT] [--disk-size=DISK_SIZE]
    [--disk-type=DISK_TYPE] [--enable-autoprovisioning]
    [--enable-autorepair] [--no-enable-autoupgrade]
    [--enable-blue-green-upgrade] [--enable-confidential-nodes]
    [--enable-confidential-storage] [--enable-gvnic]
    [--enable-image-streaming] [--enable-insecure-kubelet-readonly-port]
    [--enable-kernel-module-signature-enforcement]
    [--enable-nested-virtualization] [--enable-private-nodes]
    [--enable-queued-provisioning] [--enable-surge-upgrade] [--flex-start]
    [--image-type=IMAGE_TYPE] [--labels=[KEY=VALUE,...]]
    [--logging-variant=LOGGING_VARIANT]
    [--machine-type=MACHINE_TYPE, -m MACHINE_TYPE]
    [--max-pods-per-node=MAX_PODS_PER_NODE]
    [--max-run-duration=MAX_RUN_DURATION]
    [--max-surge-upgrade=MAX_SURGE_UPGRADE; default=1]
    [--max-unavailable-upgrade=MAX_UNAVAILABLE_UPGRADE]
    [--metadata=KEY=VALUE,[KEY=VALUE,...]]
    [--metadata-from-file=KEY=LOCAL_FILE_PATH,[...]]
    [--min-cpu-platform=PLATFORM]
    [--network-performance-configs=[PROPERTY=VALUE,...]]
    [--node-group=NODE_GROUP] [--node-labels=[NODE_LABEL,...]]
    [--node-locations=ZONE,[ZONE,...]]
    [--node-pool-soak-duration=NODE_POOL_SOAK_DURATION]
    [--node-taints=[NODE_TAINT,...]] [--node-version=NODE_VERSION]
    [--num-nodes=NUM_NODES]
    [--opportunistic-maintenance=[node-idle-time=NODE_IDLE_TIME,
      window=WINDOW,min-nodes=MIN_NODES,...]]
    [--performance-monitoring-unit=PERFORMANCE_MONITORING_UNIT]
    [--placement-policy=PLACEMENT_POLICY] [--placement-type=PLACEMENT_TYPE]
    [--preemptible] [--resource-manager-tags=[KEY=VALUE,...]]
    [--sandbox=[type=TYPE]]
    [--secondary-boot-disk=[disk-image=DISK_IMAGE,[mode=MODE],...]]
    [--shielded-integrity-monitoring] [--shielded-secure-boot]
    [--sole-tenant-min-node-cpus=SOLE_TENANT_MIN_NODE_CPUS]
    [--sole-tenant-node-affinity-file=SOLE_TENANT_NODE_AFFINITY_FILE]
    [--spot]
    [--standard-rollout-policy=[batch-node-count=BATCH_NODE_COUNT,
      batch-percent=BATCH_NODE_PERCENTAGE,
      batch-soak-duration=BATCH_SOAK_DURATION,...]]
    [--storage-pools=STORAGE_POOL,[...]]
    [--system-config-from-file=PATH_TO_FILE] [--tags=TAG,[TAG,...]]
    [--threads-per-core=THREADS_PER_CORE] [--tpu-topology=TPU_TOPOLOGY]
    [--windows-os-version=WINDOWS_OS_VERSION]
    [--workload-metadata=WORKLOAD_METADATA]
    [--create-pod-ipv4-range=[KEY=VALUE,...] | --pod-ipv4-range=NAME]
    [--enable-autoscaling --location-policy=LOCATION_POLICY
      --max-nodes=MAX_NODES --min-nodes=MIN_NODES
      --total-max-nodes=TOTAL_MAX_NODES --total-min-nodes=TOTAL_MIN_NODES]
    [--enable-best-effort-provision
      --min-provision-nodes=MIN_PROVISION_NODES]
    [--ephemeral-storage-local-ssd[=[count=COUNT]]
      | --local-nvme-ssd-block[=[count=COUNT]]
      | --local-ssd-count=LOCAL_SSD_COUNT]
    [--location=LOCATION | --region=REGION | --zone=ZONE, -z ZONE]
    [--node-drain-grace-period-seconds=NODE_DRAIN_GRACE_PERIOD_SECONDS
      --node-drain-pdb-timeout-seconds=NODE_DRAIN_PDB_TIMEOUT_SECONDS
      --respect-pdb-during-node-pool-deletion]
    [--reservation=RESERVATION --reservation-affinity=RESERVATION_AFFINITY]
    [--scopes=[SCOPE,...];
      default="gke-default" --service-account=SERVICE_ACCOUNT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of the node pool to create.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--accelerator` | one of: `default`: Install the default driver version for this GKE version |  | Attaches accelerators (e.g. GPUs) to all nodes. type (Required) The specific type (e.g. nvidia-tesla-t4 for NVIDIA T4) of accelerator to attach to the instances. Use gcloud compute accelerator-types list to learn about all available accelerator types. count (Optional) The number of accelerators to attach to the instances. The default value is 1. gpu-driver-version (Optional) The NVIDIA driver version to install. GPU_DRIVER_VERSION must be one of: `default`: Install the default driver version for this GKE version. For GKE version 1.30.1-gke.1156000 and later, this is the default option. `latest`: Install the latest driver version available for this GKE version. Can only be used for nodes that use Container-Optimized OS. `disabled`: Skip automatic driver installation. You must manually install a driver after you create the cluster. For GKE version 1.30.1-gke.1156000 and earlier, this is the default option. To manually install the GPU driver, refer to https://cloud.google.com/kubernetes-engine/docs/how-to/gpus#installing_drivers. gpu-partition-size (Optional) The GPU partition size used when running multi-instance GPUs. For information about multi-instance GPUs, refer to: https://cloud.google.com/kubernetes-engine/docs/how-to/gpus-multi gpu-sharing-strategy (Optional) The GPU sharing strategy (e.g. time-sharing) to use. For information about GPU sharing, refer to: https://cloud.google.com/kubernetes-engine/docs/concepts/timesharing-gpus max-shared-clients-per-gpu (Optional) The max number of containers allowed to share each GPU on the node. This field is used together with gpu-sharing-strategy. |
| `--additional-node-network` | [network=NETWORK_NAME,subnetwork=SUBNETWORK_NAME,...] |  | Attach an additional network interface to each node in the pool. This parameter can be specified up to 7 times. e.g. --additional-node-network network=dataplane,subnetwork=subnet-dp network (Required) The network to attach the new interface to. subnetwork (Required) The subnetwork to attach the new interface to. |
| `--additional-pod-network` | [subnetwork=SUBNETWORK_NAME,pod-ipv4-range=SECONDARY_RANGE_NAME,[max-pods-per-node=NUM_PODS],...] |  | Specify the details of a secondary range to be used for an additional pod network. Not needed if you use "host" typed NIC from this network. This parameter can be specified up to 35 times. e.g. --additional-pod-network subnetwork=subnet-dp,pod-ipv4-range=sec-range-blue,max-pods-per-node=8. subnetwork (Optional) The name of the subnetwork to link the pod network to. If not specified, the pod network defaults to the subnet connected to the default network interface. pod-ipv4-range (Required) The name of the secondary range in the subnetwork. The range must hold at least (2 * MAX_PODS_PER_NODE * MAX_NODES_IN_RANGE) IPs. max-pods-per-node (Optional) Maximum amount of pods per node that can utilize this ipv4-range. Defaults to NodePool (if specified) or Cluster value. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--autoscaled-rollout-policy` | [wait-for-drain-duration=WAIT-FOR-DRAIN-DURATION] |  | Autoscaled rollout policy options for blue-green upgrade. wait-for-drain-duration (Optional) Time in seconds to wait after cordoning the blue pool before draining the nodes. Examples: $ gcloud container node-pools create node-pool-1 \ --cluster=example-cluster --enable-blue-green-upgrade \ --autoscaled-rollout-policy="" $ gcloud container node-pools create node-pool-1 \ --cluster=example-cluster --enable-blue-green-upgrade \ --autoscaled-rollout-policy=wait-for-drain-duration=7200s |
| `--boot-disk-kms-key` | BOOT_DISK_KMS_KEY |  | The Customer Managed Encryption Key used to encrypt the boot disk attached to each node in the node pool. This should be of the form projects/[KEY_PROJECT_ID]/locations/[LOCATION]/keyRings/[RING_NAME]/cryptoKeys/[KEY_NAME]. For more information about protecting resources with Cloud KMS Keys please see: https://cloud.google.com/compute/docs/disks/customer-managed-encryption |
| `--boot-disk-provisioned-iops` | BOOT_DISK_PROVISIONED_IOPS |  | Configure the Provisioned IOPS for the node pool boot disks. Only valid for hyperdisk-balanced boot disks. |
| `--boot-disk-provisioned-throughput` | BOOT_DISK_PROVISIONED_THROUGHPUT |  | Configure the Provisioned Throughput for the node pool boot disks. Only valid for hyperdisk-balanced boot disks. |
| `--cluster` | CLUSTER |  | The cluster to add the node pool to. Overrides the default container/cluster property value for this command invocation. |
| `--confidential-node-type` | one of: sev, sev_snp, tdx, disabled |  | Enable confidential nodes for the node pool. Enabling Confidential Nodes will create nodes using Confidential VM https://docs.cloud.google.com/compute/docs/about-confidential-vm. CONFIDENTIAL_NODE_TYPE must be one of: sev, sev_snp, tdx, disabled. |
| `--containerd-config-from-file` | PATH_TO_FILE |  | Path of the YAML file that contains containerd configuration entries like configuring access to private image registries. For detailed information on the configuration usage, please refer to https://cloud.google.com/kubernetes-engine/docs/how-to/customize-containerd-configuration. Note: Updating the containerd configuration of an existing cluster or node pool requires recreation of the existing nodes, which might cause disruptions in running workloads. Use a full or relative path to a local file containing the value of containerd_config. |
| `--data-cache-count` | DATA_CACHE_COUNT |  | Specifies the number of local SSDs to be utilized for GKE Data Cache in the node pool. |
| `--disk-size` | DISK_SIZE |  | Size for node VM boot disks in GB. Defaults to 100GB. |
| `--disk-type` | one of: pd-standard, pd-ssd, pd-balanced, hyperdisk-balanced, hyperdisk-extreme, hyperdisk-throughput |  | Type of the node VM boot disk. For version 1.24 and later, defaults to pd-balanced. For versions earlier than 1.24, defaults to pd-standard. DISK_TYPE must be one of: pd-standard, pd-ssd, pd-balanced, hyperdisk-balanced, hyperdisk-extreme, hyperdisk-throughput. |
| `--enable-autoprovisioning` |  |  | Enables Cluster Autoscaler to treat the node pool as if it was autoprovisioned. Cluster Autoscaler will be able to delete the node pool if it's unneeded. |
| `--enable-autorepair` |  |  | Enable node autorepair feature for a node pool. $ gcloud container node-pools create node-pool-1 \ --cluster=example-cluster --enable-autorepair Node autorepair is enabled by default for node pools using COS, COS_CONTAINERD, UBUNTU or UBUNTU_CONTAINERD as a base image, use --no-enable-autorepair to disable. See https://cloud.google.com/kubernetes-engine/docs/how-to/node-auto-repair for more info. |
| `--enable-autoupgrade` |  |  | Sets autoupgrade feature for a node pool. $ gcloud container node-pools create node-pool-1 \ --cluster=example-cluster --enable-autoupgrade See https://cloud.google.com/kubernetes-engine/docs/node-auto-upgrades for more info. Enabled by default, use --no-enable-autoupgrade to disable. |
| `--enable-blue-green-upgrade` |  |  | Changes node pool upgrade strategy to blue-green upgrade. |
| `--enable-confidential-nodes` |  |  | Enable confidential nodes for the node pool. Enabling Confidential Nodes will create nodes using Confidential VM https://docs.cloud.google.com/compute/docs/about-confidential-vm. |
| `--enable-confidential-storage` |  |  | Enable confidential storage for the node pool. Enabling Confidential Storage will create boot disk with confidential mode |
| `--enable-gvnic` |  |  | Enable the use of GVNIC for this cluster. Requires re-creation of nodes using either a node-pool upgrade or node-pool creation. |
| `--enable-image-streaming` |  |  | Specifies whether to enable image streaming on node pool. |
| `--enable-insecure-kubelet-readonly-port` |  |  | Enables the Kubelet's insecure read only port. To disable the readonly port on a cluster or node-pool set the flag to --no-enable-insecure-kubelet-readonly-port. |
| `--enable-kernel-module-signature-enforcement` |  |  | Enforces that kernel modules are signed on all nodes in the node pool. This setting overrides the cluster-level setting. For example, if the cluster disables enforcement, you can enable enforcement only for a specific node pool. When the policy is modified on an existing node pool, nodes will be immediately recreated to use the new policy. Use --no-enable-kernel-module-signature-enforcement to disable. Examples: $ gcloud container node-pools create node-pool-1 \ --enable-kernel-module-signature-enforcement |
| `--enable-nested-virtualization` |  |  | Enables the use of nested virtualization on the node pool. Defaults to false. Can only be enabled on UBUNTU_CONTAINERD base image or COS_CONTAINERD base image with version 1.28.4-gke.1083000 and above. |
| `--enable-private-nodes` |  |  | Enables provisioning nodes with private IP addresses only. The control plane still communicates with all nodes through private IP addresses only, regardless of whether private nodes are enabled or disabled. |
| `--enable-queued-provisioning` |  |  | Mark the nodepool as Queued only. This means that all new nodes can be obtained only through queuing via ProvisioningRequest API. $ gcloud container node-pools create node-pool-1 \ --cluster=example-cluster --enable-queued-provisioning ... and other required parameters, for more details see: https://cloud.google.com/kubernetes-engine/docs/how-to/provisioningrequest |
| `--enable-surge-upgrade` |  |  | Changes node pool upgrade strategy to surge upgrade. |
| `--flex-start` |  |  | Start the node pool with Flex Start provisioning model. $ gcloud container node-pools create node-pool-1 \ --cluster=example-cluster --flex-start and other required parameters, for more details see: https://cloud.google.com/kubernetes-engine/docs/how-to/provisioningrequest |
| `--image-type` | IMAGE_TYPE |  | The image type to use for the node pool. Defaults to server-specified. Image Type specifies the base OS that the nodes in the node pool will run on. If an image type is specified, that will be assigned to the node pool and all future upgrades will use the specified image type. If it is not specified the server will pick the default image type. The default image type and the list of valid image types are available using the following command. $ gcloud container get-server-config |
| `--labels` | [KEY=VALUE,...] |  | Labels to apply to the Google Cloud resources of node pools in the Kubernetes Engine cluster. These are unrelated to Kubernetes labels. Warning: Updating this label will causes the node(s) to be recreated. Examples: $ gcloud container node-pools create node-pool-1 \ --cluster=example-cluster --labels=label1=value1,label2=value2 |
| `--logging-variant` | one of: DEFAULT 'DEFAULT' variant requests minimal resources but may not guarantee high throughput |  | Specifies the logging variant that will be deployed on all the nodes in the node pool. If the node pool doesn't specify a logging variant, then the logging variant specified for the cluster will be deployed on all the nodes in the node pool. Valid logging variants are MAX_THROUGHPUT, DEFAULT. LOGGING_VARIANT must be one of: DEFAULT 'DEFAULT' variant requests minimal resources but may not guarantee high throughput. MAX_THROUGHPUT 'MAX_THROUGHPUT' variant requests more node resources and is able to achieve logging throughput up to 10MB per sec. |
| `--machine-type` | MACHINE_TYPE, -m MACHINE_TYPE |  | The type of machine to use for nodes. Defaults to e2-medium. The list of predefined machine types is available using the following command: $ gcloud compute machine-types list You can also specify custom machine types by providing a string with the format "custom-CPUS-RAM" where "CPUS" is the number of virtual CPUs and "RAM" is the amount of RAM in MiB. For example, to create a node pool using custom machines with 2 vCPUs and 12 GB of RAM: $ gcloud container node-pools create high-mem-pool \ --machine-type=custom-2-12288 |
| `--max-pods-per-node` | MAX_PODS_PER_NODE |  | The max number of pods per node for this node pool. This flag sets the maximum number of pods that can be run at the same time on a node. This will override the value given with --default-max-pods-per-node flag set at the cluster level. Must be used in conjunction with '--enable-ip-alias'. |
| `--max-run-duration` | MAX_RUN_DURATION |  | Limit the runtime of each node in the node pool to the specified duration. $ gcloud container node-pools create node-pool-1 \ --cluster=example-cluster --max-run-duration=3600s |
| `--max-surge-upgrade` | MAX_SURGE_UPGRADE | 1 | Number of extra (surge) nodes to be created on each upgrade of the node pool. Specifies the number of extra (surge) nodes to be created during this node pool's upgrades. For example, running the following command will result in creating an extra node each time the node pool is upgraded: $ gcloud container node-pools create node-pool-1 \ --cluster=example-cluster --max-surge-upgrade=1 \ --max-unavailable-upgrade=0 Must be used in conjunction with '--max-unavailable-upgrade'. |
| `--max-unavailable-upgrade` | MAX_UNAVAILABLE_UPGRADE |  | Number of nodes that can be unavailable at the same time on each upgrade of the node pool. Specifies the number of nodes that can be unavailable at the same time during this node pool's upgrades. For example, running the following command will result in having 3 nodes being upgraded in parallel (1 + 2), but keeping always at least 3 (5 - 2) available each time the node pool is upgraded: $ gcloud container node-pools create node-pool-1 \ --cluster=example-cluster --num-nodes=5 \ --max-surge-upgrade=1 --max-unavailable-upgrade=2 Must be used in conjunction with '--max-surge-upgrade'. |
| `--metadata` | KEY=VALUE,[KEY=VALUE,...] |  | Compute Engine metadata to be made available to the guest operating system running on nodes within the node pool. Each metadata entry is a key/value pair separated by an equals sign. Metadata keys must be unique and less than 128 bytes in length. Values must be less than or equal to 32,768 bytes in length. The total size of all keys and values must be less than 512 KB. Multiple arguments can be passed to this flag. For example: --metadata key-1=value-1,key-2=value-2,key-3=value-3 Additionally, the following keys are reserved for use by Kubernetes Engine: * cluster-location * cluster-name * cluster-uid * configure-sh * enable-os-login * gci-update-strategy * gci-ensure-gke-docker * instance-template * kube-env * startup-script * user-data Google Kubernetes Engine sets the following keys by default: * serial-port-logging-enable See also Compute Engine's documentation (https://cloud.google.com/compute/docs/storing-retrieving-metadata) on storing and retrieving instance metadata. |
| `--metadata-from-file` | KEY=LOCAL_FILE_PATH,[...] |  | Same as --metadata except that the value for the entry will be read from a local file. |
| `--min-cpu-platform` | PLATFORM |  | When specified, the nodes for the new node pool will be scheduled on host with specified CPU architecture or a newer one. Examples: $ gcloud container node-pools create node-pool-1 \ --cluster=example-cluster --min-cpu-platform=PLATFORM To list available CPU platforms in given zone, run: $ gcloud beta compute zones describe ZONE \ --format="value(availableCpuPlatforms)" CPU platform selection is available only in selected zones. |
| `--network-performance-configs` | [PROPERTY=VALUE,...] |  | Configures network performance settings for the node pool. If this flag is not specified, the pool will be created with its default network performance configuration. total-egress-bandwidth-tier Total egress bandwidth is the available outbound bandwidth from a VM, regardless of whether the traffic is going to internal IP or external IP destinations. The following tier values are allowed: [TIER_UNSPECIFIED,TIER_1] |
| `--node-group` | NODE_GROUP |  | Assign instances of this pool to run on the specified Google Compute Engine node group. This is useful for running workloads on sole tenant nodes. To see available sole tenant node-groups, run: $ gcloud compute sole-tenancy node-groups list To create a sole tenant node group, run: $ gcloud compute sole-tenancy node-groups create [GROUP_NAME] \ --location [ZONE] --node-template [TEMPLATE_NAME] \ --target-size [TARGET_SIZE] See https://cloud.google.com/compute/docs/nodes for more information on sole tenancy and node groups. |
| `--node-labels` | [NODE_LABEL,...] |  | Applies the given Kubernetes labels on all nodes in the new node pool. Examples: $ gcloud container node-pools create node-pool-1 \ --cluster=example-cluster \ --node-labels=label1=value1,label2=value2 Updating the node pool's --node-labels flag applies the labels to the Kubernetes Node objects for existing nodes in-place; it does not re-create or replace nodes. New nodes, including ones created by resizing or re-creating nodes, will have these labels on the Kubernetes API Node object. The labels can be used in the nodeSelector field. See https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node/ for examples. Note that Kubernetes labels, intended to associate cluster components and resources with one another and manage resource lifecycles, are different from Google Kubernetes Engine labels that are used for the purpose of tracking billing and usage information. |
| `--node-locations` | ZONE,[ZONE,...] |  | The set of zones in which the node pool's nodes should be located. Multiple locations can be specified, separated by commas. For example: $ gcloud container node-pools create node-pool-1 \ --cluster=sample-cluster \ --node-locations=us-central1-a,us-central1-b |
| `--node-pool-soak-duration` | NODE_POOL_SOAK_DURATION |  | Time in seconds to be spent waiting during blue-green upgrade before deleting the blue pool and completing the upgrade. $ gcloud container node-pools create example-cluster \ --node-pool-soak-duration=600s |
| `--node-taints` | [NODE_TAINT,...] |  | Applies the given kubernetes taints on all nodes in the new node pool, which can be used with tolerations for pod scheduling. Examples: $ gcloud container node-pools create node-pool-1 \ --cluster=example-cluster \ --node-taints=key1=val1:NoSchedule,key2=val2:PreferNoSchedule To read more about node-taints, see https://cloud.google.com/kubernetes-engine/docs/node-taints. |
| `--node-version` | NODE_VERSION |  | The Kubernetes version to use for nodes. Defaults to server-specified. The default Kubernetes version is available using the following command. $ gcloud container get-server-config |
| `--num-nodes` | NUM_NODES |  | The number of nodes in the node pool in each of the cluster's zones. Defaults to 3. Exception: when --tpu-topology is specified for multi-host TPU machine types the number of nodes will be defaulted to (product of topology)/(# of chips per VM). |
| `--opportunistic-maintenance` | [node-idle-time=NODE_IDLE_TIME,window=WINDOW,min-nodes=MIN_NODES,...] |  | Opportunistic maintenance options. node-idle-time: Time to be spent waiting for node to be idle before starting maintenance, ending with 's'. Example: "3.5s" window: The window of time that opportunistic maintenance can run, ending with 's'. Example: A setting of 14 days (1209600s) implies that opportunistic maintenance can only be ran in the 2 weeks leading up to the scheduled maintenance date. Setting 28 days(2419200s) allows opportunistic maintenance to run at any time in the scheduled maintenance window. min-nodes: Minimum number of nodes in the node pool to be available during the opportunistic triggered maintenance. $ gcloud container node-pools create example-cluster \ --opportunistic-maintenance=node-idle-time=600s,window=600s,\ min-nodes=2 |
| `--performance-monitoring-unit` | one of: architectural Enables architectural PMU events tied to non last level cache (LLC) events |  | Sets the Performance Monitoring Unit level. Valid values are architectural, standard and enhanced. PERFORMANCE_MONITORING_UNIT must be one of: architectural Enables architectural PMU events tied to non last level cache (LLC) events. enhanced Enables most documented core/L2 and LLC PMU events. standard Enables most documented core/L2 PMU events. |
| `--placement-policy` | PLACEMENT_POLICY |  | Indicates the desired resource policy to use. $ gcloud container node-pools create node-pool-1 \ --cluster=example-cluster --placement-policy my-placement |
| `--placement-type` | one of: UNSPECIFIED, COMPACT |  | Placement type allows to define the type of node placement within this node pool. UNSPECIFIED - No requirements on the placement of nodes. This is the default option. COMPACT - GKE will attempt to place the nodes in a close proximity to each other. This helps to reduce the communication latency between the nodes, but imposes additional limitations on the node pool size. $ gcloud container node-pools create node-pool-1 \ --cluster=example-cluster --placement-type=COMPACT PLACEMENT_TYPE must be one of: UNSPECIFIED, COMPACT. |
| `--preemptible` |  |  | Create nodes using preemptible VM instances in the new node pool. $ gcloud container node-pools create node-pool-1 \ --cluster=example-cluster --preemptible New nodes, including ones created by resize or recreate, will use preemptible VM instances. See https://cloud.google.com/kubernetes-engine/docs/preemptible-vm for more information on how to use Preemptible VMs with Kubernetes Engine. |
| `--resource-manager-tags` | [KEY=VALUE,...] |  | Applies the specified comma-separated resource manager tags that has the GCE_FIREWALL purpose to all nodes in the new node pool. Examples: $ gcloud container node-pools create example-node-pool \ --resource-manager-tags=tagKeys/1234=tagValues/2345 $ gcloud container node-pools create example-node-pool \ --resource-manager-tags=my-project/key1=value1 $ gcloud container node-pools create example-node-pool \ --resource-manager-tags=12345/key1=value1,23456/key2=value2 $ gcloud container node-pools create example-node-pool \ --resource-manager-tags= All nodes, including nodes that are resized or re-created, will have the specified tags on the corresponding Instance object in the Compute Engine API. You can reference these tags in network firewall policy rules. For instructions, see https://cloud.google.com/firewall/docs/use-tags-for-firewalls. |
| `--sandbox` | [type=TYPE] |  | Enables the requested sandbox on all nodes in the node pool. Examples: $ gcloud container node-pools create node-pool-1 \ --cluster=example-cluster --sandbox="type=gvisor" The only supported type is 'gvisor'. |
| `--secondary-boot-disk` | [disk-image=DISK_IMAGE,[mode=MODE],...] |  | Attaches secondary boot disks to all nodes. disk-image (Required) The full resource path to the source disk image to create the secondary boot disks from. mode (Optional) The configuration mode for the secondary boot disks. The default value is "CONTAINER_IMAGE_CACHE". |
| `--shielded-integrity-monitoring` |  |  | Enables monitoring and attestation of the boot integrity of the instance. The attestation is performed against the integrity policy baseline. This baseline is initially derived from the implicitly trusted boot image when the instance is created. |
| `--shielded-secure-boot` |  |  | The instance will boot with secure boot enabled. |
| `--sole-tenant-min-node-cpus` | SOLE_TENANT_MIN_NODE_CPUS |  | A integer value that specifies the minimum number of vCPUs that each sole tenant node must have to use CPU overcommit. If not specified, the CPU overcommit feature is disabled. |
| `--sole-tenant-node-affinity-file` | SOLE_TENANT_NODE_AFFINITY_FILE |  | JSON/YAML file containing the configuration of desired sole tenant nodes onto which this node pool could be backed by. These rules filter the nodes according to their node affinity labels. A node's affinity labels come from the node template of the group the node is in. The file should contain a list of a JSON/YAML objects. For an example, see https://cloud.google.com/compute/docs/nodes/provisioning-sole-tenant-vms#configure_node_affinity_labels. The following list describes the fields: key Corresponds to the node affinity label keys of the Node resource. operator Specifies the node selection type. Must be one of: IN: Requires Compute Engine to seek for matched nodes. NOT_IN: Requires Compute Engine to avoid certain nodes. values Optional. A list of values which correspond to the node affinity label values of the Node resource. |
| `--spot` |  |  | Create nodes using spot VM instances in the new node pool. $ gcloud container node-pools create node-pool-1 \ --cluster=example-cluster --spot New nodes, including ones created by resize or recreate, will use spot VM instances. |
| `--standard-rollout-policy` | [batch-node-count=BATCH_NODE_COUNT,batch-percent=BATCH_NODE_PERCENTAGE,batch-soak-duration=BATCH_SOAK_DURATION,...] |  | Standard rollout policy options for blue-green upgrade. Batch sizes are specified by one of, batch-node-count or batch-percent. The duration between batches is specified by batch-soak-duration. $ gcloud container node-pools create example-cluster \ --standard-rollout-policy=batch-node-count=3,\ batch-soak-duration=60s $ gcloud container node-pools create example-cluster \ --standard-rollout-policy=batch-percent=0.3,\ batch-soak-duration=60s |
| `--storage-pools` | STORAGE_POOL,[...] |  | A list of storage pools where the node pool's boot disks will be provisioned. STORAGE_POOL must be in the format projects/project/zones/zone/storagePools/storagePool |
| `--system-config-from-file` | PATH_TO_FILE |  | Path of the YAML/JSON file that contains the node configuration, including Linux kernel parameters (sysctls) and kubelet configs. Examples: kubeletConfig: cpuManagerPolicy: static memoryManager: policy: Static topologyManager: policy: BestEffort scope: pod linuxConfig: sysctl: net.core.somaxconn: '2048' net.ipv4.tcp_rmem: '4096 87380 6291456' hugepageConfig: hugepage_size2m: '1024' hugepage_size1g: '2' swapConfig: enabled: true bootDiskProfile: swapSizeGib: 8 cgroupMode: 'CGROUP_MODE_V2' List of supported kubelet configs in 'kubeletConfig'. KEY VALUE cpuManagerPolicy either 'static' or 'none' cpuCFSQuota true or false (enabled by default) cpuCFSQuotaPeriod interval (e.g., '100ms'. The value must be between 1ms and 1 second, inclusive.) memoryManager specify memory manager policy topologyManager specify topology manager policy and scope podPidsLimit integer (The value must be greater than or equal to 1024 and less than 4194304.) containerLogMaxSize positive number plus unit suffix (e.g., '100Mi', '0.2Gi'. The value must be between 10Mi and 500Mi, inclusive.) containerLogMaxFiles integer (The value must be between [2, 10].) imageGcLowThresholdPercent integer (The value must be between [10, 85], and lower than imageGcHighThresholdPercent.) imageGcHighThresholdPercent integer (The value must be between [10, 85], and greater than imageGcLowThresholdPercent.) imageMinimumGcAge interval (e.g., '100s', '1m'. The value must be less than '2m'.) imageMaximumGcAge interval (e.g., '100s', '1m'. The value must be greater than imageMinimumGcAge.) evictionSoft specify eviction soft thresholds evictionSoftGracePeriod specify eviction soft grace period evictionMinimumReclaim specify eviction minimum reclaim thresholds evictionMaxPodGracePeriodSeconds integer (Max grace period for pod termination during eviction, in seconds. The value must be between [0, 300].) allowedUnsafeSysctls list of sysctls (Allowlisted groups: 'kernel.shm*', 'kernel.msg*', 'kernel.sem', 'fs.mqueue.*', and 'net.*', and sysctls under the groups.) singleProcessOomKill true or false maxParallelImagePulls integer (The value must be between [2, 5].) List of supported keys in memoryManager in 'kubeletConfig'. KEY VALUE policy either 'Static' or 'None' List of supported keys in topologyManager in 'kubeletConfig'. KEY VALUE policy either 'none' or 'best-effort' or 'single-numa-node' or 'restricted' scope either 'pod' or 'container' List of supported keys in evictionSoft in 'kubeletConfig'. KEY VALUE memoryAvailable quantity (e.g., '100Mi', '1Gi'. Represents the amount of memory available before soft eviction. The value must be at least 100Mi and less than 50% of the node's memory.) nodefsAvailable percentage (e.g., '20%'. Represents the nodefs available before soft eviction. The value must be between 10% and 50%, inclusive.) nodefsInodesFree percentage (e.g., '20%'. Represents the nodefs inodes free before soft eviction. The value must be between 5% and 50%, inclusive.) imagefsAvailable percentage (e.g., '20%'. Represents the imagefs available before soft eviction. The value must be between 15% and 50%, inclusive.) imagefsInodesFree percentage (e.g., '20%'. Represents the imagefs inodes free before soft eviction. The value must be between 5% and 50%, inclusive.) pidAvailable percentage (e.g., '20%'. Represents the pid available before soft eviction. The value must be between 10% and 50%, inclusive.) List of supported keys in evictionSoftGracePeriod in 'kubeletConfig'. KEY VALUE memoryAvailable duration (e.g., '30s', '1m'. The grace period for soft eviction for this resource. The value must be positive and no more than '5m'.) nodefsAvailable duration (e.g., '30s', '1m'. The grace period for soft eviction for this resource. The value must be positive and no more than '5m'.) nodefsInodesFree duration (e.g., '30s', '1m'. The grace period for soft eviction for this resource. The value must be positive and no more than '5m'.) imagefsAvailable duration (e.g., '30s', '1m'. The grace period for soft eviction for this resource. The value must be positive and no more than '5m'.) imagefsInodesFree duration (e.g., '30s', '1m'. The grace period for soft eviction for this resource. The value must be positive and no more than '5m'.) pidAvailable duration (e.g., '30s', '1m'. The grace period for soft eviction for this resource. The value must be positive and no more than '5m'.) List of supported keys in evictionMinimumReclaim in 'kubeletConfig'. KEY VALUE memoryAvailable percentage (e.g., '5%'. Represents the minimum reclaim threshold for memory available. The value must be positive and no more than 10%.) nodefsAvailable percentage (e.g., '5%'. Represents the minimum reclaim threshold for nodefs available. The value must be positive and no more than 10%.) nodefsInodesFree percentage (e.g., '5%'. Represents the minimum reclaim threshold for nodefs inodes free. The value must be positive and no more than 10%.) imagefsAvailable percentage (e.g., '5%'. Represents the minimum reclaim threshold for imagefs available. The value must be positive and no more than 10%.) imagefsInodesFree percentage (e.g., '5%'. Represents the minimum reclaim threshold for imagefs inodes free. The value must be positive and no more than 10%.) pidAvailable percentage (e.g., '5%'. Represents the minimum reclaim threshold for pid available. The value must be positive and no more than 10%.) List of supported sysctls in 'linuxConfig'. KEY VALUE net.core.netdev_max_backlog Any positive integer, less than 2147483647 net.core.rmem_default Must be between [2304, 2147483647] net.core.rmem_max Must be between [2304, 2147483647] net.core.wmem_default Must be between [4608, 2147483647] net.core.wmem_max Must be between [4608, 2147483647] net.core.optmem_max Any positive integer, less than 2147483647 net.core.somaxconn Must be between [128, 2147483647] net.ipv4.tcp_rmem Any positive integer tuple net.ipv4.tcp_wmem Any positive integer tuple net.ipv4.tcp_tw_reuse Must be {0, 1, 2} net.ipv4.tcp_mtu_probing Must be {0, 1, 2} net.ipv4.tcp_max_orphans Must be between [16384, 262144] net.ipv4.tcp_max_tw_buckets Must be between [4096, 2147483647] net.ipv4.tcp_syn_retries Must be between [1, 127] net.ipv4.tcp_ecn Must be {0, 1, 2} net.ipv4.tcp_congestion_control Supported values for COS: 'reno', 'cubic', 'bbr', 'lp', 'htcp'. Supported values for Ubuntu: 'reno', 'cubic', 'bbr', 'lp', 'htcp', 'vegas', 'dctcp', 'bic', 'cdg', 'highspeed', 'hybla', 'illinois', 'nv', 'scalable', 'veno', 'westwood', 'yeah'. net.netfilter.nf_conntrack_max Must be between [65536, 4194304] net.netfilter.nf_conntrack_buckets Must be between [65536, 524288]. Recommend setting: nf_conntrack_max = nf_conntrack_bucke ts * 4 net.netfilter.nf_conntrack_tcp_timeout_close_wait Must be between [60, 3600] net.netfilter.nf_conntrack_tcp_timeout_time_wait Must be between [1, 600] net.netfilter.nf_conntrack_tcp_timeout_established Must be between [600, 86400] net.netfilter.nf_conntrack_acct Must be {0, 1} kernel.shmmni Must be between [4096, 32768] kernel.shmmax Must be between [0, 184467440736927743 99] kernel.shmall Must be between [0, 184467440736927743 99] kernel.perf_event_paranoid Must be {-1, 0, 1, 2, 3} kernel.sched_rt_runtime_us Must be [-1, 1000000] kernel.softlockup_panic Must be {0, 1} kernel.yama.ptrace_scope Must be {0, 1, 2, 3} kernel.kptr_restrict Must be {0, 1, 2} kernel.dmesg_restrict Must be {0, 1} kernel.sysrq Must be [0, 511] fs.aio-max-nr Must be between [65536, 4194304] fs.file-max Must be between [104857, 67108864] fs.inotify.max_user_instances Must be between [8192, 1048576] fs.inotify.max_user_watches Must be between [8192, 1048576] fs.nr_open Must be between [1048576, 2147483584] vm.dirty_background_ratio Must be between [1, 100] vm.dirty_background_bytes Must be between [0, 68719476736] vm.dirty_expire_centisecs Must be between [0, 6000] vm.dirty_ratio Must be between [1, 100] vm.dirty_bytes Must be between [0, 68719476736] vm.dirty_writeback_centisecs Must be between [0, 1000] vm.max_map_count Must be between [65536, 2147483647] vm.overcommit_memory Must be one of {0, 1, 2}. Not supported on machines with less than 15 GB memory. vm.overcommit_ratio Must be between [0, 100] vm.vfs_cache_pressure Must be between [0, 100] vm.swappiness Must be between [0, 200] vm.watermark_scale_factor Must be between [10, 3000] vm.min_free_kbytes Must be between [67584, 1048576] List of supported hugepage size in 'hugepageConfig'. KEY VALUE hugepage_size2m Number of 2M huge pages, any positive integer hugepage_size1g Number of 1G huge pages, any positive integer List of supported keys in 'swapConfig' under 'linuxConfig'. KEY VALUE enabled boolean encryptionConfig specify encryption settings for the swap space bootDiskProfile specify swap on the node's boot disk ephemeralLocalSsdProfile specify swap on the local SSD shared with pod ephemeral storage dedicatedLocalSsdProfile specify swap on a new, separate local NVMe SSD exclusively for swap List of supported keys in 'encryptionConfig' under 'swapConfig'. KEY VALUE disabled boolean List of supported keys in 'bootDiskProfile' under 'swapConfig'. KEY VALUE swapSizeGib integer swapSizePercent integer List of supported keys in 'ephemeralLocalSsdProfile' under 'swapConfig'. KEY VALUE swapSizeGib integer swapSizePercent integer List of supported keys in 'dedicatedLocalSsdProfile' under 'swapConfig'. KEY VALUE diskCount integer The upper limit for total allocated hugepage size differs based upon machine size. * On machines with less than 30 GB memory: 60% of the total memory. For example, on e2-standard-2 machine with 8 GB of memory, you can't allocate more than 4.8 GB for hugepages. * On machines with more than 30 GB memory: 80% of the total memory. For example, on c4a-standard-8 machines with 32 GB of memory, hugepages cannot exceed 25.6 GB. 1G hugepages are only available in following machine familes: c3, m2, c2d, c3d, h3, m3, a2, a3, g2. Supported values for 'cgroupMode' under 'linuxConfig'. * CGROUP_MODE_V1: Use cgroupv1 on the node pool. * CGROUP_MODE_V2: Use cgroupv2 on the node pool. * CGROUP_MODE_UNSPECIFIED: Use the default GKE cgroup configuration. Supported values for 'transparentHugepageEnabled' under 'linuxConfig' which controls transparent hugepage support for anonymous memory. * TRANSPARENT_HUGEPAGE_ENABLED_ALWAYS: Transparent hugepage is enabled system wide. * TRANSPARENT_HUGEPAGE_ENABLED_MADVISE: Transparent hugepage is enabled inside MADV_HUGEPAGE regions. This is the default kernel configuration. * TRANSPARENT_HUGEPAGE_ENABLED_NEVER: Transparent hugepage is disabled. * TRANSPARENT_HUGEPAGE_ENABLED_UNSPECIFIED: Default value. GKE will not modify the kernel configuration. Supported values for 'transparentHugepageDefrag' under 'linuxConfig' which defines the transparent hugepage defrag configuration on the node. * TRANSPARENT_HUGEPAGE_DEFRAG_ALWAYS: It means that an application requesting THP will stall on allocation failure and directly reclaim pages and compact memory in an effort to allocate a THP immediately. * TRANSPARENT_HUGEPAGE_DEFRAG_DEFER: It means that an application will wake kswapd in the background to reclaim pages and wake kcompactd to compact memory so that THP is available in the near future. It is the responsibility of khugepaged to then install the THP pages later. * TRANSPARENT_HUGEPAGE_DEFRAG_DEFER_WITH_MADVISE: It means that an application will enter direct reclaim and compaction like always, but only for regions that have used madvise(MADV_HUGEPAGE); all other regions will wake kswapd in the background to reclaim pages and wake kcompactd to compact memory so that THP is available in the near future. * TRANSPARENT_HUGEPAGE_DEFRAG_MADVISE: It means that an application will enter direct reclaim and compaction like always, but only for regions that have used madvise(MADV_HUGEPAGE); all other regions will wake kswapd in the background to reclaim pages and wake kcompactd to compact memory so that THP is available in the near future. * TRANSPARENT_HUGEPAGE_DEFRAG_NEVER: It means that an application will never enter direct reclaim or compaction. * TRANSPARENT_HUGEPAGE_DEFRAG_UNSPECIFIED: Default value. GKE will not modify the kernel configuration. Note, updating the system configuration of an existing node pool requires recreation of the nodes which which might cause a disruption. Use a full or relative path to a local file containing the value of system_config. |
| `--tags` | TAG,[TAG,...] |  | Applies the given Compute Engine tags (comma separated) on all nodes in the new node-pool. Example: $ gcloud container node-pools create node-pool-1 \ --cluster=example-cluster --tags=tag1,tag2 New nodes, including ones created by resize or recreate, will have these tags on the Compute Engine API instance object and can be used in firewall rules. See https://cloud.google.com/sdk/gcloud/reference/compute/firewall-rules/create for examples. |
| `--threads-per-core` | THREADS_PER_CORE |  | The number of visible threads per physical core for each node. To disable simultaneous multithreading (SMT) set this to 1. |
| `--tpu-topology` | TPU_TOPOLOGY |  | The desired physical topology for the PodSlice. $ gcloud container node-pools create node-pool-1 \ --cluster=example-cluster --tpu-topology |
| `--windows-os-version` | one of: ltsc2019, ltsc2022 |  | Specifies the Windows Server Image to use when creating a Windows node pool. Valid variants can be "ltsc2019", "ltsc2022". It means using LTSC2019 server image or LTSC2022 server image. If the node pool doesn't specify a Windows Server Image Os version, then Ltsc2019 will be the default one to use. WINDOWS_OS_VERSION must be one of: ltsc2019, ltsc2022. |
| `--workload-metadata` | one of: GCE_METADATA Pods running in this node pool have access to the node's underlying Compute Engine Metadata Server |  | Type of metadata server available to pods running in the node pool. WORKLOAD_METADATA must be one of: GCE_METADATA Pods running in this node pool have access to the node's underlying Compute Engine Metadata Server. GKE_METADATA Run the Kubernetes Engine Metadata Server on this node. The Kubernetes Engine Metadata Server exposes a metadata API to workloads that is compatible with the V1 Compute Metadata APIs exposed by the Compute Engine and App Engine Metadata Servers. This feature can only be enabled if Workload Identity is enabled at the cluster level. |


**Examples:**
```bash
To create a new node pool "node-pool-1" with the default options in the
cluster "sample-cluster", run:

    $ gcloud container node-pools create node-pool-1 \
        --cluster=sample-cluster

The new node pool will show up in the cluster after all the nodes have been
provisioned.

To create a node pool with 5 nodes, run:

    $ gcloud container node-pools create node-pool-1 \
        --cluster=sample-cluster --num-nodes=5
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/node-pools/create)

---
### `gcloud container node-pools delete`

Delete an existing node pool in a running cluster

gcloud container node-pools delete deletes a node pool from a Google
Kubernetes Engine (GKE) cluster. When you delete a node pool, GKE drains
all the nodes in the node pool. The draining process involves GKE deleting
Pods on each node in the node pool. Each node in a node pool is drained by
deleting Pods with an allotted graceful termination period of MAX_POD.
MAX_POD is the maximum terminationGracePeriodSeconds set on the Pods
scheduled to the node with a cap of one hour.

**Synopsis:**
```
gcloud container node-pools delete NAME [--async] [--cluster=CLUSTER]
    [--location=LOCATION | --region=REGION | --zone=ZONE, -z ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of the node pool to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--cluster` | CLUSTER |  | The cluster from which to delete the node pool. Overrides the default container/cluster property value for this command invocation. |


**Examples:**
```bash
To delete the "node-pool-1" node pool from the cluster "sample-cluster",
run:

    $ gcloud container node-pools delete node-pool-1 \
        --cluster=sample-cluster
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/node-pools/delete)

---
### `gcloud container node-pools describe`

Describe an existing node pool for a cluster

gcloud container node-pools describe displays all data associated with the
node pool in the Google Kubernetes Engine cluster.

**Synopsis:**
```
gcloud container node-pools describe NAME [--cluster=CLUSTER]
    [--location=LOCATION | --region=REGION | --zone=ZONE, -z ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of the node pool.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cluster` | CLUSTER |  | The name of the cluster. Overrides the default container/cluster property value for this command invocation. |


**Examples:**
```bash
To describe a node pool of an existing cluster, run:

    $ gcloud container node-pools describe node-pool-1 \
        --cluster=sample-cluster
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/node-pools/describe)

---
### `gcloud container node-pools get-upgrade-info`

Get upgrade information for an existing node pool for a cluster

gcloud container node-pools get-upgrade-info displays all upgrade
information associated with the node pool in the Google Kubernetes Engine
cluster.

**Synopsis:**
```
gcloud container node-pools get-upgrade-info NAME [--cluster=CLUSTER]
    [--location=LOCATION | --region=REGION | --zone=ZONE, -z ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of the node pool.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cluster` | CLUSTER |  | The name of the cluster. Overrides the default container/cluster property value for this command invocation. |


**Examples:**
```bash
To get upgrade information for a node pool of an existing cluster, run:

    $ gcloud container node-pools get-upgrade-info node-pool-1 \
        --cluster=sample-cluster
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/node-pools/get-upgrade-info)

---
### `gcloud container node-pools list`

List existing node pools for a cluster

gcloud container node-pools list displays all node pools in the Google
Kubernetes Engine cluster.

**Synopsis:**
```
gcloud container node-pools list [--cluster=CLUSTER]
    [--location=LOCATION | --region=REGION | --zone=ZONE, -z ZONE]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cluster` | CLUSTER |  | The name of the cluster. Overrides the default container/cluster property value for this command invocation. |


**Examples:**
```bash
To list all node pools in the cluster "sample-cluster" in table form, run:

    $ gcloud container node-pools list --cluster=sample-cluster
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/node-pools/list)

---
### `gcloud container node-pools rollback`

Rollback a node-pool upgrade

Rollback a node-pool upgrade.

Rollback is a method used after a canceled or failed node-pool upgrade. It
makes a best-effort attempt to revert the pool back to its original state.

**Synopsis:**
```
gcloud container node-pools rollback NAME [--async] [--cluster=CLUSTER]
    [--respect-pdb=RESPECT_PDB]
    [--location=LOCATION | --region=REGION | --zone=ZONE, -z ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of the node pool to rollback.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--cluster` | CLUSTER |  | The cluster from which to rollback the node pool. Overrides the default container/cluster property value for this command invocation. |
| `--respect-pdb` | RESPECT_PDB |  | Indicates whether node pool rollbacks should respect pod disruption budgets. |


**Examples:**
```bash
To roll back a canceled or failed upgrade in "node-pool-1" in the cluster
"sample-cluster", run:

    $ gcloud container node-pools rollback node-pool-1 \
        --cluster=sample-cluster
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/node-pools/rollback)

---
### `gcloud container node-pools update`

Updates a node pool in a running cluster

gcloud container node-pools update updates a node pool in a Google
Kubernetes Engine cluster.

**Synopsis:**
```
gcloud container node-pools update NAME
    (--accelerator=[type=TYPE,[count=COUNT,
      gpu-driver-version=GPU_DRIVER_VERSION,
      gpu-partition-size=GPU_PARTITION_SIZE,
      gpu-sharing-strategy=GPU_SHARING_STRATEGY,
      max-shared-clients-per-gpu=MAX_SHARED_CLIENTS_PER_GPU],...]
      | --confidential-node-type=CONFIDENTIAL_NODE_TYPE
      | --containerd-config-from-file=PATH_TO_FILE
      | --enable-confidential-nodes | --enable-gvnic
      | --enable-image-streaming | --enable-insecure-kubelet-readonly-port
      | --enable-kernel-module-signature-enforcement
      | --enable-private-nodes | --enable-queued-provisioning
      | --flex-start | --labels=[KEY=VALUE,...]
      | --logging-variant=LOGGING_VARIANT
      | --max-run-duration=MAX_RUN_DURATION
      | --network-performance-configs=[PROPERTY=VALUE,...]
      | --node-labels=[NODE_LABEL,...] | --node-locations=ZONE,[ZONE,...]
      | --node-taints=[NODE_TAINT,...]
      | --resource-manager-tags=[KEY=VALUE,...]
      | --storage-pools=STORAGE_POOL,[...]
      | --system-config-from-file=PATH_TO_FILE | --tags=[TAG,...]
      | --windows-os-version=WINDOWS_OS_VERSION
      | --workload-metadata=WORKLOAD_METADATA
      | --autoscaled-rollout-policy=[wait-for-drain-duration=WAIT-FOR-DRAIN-DURATION] --enable-blue-green-upgrade --enable-surge-upgrade --max-surge-upgrade=MAX_SURGE_UPGRADE --max-unavailable-upgrade=MAX_UNAVAILABLE_UPGRADE --node-pool-soak-duration=NODE_POOL_SOAK_DURATION --standard-rollout-policy=[batch-node-count=BATCH_NODE_COUNT,
      batch-percent=BATCH_NODE_PERCENTAGE,
      batch-soak-duration=BATCH_SOAK_DURATION,...]
      | --boot-disk-provisioned-iops=BOOT_DISK_PROVISIONED_IOPS
      --boot-disk-provisioned-throughput=BOOT_DISK_PROVISIONED_THROUGHPUT
      --disk-size=DISK_SIZE
      --disk-type=DISK_TYPE --machine-type=MACHINE_TYPE
      | --enable-autoprovisioning --enable-autoscaling
      --location-policy=LOCATION_POLICY --max-nodes=MAX_NODES
      --min-nodes=MIN_NODES
      --total-max-nodes=TOTAL_MAX_NODES --total-min-nodes=TOTAL_MIN_NODES
      | --enable-autorepair --enable-autoupgrade
      | --node-drain-grace-period-seconds=NODE_DRAIN_GRACE_PERIOD_SECONDS
      --node-drain-pdb-timeout-seconds=NODE_DRAIN_PDB_TIMEOUT_SECONDS
      --respect-pdb-during-node-pool-deletion) [--async]
    [--cluster=CLUSTER]
    [--location=LOCATION | --region=REGION | --zone=ZONE, -z ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of the node pool.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--accelerator` | one of: `default`: Install the default driver version for this GKE version |  | _[Exactly one of these must be specified:]_ Attaches accelerators (e.g. GPUs) to all nodes. type (Required) The specific type (e.g. nvidia-tesla-t4 for NVIDIA T4) of accelerator to attach to the instances. Use gcloud compute accelerator-types list to learn about all available accelerator types. count (Optional) The number of accelerators to attach to the instances. The default value is 1. gpu-driver-version (Optional) The NVIDIA driver version to install. GPU_DRIVER_VERSION must be one of: `default`: Install the default driver version for this GKE version. For GKE version 1.30.1-gke.1156000 and later, this is the default option. `latest`: Install the latest driver version available for this GKE version. Can only be used for nodes that use Container-Optimized OS. `disabled`: Skip automatic driver installation. You must manually install a driver after you create the cluster. For GKE version 1.30.1-gke.1156000 and earlier, this is the default option. To manually install the GPU driver, refer to https://cloud.google.com/kubernetes-engine/docs/how-to/gpus#installing_drivers. gpu-partition-size (Optional) The GPU partition size used when running multi-instance GPUs. For information about multi-instance GPUs, refer to: https://cloud.google.com/kubernetes-engine/docs/how-to/gpus-multi gpu-sharing-strategy (Optional) The GPU sharing strategy (e.g. time-sharing) to use. For information about GPU sharing, refer to: https://cloud.google.com/kubernetes-engine/docs/concepts/timesharing-gpus max-shared-clients-per-gpu (Optional) The max number of containers allowed to share each GPU on the node. This field is used together with gpu-sharing-strategy. |
| `--confidential-node-type` | one of: sev, sev_snp, tdx, disabled |  | _[Exactly one of these must be specified:]_ Recreate all the nodes in the node pool to be confidential VM https://docs.cloud.google.com/compute/docs/about-confidential-vm. CONFIDENTIAL_NODE_TYPE must be one of: sev, sev_snp, tdx, disabled. |
| `--containerd-config-from-file` | PATH_TO_FILE |  | _[Exactly one of these must be specified:]_ Path of the YAML file that contains containerd configuration entries like configuring access to private image registries. For detailed information on the configuration usage, please refer to https://cloud.google.com/kubernetes-engine/docs/how-to/customize-containerd-configuration. Note: Updating the containerd configuration of an existing cluster or node pool requires recreation of the existing nodes, which might cause disruptions in running workloads. Use a full or relative path to a local file containing the value of containerd_config. |
| `--enable-confidential-nodes` |  |  | _[Exactly one of these must be specified:]_ Recreate all the nodes in the node pool to be confidential VM https://docs.cloud.google.com/compute/docs/about-confidential-vm. |
| `--enable-gvnic` |  |  | _[Exactly one of these must be specified:]_ Enable the use of GVNIC for this cluster. Requires re-creation of nodes using either a node-pool upgrade or node-pool creation. |
| `--enable-image-streaming` |  |  | _[Exactly one of these must be specified:]_ Specifies whether to enable image streaming on node pool. |
| `--enable-insecure-kubelet-readonly-port` |  |  | _[Exactly one of these must be specified:]_ Enables the Kubelet's insecure read only port. To disable the readonly port on a cluster or node-pool set the flag to --no-enable-insecure-kubelet-readonly-port. |
| `--enable-kernel-module-signature-enforcement` |  |  | _[Exactly one of these must be specified:]_ Enforces that kernel modules are signed on all nodes in the node pool. This setting overrides the cluster-level setting. For example, if the cluster disables enforcement, you can enable enforcement only for a specific node pool. When the policy is modified on an existing node pool, nodes will be immediately recreated to use the new policy. Use --no-enable-kernel-module-signature-enforcement to disable. Examples: $ gcloud container node-pools update node-pool-1 \ --enable-kernel-module-signature-enforcement |
| `--enable-private-nodes` |  |  | _[Exactly one of these must be specified:]_ Enables provisioning nodes with private IP addresses only. The control plane still communicates with all nodes through private IP addresses only, regardless of whether private nodes are enabled or disabled. |
| `--enable-queued-provisioning` |  |  | _[Exactly one of these must be specified:]_ Mark the nodepool as Queued only. This means that all new nodes can be obtained only through queuing via ProvisioningRequest API. $ gcloud container node-pools update node-pool-1 \ --cluster=example-cluster --enable-queued-provisioning ... and other required parameters, for more details see: https://cloud.google.com/kubernetes-engine/docs/how-to/provisioningrequest |
| `--flex-start` |  |  | _[Exactly one of these must be specified:]_ Start the node pool with Flex Start provisioning model. $ gcloud container node-pools update node-pool-1 \ --cluster=example-cluster --flex-start and other required parameters, for more details see: https://cloud.google.com/kubernetes-engine/docs/how-to/provisioningrequest |
| `--labels` | [KEY=VALUE,...] |  | _[Exactly one of these must be specified:]_ Labels to apply to the Google Cloud resources of node pools in the Kubernetes Engine cluster. These are unrelated to Kubernetes labels. Warning: Updating this label will causes the node(s) to be recreated. Examples: $ gcloud container node-pools update node-pool-1 \ --cluster=example-cluster --labels=label1=value1,label2=value2 |
| `--logging-variant` | one of: DEFAULT 'DEFAULT' variant requests minimal resources but may not guarantee high throughput |  | _[Exactly one of these must be specified:]_ Specifies the logging variant that will be deployed on all the nodes in the node pool. If the node pool doesn't specify a logging variant, then the logging variant specified for the cluster will be deployed on all the nodes in the node pool. Valid logging variants are MAX_THROUGHPUT, DEFAULT. LOGGING_VARIANT must be one of: DEFAULT 'DEFAULT' variant requests minimal resources but may not guarantee high throughput. MAX_THROUGHPUT 'MAX_THROUGHPUT' variant requests more node resources and is able to achieve logging throughput up to 10MB per sec. |
| `--max-run-duration` | MAX_RUN_DURATION |  | _[Exactly one of these must be specified:]_ Limit the runtime of each node in the node pool to the specified duration. $ gcloud container node-pools update node-pool-1 \ --cluster=example-cluster --max-run-duration=3600s |
| `--network-performance-configs` | [PROPERTY=VALUE,...] |  | _[Exactly one of these must be specified:]_ Configures network performance settings for the node pool. If this flag is not specified, the pool will be created with its default network performance configuration. total-egress-bandwidth-tier Total egress bandwidth is the available outbound bandwidth from a VM, regardless of whether the traffic is going to internal IP or external IP destinations. The following tier values are allowed: [TIER_UNSPECIFIED,TIER_1] |
| `--node-labels` | [NODE_LABEL,...] |  | _[Exactly one of these must be specified:]_ Replaces all the user specified Kubernetes labels on all nodes in an existing node pool with the given labels. Examples: $ gcloud container node-pools update node-pool-1 \ --cluster=example-cluster \ --node-labels=label1=value1,label2=value2 Updating the node pool's --node-labels flag applies the labels to the Kubernetes Node objects for existing nodes in-place; it does not re-create or replace nodes. New nodes, including ones created by resizing or re-creating nodes, will have these labels on the Kubernetes API Node object. The labels can be used in the nodeSelector field. See https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node/ for examples. Note that Kubernetes labels, intended to associate cluster components and resources with one another and manage resource lifecycles, are different from Google Kubernetes Engine labels that are used for the purpose of tracking billing and usage information. |
| `--node-locations` | ZONE,[ZONE,...] |  | _[Exactly one of these must be specified:]_ Set of zones in which the node pool's nodes should be located. Changing the locations for a node pool will result in nodes being either created or removed from the node pool, depending on whether locations are being added or removed. Multiple locations can be specified, separated by commas. For example: $ gcloud container node-pools update node-pool-1 \ --cluster=sample-cluster \ --node-locations=us-central1-a,us-central1-b |
| `--node-taints` | [NODE_TAINT,...] |  | _[Exactly one of these must be specified:]_ Replaces all the user specified Kubernetes taints on all nodes in an existing node pool, which can be used with tolerations for pod scheduling. Examples: $ gcloud container node-pools update node-pool-1 \ --cluster=example-cluster \ --node-taints=key1=val1:NoSchedule,key2=val2:PreferNoSchedule To read more about node-taints, see https://cloud.google.com/kubernetes-engine/docs/node-taints. |
| `--resource-manager-tags` | [KEY=VALUE,...] |  | _[Exactly one of these must be specified:]_ Replaces all the user specified resource manager tags on all nodes in an existing node pool in a Standard cluster with the given comma-separated resource manager tags that has the GCE_FIREWALL purpose. Examples: $ gcloud container node-pools update example-node-pool \ --resource-manager-tags=tagKeys/1234=tagValues/2345 $ gcloud container node-pools update example-node-pool \ --resource-manager-tags=my-project/key1=value1 $ gcloud container node-pools update example-node-pool \ --resource-manager-tags=12345/key1=value1,23456/key2=value2 $ gcloud container node-pools update example-node-pool \ --resource-manager-tags= All nodes, including nodes that are resized or re-created, will have the specified tags on the corresponding Instance object in the Compute Engine API. You can reference these tags in network firewall policy rules. For instructions, see https://cloud.google.com/firewall/docs/use-tags-for-firewalls. |
| `--storage-pools` | STORAGE_POOL,[...] |  | _[Exactly one of these must be specified:]_ A list of storage pools where the node pool's boot disks will be provisioned. Replaces all the current storage pools of an existing node pool, with the specified storage pools. STORAGE_POOL must be in the format projects/project/zones/zone/storagePools/storagePool |
| `--system-config-from-file` | PATH_TO_FILE |  | _[Exactly one of these must be specified:]_ Path of the YAML/JSON file that contains the node configuration, including Linux kernel parameters (sysctls) and kubelet configs. Examples: kubeletConfig: cpuManagerPolicy: static memoryManager: policy: Static topologyManager: policy: BestEffort scope: pod linuxConfig: sysctl: net.core.somaxconn: '2048' net.ipv4.tcp_rmem: '4096 87380 6291456' hugepageConfig: hugepage_size2m: '1024' hugepage_size1g: '2' swapConfig: enabled: true bootDiskProfile: swapSizeGib: 8 cgroupMode: 'CGROUP_MODE_V2' List of supported kubelet configs in 'kubeletConfig'. KEY VALUE cpuManagerPolicy either 'static' or 'none' cpuCFSQuota true or false (enabled by default) cpuCFSQuotaPeriod interval (e.g., '100ms'. The value must be between 1ms and 1 second, inclusive.) memoryManager specify memory manager policy topologyManager specify topology manager policy and scope podPidsLimit integer (The value must be greater than or equal to 1024 and less than 4194304.) containerLogMaxSize positive number plus unit suffix (e.g., '100Mi', '0.2Gi'. The value must be between 10Mi and 500Mi, inclusive.) containerLogMaxFiles integer (The value must be between [2, 10].) imageGcLowThresholdPercent integer (The value must be between [10, 85], and lower than imageGcHighThresholdPercent.) imageGcHighThresholdPercent integer (The value must be between [10, 85], and greater than imageGcLowThresholdPercent.) imageMinimumGcAge interval (e.g., '100s', '1m'. The value must be less than '2m'.) imageMaximumGcAge interval (e.g., '100s', '1m'. The value must be greater than imageMinimumGcAge.) evictionSoft specify eviction soft thresholds evictionSoftGracePeriod specify eviction soft grace period evictionMinimumReclaim specify eviction minimum reclaim thresholds evictionMaxPodGracePeriodSeconds integer (Max grace period for pod termination during eviction, in seconds. The value must be between [0, 300].) allowedUnsafeSysctls list of sysctls (Allowlisted groups: 'kernel.shm*', 'kernel.msg*', 'kernel.sem', 'fs.mqueue.*', and 'net.*', and sysctls under the groups.) singleProcessOomKill true or false maxParallelImagePulls integer (The value must be between [2, 5].) List of supported keys in memoryManager in 'kubeletConfig'. KEY VALUE policy either 'Static' or 'None' List of supported keys in topologyManager in 'kubeletConfig'. KEY VALUE policy either 'none' or 'best-effort' or 'single-numa-node' or 'restricted' scope either 'pod' or 'container' List of supported keys in evictionSoft in 'kubeletConfig'. KEY VALUE memoryAvailable quantity (e.g., '100Mi', '1Gi'. Represents the amount of memory available before soft eviction. The value must be at least 100Mi and less than 50% of the node's memory.) nodefsAvailable percentage (e.g., '20%'. Represents the nodefs available before soft eviction. The value must be between 10% and 50%, inclusive.) nodefsInodesFree percentage (e.g., '20%'. Represents the nodefs inodes free before soft eviction. The value must be between 5% and 50%, inclusive.) imagefsAvailable percentage (e.g., '20%'. Represents the imagefs available before soft eviction. The value must be between 15% and 50%, inclusive.) imagefsInodesFree percentage (e.g., '20%'. Represents the imagefs inodes free before soft eviction. The value must be between 5% and 50%, inclusive.) pidAvailable percentage (e.g., '20%'. Represents the pid available before soft eviction. The value must be between 10% and 50%, inclusive.) List of supported keys in evictionSoftGracePeriod in 'kubeletConfig'. KEY VALUE memoryAvailable duration (e.g., '30s', '1m'. The grace period for soft eviction for this resource. The value must be positive and no more than '5m'.) nodefsAvailable duration (e.g., '30s', '1m'. The grace period for soft eviction for this resource. The value must be positive and no more than '5m'.) nodefsInodesFree duration (e.g., '30s', '1m'. The grace period for soft eviction for this resource. The value must be positive and no more than '5m'.) imagefsAvailable duration (e.g., '30s', '1m'. The grace period for soft eviction for this resource. The value must be positive and no more than '5m'.) imagefsInodesFree duration (e.g., '30s', '1m'. The grace period for soft eviction for this resource. The value must be positive and no more than '5m'.) pidAvailable duration (e.g., '30s', '1m'. The grace period for soft eviction for this resource. The value must be positive and no more than '5m'.) List of supported keys in evictionMinimumReclaim in 'kubeletConfig'. KEY VALUE memoryAvailable percentage (e.g., '5%'. Represents the minimum reclaim threshold for memory available. The value must be positive and no more than 10%.) nodefsAvailable percentage (e.g., '5%'. Represents the minimum reclaim threshold for nodefs available. The value must be positive and no more than 10%.) nodefsInodesFree percentage (e.g., '5%'. Represents the minimum reclaim threshold for nodefs inodes free. The value must be positive and no more than 10%.) imagefsAvailable percentage (e.g., '5%'. Represents the minimum reclaim threshold for imagefs available. The value must be positive and no more than 10%.) imagefsInodesFree percentage (e.g., '5%'. Represents the minimum reclaim threshold for imagefs inodes free. The value must be positive and no more than 10%.) pidAvailable percentage (e.g., '5%'. Represents the minimum reclaim threshold for pid available. The value must be positive and no more than 10%.) List of supported sysctls in 'linuxConfig'. KEY VALUE net.core.netdev_max_backlog Any positive integer, less than 2147483647 net.core.rmem_default Must be between [2304, 2147483647] net.core.rmem_max Must be between [2304, 2147483647] net.core.wmem_default Must be between [4608, 2147483647] net.core.wmem_max Must be between [4608, 2147483647] net.core.optmem_max Any positive integer, less than 2147483647 net.core.somaxconn Must be between [128, 2147483647] net.ipv4.tcp_rmem Any positive integer tuple net.ipv4.tcp_wmem Any positive integer tuple net.ipv4.tcp_tw_reuse Must be {0, 1, 2} net.ipv4.tcp_mtu_probing Must be {0, 1, 2} net.ipv4.tcp_max_orphans Must be between [16384, 262144] net.ipv4.tcp_max_tw_buckets Must be between [4096, 2147483647] net.ipv4.tcp_syn_retries Must be between [1, 127] net.ipv4.tcp_ecn Must be {0, 1, 2} net.ipv4.tcp_congestion_control Supported values for COS: 'reno', 'cubic', 'bbr', 'lp', 'htcp'. Supported values for Ubuntu: 'reno', 'cubic', 'bbr', 'lp', 'htcp', 'vegas', 'dctcp', 'bic', 'cdg', 'highspeed', 'hybla', 'illinois', 'nv', 'scalable', 'veno', 'westwood', 'yeah'. net.netfilter.nf_conntrack_max Must be between [65536, 4194304] net.netfilter.nf_conntrack_buckets Must be between [65536, 524288]. Recommend setting: nf_conntrack_max = nf_conntrack_buc kets * 4 net.netfilter.nf_conntrack_tcp_timeout_close_wait Must be between [60, 3600] net.netfilter.nf_conntrack_tcp_timeout_time_wait Must be between [1, 600] net.netfilter.nf_conntrack_tcp_timeout_established Must be between [600, 86400] net.netfilter.nf_conntrack_acct Must be {0, 1} kernel.shmmni Must be between [4096, 32768] kernel.shmmax Must be between [0, 1844674407369277 4399] kernel.shmall Must be between [0, 1844674407369277 4399] kernel.perf_event_paranoid Must be {-1, 0, 1, 2, 3} kernel.sched_rt_runtime_us Must be [-1, 1000000] kernel.softlockup_panic Must be {0, 1} kernel.yama.ptrace_scope Must be {0, 1, 2, 3} kernel.kptr_restrict Must be {0, 1, 2} kernel.dmesg_restrict Must be {0, 1} kernel.sysrq Must be [0, 511] fs.aio-max-nr Must be between [65536, 4194304] fs.file-max Must be between [104857, 67108864] fs.inotify.max_user_instances Must be between [8192, 1048576] fs.inotify.max_user_watches Must be between [8192, 1048576] fs.nr_open Must be between [1048576, 2147483584] vm.dirty_background_ratio Must be between [1, 100] vm.dirty_background_bytes Must be between [0, 68719476736] vm.dirty_expire_centisecs Must be between [0, 6000] vm.dirty_ratio Must be between [1, 100] vm.dirty_bytes Must be between [0, 68719476736] vm.dirty_writeback_centisecs Must be between [0, 1000] vm.max_map_count Must be between [65536, 2147483647] vm.overcommit_memory Must be one of {0, 1, 2}. Not supported on machines with less than 15 GB memory. vm.overcommit_ratio Must be between [0, 100] vm.vfs_cache_pressure Must be between [0, 100] vm.swappiness Must be between [0, 200] vm.watermark_scale_factor Must be between [10, 3000] vm.min_free_kbytes Must be between [67584, 1048576] List of supported hugepage size in 'hugepageConfig'. KEY VALUE hugepage_size2m Number of 2M huge pages, any positive integer hugepage_size1g Number of 1G huge pages, any positive integer List of supported keys in 'swapConfig' under 'linuxConfig'. KEY VALUE enabled boolean encryptionConfig specify encryption settings for the swap space bootDiskProfile specify swap on the node's boot disk ephemeralLocalSsdProfile specify swap on the local SSD shared with pod ephemeral storage dedicatedLocalSsdProfile specify swap on a new, separate local NVMe SSD exclusively for swap List of supported keys in 'encryptionConfig' under 'swapConfig'. KEY VALUE disabled boolean List of supported keys in 'bootDiskProfile' under 'swapConfig'. KEY VALUE swapSizeGib integer swapSizePercent integer List of supported keys in 'ephemeralLocalSsdProfile' under 'swapConfig'. KEY VALUE swapSizeGib integer swapSizePercent integer List of supported keys in 'dedicatedLocalSsdProfile' under 'swapConfig'. KEY VALUE diskCount integer The upper limit for total allocated hugepage size differs based upon machine size. + On machines with less than 30 GB memory: 60% of the total memory. For example, on e2-standard-2 machine with 8 GB of memory, you can't allocate more than 4.8 GB for hugepages. + On machines with more than 30 GB memory: 80% of the total memory. For example, on c4a-standard-8 machines with 32 GB of memory, hugepages cannot exceed 25.6 GB. 1G hugepages are only available in following machine familes: c3, m2, c2d, c3d, h3, m3, a2, a3, g2. Supported values for 'cgroupMode' under 'linuxConfig'. + CGROUP_MODE_V1: Use cgroupv1 on the node pool. + CGROUP_MODE_V2: Use cgroupv2 on the node pool. + CGROUP_MODE_UNSPECIFIED: Use the default GKE cgroup configuration. Supported values for 'transparentHugepageEnabled' under 'linuxConfig' which controls transparent hugepage support for anonymous memory. + TRANSPARENT_HUGEPAGE_ENABLED_ALWAYS: Transparent hugepage is enabled system wide. + TRANSPARENT_HUGEPAGE_ENABLED_MADVISE: Transparent hugepage is enabled inside MADV_HUGEPAGE regions. This is the default kernel configuration. + TRANSPARENT_HUGEPAGE_ENABLED_NEVER: Transparent hugepage is disabled. + TRANSPARENT_HUGEPAGE_ENABLED_UNSPECIFIED: Default value. GKE will not modify the kernel configuration. Supported values for 'transparentHugepageDefrag' under 'linuxConfig' which defines the transparent hugepage defrag configuration on the node. + TRANSPARENT_HUGEPAGE_DEFRAG_ALWAYS: It means that an application requesting THP will stall on allocation failure and directly reclaim pages and compact memory in an effort to allocate a THP immediately. + TRANSPARENT_HUGEPAGE_DEFRAG_DEFER: It means that an application will wake kswapd in the background to reclaim pages and wake kcompactd to compact memory so that THP is available in the near future. It is the responsibility of khugepaged to then install the THP pages later. + TRANSPARENT_HUGEPAGE_DEFRAG_DEFER_WITH_MADVISE: It means that an application will enter direct reclaim and compaction like always, but only for regions that have used madvise(MADV_HUGEPAGE); all other regions will wake kswapd in the background to reclaim pages and wake kcompactd to compact memory so that THP is available in the near future. + TRANSPARENT_HUGEPAGE_DEFRAG_MADVISE: It means that an application will enter direct reclaim and compaction like always, but only for regions that have used madvise(MADV_HUGEPAGE); all other regions will wake kswapd in the background to reclaim pages and wake kcompactd to compact memory so that THP is available in the near future. + TRANSPARENT_HUGEPAGE_DEFRAG_NEVER: It means that an application will never enter direct reclaim or compaction. + TRANSPARENT_HUGEPAGE_DEFRAG_UNSPECIFIED: Default value. GKE will not modify the kernel configuration. Note, updating the system configuration of an existing node pool requires recreation of the nodes which which might cause a disruption. Use a full or relative path to a local file containing the value of system_config. |
| `--tags` | [TAG,...] |  | _[Exactly one of these must be specified:]_ Replaces all the user specified Compute Engine tags on all nodes in an existing node pool with the given tags (comma separated). Examples: $ gcloud container node-pools update node-pool-1 \ --cluster=example-cluster --tags=tag1,tag2 New nodes, including ones created by resize or recreate, will have these tags on the Compute Engine API instance object and these tags can be used in firewall rules. See https://cloud.google.com/sdk/gcloud/reference/compute/firewall-rules/create for examples. |
| `--windows-os-version` | one of: ltsc2019, ltsc2022 |  | _[Exactly one of these must be specified:]_ Specifies the Windows Server Image to use when creating a Windows node pool. Valid variants can be "ltsc2019", "ltsc2022". It means using LTSC2019 server image or LTSC2022 server image. If the node pool doesn't specify a Windows Server Image Os version, then Ltsc2019 will be the default one to use. WINDOWS_OS_VERSION must be one of: ltsc2019, ltsc2022. |
| `--workload-metadata` | one of: GCE_METADATA Pods running in this node pool have access to the node's underlying Compute Engine Metadata Server |  | _[Exactly one of these must be specified:]_ Type of metadata server available to pods running in the node pool. WORKLOAD_METADATA must be one of: GCE_METADATA Pods running in this node pool have access to the node's underlying Compute Engine Metadata Server. GKE_METADATA Run the Kubernetes Engine Metadata Server on this node. The Kubernetes Engine Metadata Server exposes a metadata API to workloads that is compatible with the V1 Compute Metadata APIs exposed by the Compute Engine and App Engine Metadata Servers. This feature can only be enabled if Workload Identity is enabled at the cluster level. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--cluster` | CLUSTER |  | The name of the cluster. Overrides the default container/cluster property value for this command invocation. |


**Examples:**
```bash
To turn on node autoupgrade in "node-pool-1" in the cluster
"sample-cluster", run:

    $ gcloud container node-pools update node-pool-1 \
        --cluster=sample-cluster --enable-autoupgrade
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/node-pools/update)

---
# gcloud container clusters

deploy and teardown Google Kubernetes Engine clusters

### `gcloud container clusters check-autopilot-compatibility`

Check autopilot compatibility of a running cluster

Check autopilot compatibility of a running cluster.

For clusters with GKE version 1.31.6-gke.1027000 or later, you must enable
the control plane component that performs the check by running the gcloud
container clusters update command with the
`--enable-autopilot-compatiblity-auditing`
(https://cloud.google.com/sdk/gcloud/reference/container/clusters/update#--%5Bno-%5Denable-autopilot-compatibility-auditing)
flag.

**Synopsis:**
```
gcloud container clusters check-autopilot-compatibility NAME
    [--location=LOCATION | --region=REGION | --zone=ZONE, -z ZONE]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of this cluster.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[At most one of these can be specified:]_ Compute zone or region (e.g. us-central1-a or us-central1) for the cluster. Overrides the default compute/region or compute/zone value for this command invocation. Prefer using this flag over the --region or --zone flags. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Compute region (e.g. us-central1) for a regional cluster. Overrides the default compute/region property value for this command invocation. |
| `--zone` | ZONE, -z ZONE |  | _[At most one of these can be specified:]_ Compute zone (e.g. us-central1-a) for a zonal cluster. Overrides the default compute/zone property value for this command invocation. |


**Examples:**
```bash
To check autopilot compatibility of an existing cluster, run:

    $ gcloud container clusters check-autopilot-compatibility \
        sample-cluster
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/clusters/check-autopilot-compatibility)

---
### `gcloud container clusters create`

Create a cluster for running containers

Create a cluster for running containers.

**Synopsis:**
```
gcloud container clusters create NAME
    [--accelerator=[type=TYPE,[count=COUNT,
      gpu-driver-version=GPU_DRIVER_VERSION,
      gpu-partition-size=GPU_PARTITION_SIZE,
      gpu-sharing-strategy=GPU_SHARING_STRATEGY,
      max-shared-clients-per-gpu=MAX_SHARED_CLIENTS_PER_GPU],...]]
    [--additional-zones=ZONE,[ZONE,...]]
    [--addons=[ADDON[=ENABLED|DISABLED],...]]
    [--alpha-cluster-feature-gates=[FEATURE=true|false,...]]
    [--anonymous-authentication-config=ANONYMOUS_AUTHENTICATION_CONFIG]
    [--async] [--auto-monitoring-scope=AUTO_MONITORING_SCOPE]
    [--autopilot-workload-policies=WORKLOAD_POLICIES]
    [--autoprovisioning-enable-insecure-kubelet-readonly-port]
    [--autoprovisioning-network-tags=TAGS,[TAGS,...]]
    [--autoprovisioning-resource-manager-tags=[KEY=VALUE,...]]
    [--autoscaling-profile=AUTOSCALING_PROFILE]
    [--boot-disk-kms-key=BOOT_DISK_KMS_KEY]
    [--cloud-run-config=[load-balancer-type=EXTERNAL,...]]
    [--cluster-ipv4-cidr=CLUSTER_IPV4_CIDR]
    [--cluster-secondary-range-name=NAME]
    [--cluster-version=CLUSTER_VERSION]
    [--confidential-node-type=CONFIDENTIAL_NODE_TYPE]
    [--containerd-config-from-file=PATH_TO_FILE]
    [--create-subnetwork=[KEY=VALUE,...]]
    [--data-cache-count=DATA_CACHE_COUNT]
    [--database-encryption-key=DATABASE_ENCRYPTION_KEY]
    [--default-max-pods-per-node=DEFAULT_MAX_PODS_PER_NODE]
    [--disable-default-snat] [--disable-l4-lb-firewall-reconciliation]
    [--disk-size=DISK_SIZE] [--disk-type=DISK_TYPE]
    [--enable-authorized-networks-on-private-endpoint] [--enable-auto-ipam]
    [--enable-autorepair] [--no-enable-autoupgrade]
    [--enable-cilium-clusterwide-network-policy] [--enable-cloud-logging]
    [--enable-cloud-monitoring] [--enable-cloud-run-alpha]
    [--enable-confidential-nodes] [--enable-confidential-storage]
    [--enable-cost-allocation] [--enable-dataplane-v2]
    [--enable-default-compute-class] [--enable-dns-access] [--enable-fleet]
    [--enable-fqdn-network-policy] [--enable-google-cloud-access]
    [--enable-gvnic] [--enable-identity-service] [--enable-image-streaming]
    [--enable-insecure-kubelet-readonly-port]
    [--enable-intra-node-visibility] [--enable-ip-access]
    [--enable-ip-alias] [--enable-k8s-certs-via-dns]
    [--enable-k8s-tokens-via-dns]
    [--enable-kernel-module-signature-enforcement]
    [--enable-kubernetes-alpha]
    [--enable-kubernetes-unstable-apis=API,[API,...]]
    [--enable-l4-ilb-subsetting] [--enable-legacy-authorization]
    [--enable-legacy-lustre-port] [--enable-managed-prometheus]
    [--enable-master-global-access] [--enable-multi-networking]
    [--enable-nested-virtualization] [--enable-network-policy]
    [--enable-ray-cluster-logging] [--enable-ray-cluster-monitoring]
    [--enable-service-externalips] [--enable-shielded-nodes]
    [--enable-stackdriver-kubernetes] [--enable-vertical-pod-autoscaling]
    [--fleet-project=PROJECT_ID_OR_NUMBER] [--gateway-api=GATEWAY_API]
    [--hpa-profile=HPA_PROFILE] [--image-type=IMAGE_TYPE]
    [--in-transit-encryption=IN_TRANSIT_ENCRYPTION]
    [--ipv6-access-type=IPV6_ACCESS_TYPE] [--issue-client-certificate]
    [--labels=[KEY=VALUE,...]] [--logging=[COMPONENT,...]]
    [--logging-variant=LOGGING_VARIANT]
    [--machine-type=MACHINE_TYPE, -m MACHINE_TYPE]
    [--max-nodes-per-pool=MAX_NODES_PER_POOL]
    [--max-pods-per-node=MAX_PODS_PER_NODE]
    [--max-surge-upgrade=MAX_SURGE_UPGRADE; default=1]
    [--max-unavailable-upgrade=MAX_UNAVAILABLE_UPGRADE]
    [--membership-type=MEMBERSHIP_TYPE]
    [--metadata=KEY=VALUE,[KEY=VALUE,...]]
    [--metadata-from-file=KEY=LOCAL_FILE_PATH,[...]]
    [--min-cpu-platform=PLATFORM] [--monitoring=[COMPONENT,...]]
    [--network=NETWORK]
    [--network-performance-configs=[PROPERTY1=VALUE1,...]]
    [--node-labels=[NODE_LABEL,...]] [--node-locations=ZONE,[ZONE,...]]
    [--node-taints=[NODE_TAINT,...]] [--node-version=NODE_VERSION]
    [--notification-config=[pubsub=ENABLED|DISABLED,
      pubsub-topic=TOPIC,...]] [--num-nodes=NUM_NODES; default=3]
    [--patch-update=[PATCH_UPDATE]]
    [--performance-monitoring-unit=PERFORMANCE_MONITORING_UNIT]
    [--placement-policy=PLACEMENT_POLICY] [--placement-type=PLACEMENT_TYPE]
    [--preemptible] [--private-endpoint-subnetwork=NAME]
    [--private-ipv6-google-access-type=PRIVATE_IPV6_GOOGLE_ACCESS_TYPE]
    [--release-channel=CHANNEL] [--resource-manager-tags=[KEY=VALUE,...]]
    [--security-group=SECURITY_GROUP] [--security-posture=SECURITY_POSTURE]
    [--services-ipv4-cidr=CIDR] [--services-secondary-range-name=NAME]
    [--shielded-integrity-monitoring] [--shielded-secure-boot] [--spot]
    [--stack-type=STACK_TYPE] [--storage-pools=STORAGE_POOL,[...]]
    [--subnetwork=SUBNETWORK] [--system-config-from-file=PATH_TO_FILE]
    [--tags=TAG,[TAG,...]] [--threads-per-core=THREADS_PER_CORE]
    [--tier=TIER] [--workload-metadata=WORKLOAD_METADATA]
    [--workload-pool=WORKLOAD_POOL]
    [--workload-vulnerability-scanning=WORKLOAD_VULNERABILITY_SCANNING]
    [--aggregation-ca=CA_POOL_PATH --cluster-ca=CA_POOL_PATH
      --control-plane-disk-encryption-key=KEY --etcd-api-ca=CA_POOL_PATH
      --etcd-peer-ca=CA_POOL_PATH --gkeops-etcd-backup-encryption-key=KEY
      --service-account-signing-keys=KEY_VERSION,[KEY_VERSION,...]
      --service-account-verification-keys=KEY_VERSION,[KEY_VERSION,...]]
    [--binauthz-evaluation-mode=BINAUTHZ_EVALUATION_MODE
      | --enable-binauthz]
    [--boot-disk-provisioned-iops=BOOT_DISK_PROVISIONED_IOPS
      --boot-disk-provisioned-throughput=BOOT_DISK_PROVISIONED_THROUGHPUT]
    [--cluster-dns=CLUSTER_DNS --cluster-dns-domain=CLUSTER_DNS_DOMAIN
      --cluster-dns-scope=CLUSTER_DNS_SCOPE
      --additive-vpc-scope-dns-domain=ADDITIVE_VPC_SCOPE_DNS_DOMAIN
      | --disable-additive-vpc-scope]
    [--dataplane-v2-observability-mode=DATAPLANE_V2_OBSERVABILITY_MODE
      | --disable-dataplane-v2-flow-observability
      | --enable-dataplane-v2-flow-observability]
    [--disable-dataplane-v2-metrics | --enable-dataplane-v2-metrics]
    [[--enable-autoprovisioning
      : --autoprovisioning-config-file=PATH_TO_FILE
      | [--max-cpu=MAX_CPU --max-memory=MAX_MEMORY
      : --autoprovisioning-image-type=AUTOPROVISIONING_IMAGE_TYPE
      --autoprovisioning-locations=ZONE,[ZONE,...]
      --autoprovisioning-min-cpu-platform=PLATFORM --min-cpu=MIN_CPU
      --min-memory=MIN_MEMORY
      --autoprovisioning-max-surge-upgrade=AUTOPROVISIONING_MAX_SURGE_UPGRADE --autoprovisioning-max-unavailable-upgrade=AUTOPROVISIONING_MAX_UNAVAILABLE_UPGRADE --autoprovisioning-node-pool-soak-duration=AUTOPROVISIONING_NODE_POOL_SOAK_DURATION --autoprovisioning-standard-rollout-policy=[batch-node-count=BATCH_NODE_COUNT,
      batch-percent=BATCH_NODE_PERCENTAGE,
      batch-soak-duration=BATCH_SOAK_DURATION,...]
      --enable-autoprovisioning-blue-green-upgrade
      | --enable-autoprovisioning-surge-upgrade
      --autoprovisioning-scopes=[SCOPE,...]
      --autoprovisioning-service-account=AUTOPROVISIONING_SERVICE_ACCOUNT
      --enable-autoprovisioning-autorepair
      --enable-autoprovisioning-autoupgrade
      [--max-accelerator=[type=TYPE,count=COUNT,...]
      : --min-accelerator=[type=TYPE,count=COUNT,...]]]]]
    [--enable-autoscaling --location-policy=LOCATION_POLICY
      --max-nodes=MAX_NODES --min-nodes=MIN_NODES
      --total-max-nodes=TOTAL_MAX_NODES --total-min-nodes=TOTAL_MIN_NODES]
    [--enable-insecure-binding-system-authenticated
      --enable-insecure-binding-system-unauthenticated]
    [--enable-master-authorized-networks
      --master-authorized-networks=NETWORK,[NETWORK,...]]
    [--enable-network-egress-metering
      --enable-resource-consumption-metering
      --resource-usage-bigquery-dataset=RESOURCE_USAGE_BIGQUERY_DATASET]
    [--enable-private-endpoint
      --enable-private-nodes --master-ipv4-cidr=MASTER_IPV4_CIDR]
    [--enable-secret-manager --enable-secret-manager-rotation
      --secret-manager-rotation-interval=SECRET_MANAGER_ROTATION_INTERVAL]
    [--ephemeral-storage-local-ssd[=[count=COUNT]]
      | --local-nvme-ssd-block[=[count=COUNT]]
      | --local-ssd-count=LOCAL_SSD_COUNT]
    [--location=LOCATION | --region=REGION | --zone=ZONE, -z ZONE]
    [--maintenance-window=START_TIME | --maintenance-window-end=TIME_STAMP
      --maintenance-window-recurrence=RRULE
      --maintenance-window-start=TIME_STAMP]
    [--password=PASSWORD --enable-basic-auth
      | --username=USERNAME, -u USERNAME]
    [--reservation=RESERVATION --reservation-affinity=RESERVATION_AFFINITY]
    [--scopes=[SCOPE,...];
      default="gke-default" --service-account=SERVICE_ACCOUNT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of the cluster to create.

   The name may contain only lowercase alphanumerics and '-', must start
   with a letter and end with an alphanumeric, and must be no longer than
   40 characters.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--accelerator` | one of: `default`: Install the default driver version for this GKE version |  | Attaches accelerators (e.g. GPUs) to all nodes. type (Required) The specific type (e.g. nvidia-tesla-t4 for NVIDIA T4) of accelerator to attach to the instances. Use gcloud compute accelerator-types list to learn about all available accelerator types. count (Optional) The number of accelerators to attach to the instances. The default value is 1. gpu-driver-version (Optional) The NVIDIA driver version to install. GPU_DRIVER_VERSION must be one of: `default`: Install the default driver version for this GKE version. For GKE version 1.30.1-gke.1156000 and later, this is the default option. `latest`: Install the latest driver version available for this GKE version. Can only be used for nodes that use Container-Optimized OS. `disabled`: Skip automatic driver installation. You must manually install a driver after you create the cluster. For GKE version 1.30.1-gke.1156000 and earlier, this is the default option. To manually install the GPU driver, refer to https://cloud.google.com/kubernetes-engine/docs/how-to/gpus#installing_drivers. gpu-partition-size (Optional) The GPU partition size used when running multi-instance GPUs. For information about multi-instance GPUs, refer to: https://cloud.google.com/kubernetes-engine/docs/how-to/gpus-multi gpu-sharing-strategy (Optional) The GPU sharing strategy (e.g. time-sharing) to use. For information about GPU sharing, refer to: https://cloud.google.com/kubernetes-engine/docs/concepts/timesharing-gpus max-shared-clients-per-gpu (Optional) The max number of containers allowed to share each GPU on the node. This field is used together with gpu-sharing-strategy. |
| `--additional-zones` | ZONE,[ZONE,...] |  | (DEPRECATED) The set of additional zones in which the specified node footprint should be replicated. All zones must be in the same region as the cluster's primary zone. If additional-zones is not specified, all nodes will be in the cluster's primary zone. Note that NUM_NODES nodes will be created in each zone, such that if you specify --num-nodes=4 and choose one additional zone, 8 nodes will be created. Multiple locations can be specified, separated by commas. For example: $ gcloud container clusters create example-cluster \ --zone us-central1-a \ --additional-zones us-central1-b,us-central1-c This flag is deprecated. Use --node-locations=PRIMARY_ZONE,[ZONE,...] instead. |
| `--addons` | one of: HttpLoadBalancing, HorizontalPodAutoscaling, KubernetesDashboard, NetworkPolicy, NodeLocalDNS, ConfigConnector, GcePersistentDiskCsiDriver, GcpFilestoreCsiDriver, BackupRestore, GcsFuseCsiDriver, ParallelstoreCsiDriver, HighScaleCheckpointing, LustreCsiDriver, RayOperator, SlurmOperator, CloudRun |  | Addons (https://cloud.google.com/kubernetes-engine/docs/reference/rest/v1/projects.locations.clusters#Cluster.AddonsConfig) are additional Kubernetes cluster components. Addons specified by this flag will be enabled. The others will be disabled. Default addons: HttpLoadBalancing, HorizontalPodAutoscaling. The Istio addon is deprecated and removed. For more information and migration, see https://cloud.google.com/istio/docs/istio-on-gke/migrate-to-anthos-service-mesh. ADDON must be one of: HttpLoadBalancing, HorizontalPodAutoscaling, KubernetesDashboard, NetworkPolicy, NodeLocalDNS, ConfigConnector, GcePersistentDiskCsiDriver, GcpFilestoreCsiDriver, BackupRestore, GcsFuseCsiDriver, ParallelstoreCsiDriver, HighScaleCheckpointing, LustreCsiDriver, RayOperator, SlurmOperator, CloudRun. |
| `--alpha-cluster-feature-gates` | [FEATURE=true\|false,...] |  | Selectively enable or disable Kubernetes alpha and beta kubernetesfeature gates on alpha GKE cluster. Alpha clusters are not covered by the Kubernetes Engine SLA and should not be used for production workloads. |
| `--anonymous-authentication-config` | one of: ENABLED 'ENABLED' enables anonymous calls |  | Enable or restrict anonymous access to the cluster. When enabled, anonymous users will be authenticated as system:anonymous with the group system:unauthenticated. Limiting access restricts anonymous access to only the health check endpoints /readyz, /livez, and /healthz. ANONYMOUS_AUTHENTICATION_CONFIG must be one of: ENABLED 'ENABLED' enables anonymous calls. LIMITED 'LIMITED' restricts anonymous access to the cluster. Only calls to the health check endpoints are allowed anonymously, all other calls will be rejected. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--auto-monitoring-scope` | one of: ALL, NONE |  | Enables Auto-Monitoring for a specific scope within the cluster. ALL: Enables Auto-Monitoring for all supported workloads within the cluster. NONE: Disables Auto-Monitoring. AUTO_MONITORING_SCOPE must be one of: ALL, NONE. |
| `--autopilot-workload-policies` | WORKLOAD_POLICIES |  | Add Autopilot workload policies to the cluster. Examples: $ gcloud container clusters create example-cluster \ --autopilot-workload-policies=allow-net-admin The only supported workload policy is 'allow-net-admin'. |
| `--autoprovisioning-enable-insecure-kubelet-readonly-port` |  |  | Enables the Kubelet's insecure read only port for Autoprovisioned Node Pools. If not set, the value from nodePoolDefaults.nodeConfigDefaults will be used. To disable the readonly port --no-autoprovisioning-enable-insecure-kubelet-readonly-port. |
| `--autoprovisioning-network-tags` | TAGS,[TAGS,...] |  | Applies the given Compute Engine tags (comma separated) on all nodes in the auto-provisioned node pools of the new Standard cluster or the new Autopilot cluster. Examples: $ gcloud container clusters create example-cluster \ --autoprovisioning-network-tags=tag1,tag2 New nodes in auto-provisioned node pools, including ones created by resize or recreate, will have these tags on the Compute Engine API instance object and can be used in firewall rules. See https://cloud.google.com/sdk/gcloud/reference/compute/firewall-rules/create for examples. |
| `--autoprovisioning-resource-manager-tags` | [KEY=VALUE,...] |  | Applies the specified comma-separated resource manager tags that has the GCE_FIREWALL purpose to all nodes in the new Autopilot cluster or all auto-provisioned nodes in the new Standard cluster. Examples: $ gcloud container clusters create example-cluster \ --autoprovisioning-resource-manager-tags=tagKeys/\ 1234=tagValues/2345 $ gcloud container clusters create example-cluster \ --autoprovisioning-resource-manager-tags=my-project/key1=value1 $ gcloud container clusters create example-cluster \ --autoprovisioning-resource-manager-tags=12345/key1=value1,\ 23456/key2=value2 $ gcloud container clusters create example-cluster \ --autoprovisioning-resource-manager-tags= All nodes in an Autopilot cluster or all auto-provisioned nodes in a Standard cluster, including nodes that are resized or re-created, will have the specified tags on the corresponding Instance object in the Compute Engine API. You can reference these tags in network firewall policy rules. For instructions, see https://cloud.google.com/firewall/docs/use-tags-for-firewalls. |
| `--autoscaling-profile` | AUTOSCALING_PROFILE |  | Set autoscaling behaviour, choices are 'optimize-utilization' and 'balanced'. Default is 'balanced'. |
| `--boot-disk-kms-key` | BOOT_DISK_KMS_KEY |  | The Customer Managed Encryption Key used to encrypt the boot disk attached to each node in the node pool. This should be of the form projects/[KEY_PROJECT_ID]/locations/[LOCATION]/keyRings/[RING_NAME]/cryptoKeys/[KEY_NAME]. For more information about protecting resources with Cloud KMS Keys please see: https://cloud.google.com/compute/docs/disks/customer-managed-encryption |
| `--cloud-run-config` | [load-balancer-type=EXTERNAL,...] |  | Configurations for Cloud Run addon, requires --addons=CloudRun for create and --update-addons=CloudRun=ENABLED for update. load-balancer-type (Optional) Type of load-balancer-type EXTERNAL or INTERNAL. Examples: $ gcloud container clusters create example-cluster \ --cloud-run-config=load-balancer-type=INTERNAL |
| `--cluster-ipv4-cidr` | CLUSTER_IPV4_CIDR |  | The IP address range for the pods in this cluster in CIDR notation (e.g. 10.0.0.0/14). Prior to Kubernetes version 1.7.0 this must be a subset of 10.0.0.0/8; however, starting with version 1.7.0 can be any RFC 1918 IP range. If you omit this option, a range is chosen automatically. The automatically chosen range is randomly selected from 10.0.0.0/8 and will not include IP address ranges allocated to VMs, existing routes, or ranges allocated to other clusters. The automatically chosen range might conflict with reserved IP addresses, dynamic routes, or routes within VPCs that peer with this cluster. You should specify --cluster-ipv4-cidr to prevent conflicts. This field is not applicable in a Shared VPC setup where the IP address range for the pods must be specified with --cluster-secondary-range-name |
| `--cluster-secondary-range-name` | NAME |  | Set the secondary range to be used as the source for pod IPs. Alias ranges will be allocated from this secondary range. NAME must be the name of an existing secondary range in the cluster subnetwork. Cannot be specified unless '--enable-ip-alias' option is also specified. Cannot be used with '--create-subnetwork' option. |
| `--cluster-version` | CLUSTER_VERSION |  | The Kubernetes version to use for the master and nodes. Defaults to server-specified. The default Kubernetes version is available using the following command. $ gcloud container get-server-config |
| `--confidential-node-type` | one of: sev, sev_snp, tdx |  | Enable confidential nodes for the cluster. Enabling Confidential Nodes will create nodes using Confidential VM https://docs.cloud.google.com/compute/docs/about-confidential-vm. CONFIDENTIAL_NODE_TYPE must be one of: sev, sev_snp, tdx. |
| `--containerd-config-from-file` | PATH_TO_FILE |  | Path of the YAML file that contains containerd configuration entries like configuring access to private image registries. For detailed information on the configuration usage, please refer to https://cloud.google.com/kubernetes-engine/docs/how-to/customize-containerd-configuration. Note: Updating the containerd configuration of an existing cluster or node pool requires recreation of the existing nodes, which might cause disruptions in running workloads. Use a full or relative path to a local file containing the value of containerd_config. |
| `--create-subnetwork` | [KEY=VALUE,...] |  | Create a new subnetwork for the cluster. The name and range of the subnetwork can be customized via optional 'name' and 'range' key-value pairs. 'name' specifies the name of the subnetwork to be created. 'range' specifies the IP range for the new subnetwork. This can either be a netmask size (e.g. '/20') or a CIDR range (e.g. '10.0.0.0/20'). If a netmask size is specified, the IP is automatically taken from the free space in the cluster's network. Examples: Create a new subnetwork with a default name and size. $ gcloud container clusters create --create-subnetwork "" Create a new subnetwork named "my-subnet" with netmask of size 21. $ gcloud container clusters create \ --create-subnetwork name=my-subnet,range=/21 Create a new subnetwork with a default name with the primary range of 10.100.0.0/16. $ gcloud container clusters create \ --create-subnetwork range=10.100.0.0/16 Create a new subnetwork with the name "my-subnet" with a default range. $ gcloud container clusters create --create-subnetwork name=my-subnet Cannot be specified unless '--enable-ip-alias' option is also specified. Cannot be used in conjunction with '--subnetwork' option. |
| `--data-cache-count` | DATA_CACHE_COUNT |  | Specifies the number of local SSDs to be utilized for GKE Data Cache in the cluster. |
| `--database-encryption-key` | DATABASE_ENCRYPTION_KEY |  | Enable Database Encryption. Enable database encryption that will be used to encrypt Kubernetes Secrets at the application layer. The key provided should be the resource ID in the format of projects/[KEY_PROJECT_ID]/locations/[LOCATION]/keyRings/[RING_NAME]/cryptoKeys/[KEY_NAME]. For more information, see https://cloud.google.com/kubernetes-engine/docs/how-to/encrypting-secrets. |
| `--default-max-pods-per-node` | DEFAULT_MAX_PODS_PER_NODE |  | The default max number of pods per node for node pools in the cluster. This flag sets the default max-pods-per-node for node pools in the cluster. If --max-pods-per-node is not specified explicitly for a node pool, this flag value will be used. Must be used in conjunction with '--enable-ip-alias'. |
| `--disable-default-snat` |  |  | Disable default source NAT rules applied in cluster nodes. By default, cluster nodes perform source network address translation (SNAT) for packets sent from Pod IP address sources to destination IP addresses that are not in the non-masquerade CIDRs list. For more details about SNAT and IP masquerading, see: https://cloud.google.com/kubernetes-engine/docs/how-to/ip-masquerade-agent#how_ipmasq_works SNAT changes the packet's source IP address to the node's internal IP address. When this flag is set, GKE does not perform SNAT for packets sent to any destination. You must set this flag if the cluster uses privately reused public IPs. The --disable-default-snat flag is only applicable to private GKE clusters, which are inherently VPC-native. Thus, --disable-default-snat requires that you also set --enable-ip-alias and --enable-private-nodes. |
| `--disable-l4-lb-firewall-reconciliation` |  |  | Disable reconciliation on the cluster for L4 Load Balancer VPC firewalls targeting ingress traffic. |
| `--disk-size` | DISK_SIZE |  | Size for node VM boot disks in GB. Defaults to 100GB. |
| `--disk-type` | one of: pd-standard, pd-ssd, pd-balanced, hyperdisk-balanced, hyperdisk-extreme, hyperdisk-throughput |  | Type of the node VM boot disk. For version 1.24 and later, defaults to pd-balanced. For versions earlier than 1.24, defaults to pd-standard. DISK_TYPE must be one of: pd-standard, pd-ssd, pd-balanced, hyperdisk-balanced, hyperdisk-extreme, hyperdisk-throughput. |
| `--enable-authorized-networks-on-private-endpoint` |  |  | Enable enforcement of --master-authorized-networks CIDR ranges for traffic reaching cluster's control plane via private IP. |
| `--enable-auto-ipam` |  |  | Enable the Auto IP Address Management (Auto IPAM) feature for the cluster. |
| `--enable-autorepair` |  |  | Enable node autorepair feature for a cluster's default node pool(s). $ gcloud container clusters create example-cluster \ --enable-autorepair Node autorepair is enabled by default for clusters using COS, COS_CONTAINERD, UBUNTU or UBUNTU_CONTAINERD as a base image, use --no-enable-autorepair to disable. See https://cloud.google.com/kubernetes-engine/docs/how-to/node-auto-repair for more info. |
| `--enable-autoupgrade` |  |  | Sets autoupgrade feature for a cluster's default node pool(s). $ gcloud container clusters create example-cluster \ --enable-autoupgrade See https://cloud.google.com/kubernetes-engine/docs/node-auto-upgrades for more info. Enabled by default, use --no-enable-autoupgrade to disable. |
| `--enable-cilium-clusterwide-network-policy` |  |  | Enable Cilium Clusterwide Network Policies on the cluster. Disabled by default. |
| `--enable-cloud-logging` |  |  | (DEPRECATED) Automatically send logs from the cluster to the Google Cloud Logging API. Legacy Logging and Monitoring is deprecated. Thus, flag --enable-cloud-logging is also deprecated and will be removed in an upcoming release. Please use --logging (optionally with --monitoring). For more details, please read: https://cloud.google.com/kubernetes-engine/docs/concepts/about-logs and https://cloud.google.com/kubernetes-engine/docs/how-to/configure-metrics. |
| `--enable-cloud-monitoring` |  |  | (DEPRECATED) Automatically send metrics from pods in the cluster to the Google Cloud Monitoring API. VM metrics will be collected by Google Compute Engine regardless of this setting. Legacy Logging and Monitoring is deprecated. Thus, flag --enable-cloud-monitoring is also deprecated. Please use --monitoring (optionally with --logging). For more details, please read: https://cloud.google.com/kubernetes-engine/docs/how-to/configure-metrics and https://cloud.google.com/kubernetes-engine/docs/concepts/about-logs. |
| `--enable-cloud-run-alpha` |  |  | Enable Cloud Run alpha features on this cluster. Selecting this option will result in the cluster having all Cloud Run alpha API groups and features turned on. Cloud Run alpha clusters are not covered by the Cloud Run SLA and should not be used for production workloads. |
| `--enable-confidential-nodes` |  |  | Enable confidential nodes for the cluster. Enabling Confidential Nodes will create nodes using Confidential VM https://docs.cloud.google.com/compute/docs/about-confidential-vm. |
| `--enable-confidential-storage` |  |  | Enable confidential storage for the cluster. Enabling Confidential Storage will create boot disk with confidential mode |
| `--enable-cost-allocation` |  |  | Enable the cost management feature. When enabled, you can get informational GKE cost breakdowns by cluster, namespace and label in your billing data exported to BigQuery (https://cloud.google.com/billing/docs/how-to/export-data-bigquery). |
| `--enable-dataplane-v2` |  |  | Enables the new eBPF dataplane for GKE clusters that is required for network security, scalability and visibility features. |
| `--enable-default-compute-class` |  |  | Enable the default compute class to use for the cluster. To disable Default Compute Class in an existing cluster, explicitly set flag --no-enable-default-compute-class. |
| `--enable-dns-access` |  |  | Enable access to the cluster's control plane over DNS-based endpoint. DNS-based control plane access is recommended. |
| `--enable-fleet` |  |  | Set cluster project as the fleet host project. This will register the cluster to the same project. To register the cluster to a fleet in a different project, please use --fleet-project=FLEET_HOST_PROJECT. Example: $ gcloud container clusters create --enable-fleet |
| `--enable-fqdn-network-policy` |  |  | Enable FQDN Network Policies on the cluster. FQDN Network Policies are disabled by default. |
| `--enable-google-cloud-access` |  |  | When you enable Google Cloud Access, any public IP addresses owned by Google Cloud can reach the public control plane endpoint of your cluster. |
| `--enable-gvnic` |  |  | Enable the use of GVNIC for this cluster. Requires re-creation of nodes using either a node-pool upgrade or node-pool creation. |
| `--enable-identity-service` |  |  | Enable Identity Service component on the cluster. When enabled, users can authenticate to Kubernetes cluster with external identity providers. Identity Service is by default disabled when creating a new cluster. To disable Identity Service in an existing cluster, explicitly set flag --no-enable-identity-service. |
| `--enable-image-streaming` |  |  | Specifies whether to enable image streaming on cluster. |
| `--enable-insecure-kubelet-readonly-port` |  |  | Enables the Kubelet's insecure read only port. To disable the readonly port on a cluster or node-pool set the flag to --no-enable-insecure-kubelet-readonly-port. |
| `--enable-intra-node-visibility` |  |  | Enable Intra-node visibility for this cluster. Enabling intra-node visibility makes your intra-node pod-to-pod traffic visible to the networking fabric. With this feature, you can use VPC flow logging or other VPC features for intra-node traffic. Enabling it on an existing cluster causes the cluster master and the cluster nodes to restart, which might cause a disruption. |
| `--enable-ip-access` |  |  | Enable access to the cluster's control plane over private IP and public IP if --enable-private-endpoint is not enabled. |
| `--enable-ip-alias` |  |  | --enable-ip-alias creates a VPC-native cluster. If you set this option, you can optionally specify the IP address ranges to use for Pods and Services. For instructions, see https://cloud.google.com/kubernetes-engine/docs/how-to/alias-ips. --no-enable-ip-alias creates a routes-based cluster. This type of cluster routes traffic between Pods using Google Cloud Routes. This option is not recommended; use the default VPC-native cluster type instead. For instructions, see https://cloud.google.com/kubernetes-engine/docs/how-to/routes-based-cluster Note: For IPv6-only clusters, these flags are a no-op as IP Aliases do not apply, and any specified IP address ranges for Pods and Services will be ignored. You can't specify both --enable-ip-alias and --no-enable-ip-alias. If you omit both --enable-ip-alias and --no-enable-ip-alias, the default is a VPC-native cluster. |
| `--enable-k8s-certs-via-dns` |  |  | Enable K8s client certificates Authentication to the cluster's control plane over DNS-based endpoint. |
| `--enable-k8s-tokens-via-dns` |  |  | Enable K8s Service Account tokens Authentication to the cluster's control plane over DNS-based endpoint. |
| `--enable-kernel-module-signature-enforcement` |  |  | Enforces that kernel modules are signed on all new nodes in the cluster unless explicitly overridden with --no-enable-kernel-module-signature-enforcement when creating the nodepool. Use --no-enable-kernel-module-signature-enforcement to disable. Examples: $ gcloud container clusters create example-cluster \ --enable-kernel-module-signature-enforcement |
| `--enable-kubernetes-alpha` |  |  | Enable Kubernetes alpha features on this cluster. Selecting this option will result in the cluster having all Kubernetes alpha API groups and features turned on. Cluster upgrades (both manual and automatic) will be disabled and the cluster will be automatically deleted after 30 days. Alpha clusters are not covered by the Kubernetes Engine SLA and should not be used for production workloads. |
| `--enable-kubernetes-unstable-apis` | API,[API,...] |  | Enable Kubernetes beta API features on this cluster. Beta APIs are not expected to be production ready and should be avoided in production-grade environments. |
| `--enable-l4-ilb-subsetting` |  |  | Enable Subsetting for L4 ILB services created on this cluster. |
| `--enable-legacy-authorization` |  |  | Enables the legacy ABAC authentication for the cluster. User rights are granted through the use of policies which combine attributes together. For a detailed look at these properties and related formats, see https://kubernetes.io/docs/admin/authorization/abac/. To use RBAC permissions instead, create or update your cluster with the option --no-enable-legacy-authorization. |
| `--enable-legacy-lustre-port` |  |  | Allow the Lustre CSI driver to initialize LNet (the virtual network layer for Lustre kernel module) using port 6988. This flag is required to workaround a port conflict with the gke-metadata-server on GKE nodes. |
| `--enable-managed-prometheus` |  |  | Enables managed collection for Managed Service for Prometheus in the cluster. See https://cloud.google.com/stackdriver/docs/managed-prometheus/setup-managed#enable-mgdcoll-gke for more info. Enabled by default for cluster versions 1.27 or greater, use --no-enable-managed-prometheus to disable. |
| `--enable-master-global-access` |  |  | Use with private clusters to allow access to the master's private endpoint from any Google Cloud region or on-premises environment regardless of the private cluster's region. |
| `--enable-multi-networking` |  |  | Enables multi-networking on the cluster. Multi-networking is disabled by default. |
| `--enable-nested-virtualization` |  |  | Enables the use of nested virtualization on the default initial node pool. Defaults to false. Can only be enabled on UBUNTU_CONTAINERD base image or COS_CONTAINERD base image with version 1.28.4-gke.1083000 and above. |
| `--enable-network-policy` |  |  | Enable network policy enforcement for this cluster. If you are enabling network policy on an existing cluster the network policy addon must first be enabled on the master by using --update-addons=NetworkPolicy=ENABLED flag. |
| `--enable-ray-cluster-logging` |  |  | Enable automatic log processing sidecar for Ray clusters. |
| `--enable-ray-cluster-monitoring` |  |  | Enable automatic metrics collection for Ray clusters. |
| `--enable-service-externalips` |  |  | Enables use of services with externalIPs field. |
| `--enable-shielded-nodes` |  |  | Enable Shielded Nodes for this cluster. Enabling Shielded Nodes will enable a more secure Node credential bootstrapping implementation. Starting with version 1.18, clusters will have Shielded GKE nodes by default. |
| `--enable-stackdriver-kubernetes` |  |  | (DEPRECATED) Enable Cloud Operations for GKE. The --enable-stackdriver-kubernetes flag is deprecated and will be removed in an upcoming release. Please use --logging and --monitoring instead. For more information, please read: https://cloud.google.com/kubernetes-engine/docs/concepts/about-logs and https://cloud.google.com/kubernetes-engine/docs/how-to/configure-metrics. |
| `--fleet-project` | PROJECT_ID_OR_NUMBER |  | _[Enable vertical pod autoscaling for a cluster.]_ Sets fleet host project for the cluster. If specified, the current cluster will be registered as a fleet membership under the fleet host project. Example: $ gcloud container clusters create --fleet-project=my-project |
| `--gateway-api` | one of: disabled Gateway controller will be disabled in the cluster |  | _[Enable vertical pod autoscaling for a cluster.]_ Enables GKE Gateway controller in this cluster. The value of the flag specifies which Open Source Gateway API release channel will be used to define Gateway resources. GATEWAY_API must be one of: disabled Gateway controller will be disabled in the cluster. standard Gateway controller will be enabled in the cluster. Resource definitions from the standard OSS Gateway API release channel will be installed. |
| `--hpa-profile` | HPA_PROFILE |  | _[Enable vertical pod autoscaling for a cluster.]_ Set Horizontal Pod Autoscaler behavior. Accepted values are: none, performance. For more information, see https://cloud.google.com/kubernetes-engine/docs/how-to/horizontal-pod-autoscaling#hpa-profile. |
| `--image-type` | IMAGE_TYPE |  | _[Enable vertical pod autoscaling for a cluster.]_ The image type to use for the cluster. Defaults to server-specified. Image Type specifies the base OS that the nodes in the cluster will run on. If an image type is specified, that will be assigned to the cluster and all future upgrades will use the specified image type. If it is not specified the server will pick the default image type. The default image type and the list of valid image types are available using the following command. $ gcloud container get-server-config |
| `--in-transit-encryption` | one of: inter-node-transparent, none |  | _[Enable vertical pod autoscaling for a cluster.]_ Enable Dataplane V2 in-transit encryption. Dataplane v2 in-transit encryption is disabled by default. IN_TRANSIT_ENCRYPTION must be one of: inter-node-transparent, none. |
| `--ipv6-access-type` | one of: external, internal |  | _[Enable vertical pod autoscaling for a cluster.]_ IPv6 access type of the subnetwork. Defaults to 'external'. IPV6_ACCESS_TYPE must be one of: external, internal. |
| `--issue-client-certificate` |  |  | _[Enable vertical pod autoscaling for a cluster.]_ Issue a TLS client certificate with admin permissions. When enabled, the certificate and private key pair will be present in MasterAuth field of the Cluster object. For cluster versions before 1.12, a client certificate will be issued by default. As of 1.12, client certificates are disabled by default. |
| `--labels` | [KEY=VALUE,...] |  | _[Enable vertical pod autoscaling for a cluster.]_ Labels to apply to the Google Cloud resources in use by the Kubernetes Engine cluster. These are unrelated to Kubernetes labels. Examples: $ gcloud container clusters create example-cluster \ --labels=label_a=value1,label_b=,label_c=value3 |
| `--logging` | [COMPONENT,...] |  | _[Enable vertical pod autoscaling for a cluster.]_ Set the components that have logging enabled. Valid component values are: SYSTEM, WORKLOAD, API_SERVER, CONTROLLER_MANAGER, SCHEDULER, NONE For more information, see https://cloud.google.com/kubernetes-engine/docs/concepts/about-logs#available-logs Examples: $ gcloud container clusters create --logging=SYSTEM $ gcloud container clusters create \ --logging=SYSTEM,API_SERVER,WORKLOAD $ gcloud container clusters create --logging=NONE |
| `--logging-variant` | one of: DEFAULT 'DEFAULT' variant requests minimal resources but may not guarantee high throughput |  | _[Enable vertical pod autoscaling for a cluster.]_ Specifies the logging variant that will be deployed on all the nodes in the cluster. Valid logging variants are MAX_THROUGHPUT, DEFAULT. If no value is specified, DEFAULT is used. LOGGING_VARIANT must be one of: DEFAULT 'DEFAULT' variant requests minimal resources but may not guarantee high throughput. MAX_THROUGHPUT 'MAX_THROUGHPUT' variant requests more node resources and is able to achieve logging throughput up to 10MB per sec. |
| `--machine-type` | MACHINE_TYPE, -m MACHINE_TYPE |  | _[Enable vertical pod autoscaling for a cluster.]_ The type of machine to use for nodes. Defaults to e2-medium. The list of predefined machine types is available using the following command: $ gcloud compute machine-types list You can also specify custom machine types by providing a string with the format "custom-CPUS-RAM" where "CPUS" is the number of virtual CPUs and "RAM" is the amount of RAM in MiB. For example, to create a node pool using custom machines with 2 vCPUs and 12 GB of RAM: $ gcloud container clusters create high-mem-pool \ --machine-type=custom-2-12288 |
| `--max-nodes-per-pool` | MAX_NODES_PER_POOL |  | _[Enable vertical pod autoscaling for a cluster.]_ The maximum number of nodes to allocate per default initial node pool. Kubernetes Engine will automatically create enough nodes pools such that each node pool contains less than --max-nodes-per-pool nodes. Defaults to 1000 nodes, but can be set as low as 100 nodes per pool on initial create. |
| `--max-pods-per-node` | MAX_PODS_PER_NODE |  | _[Enable vertical pod autoscaling for a cluster.]_ The max number of pods per node for this node pool. This flag sets the maximum number of pods that can be run at the same time on a node. This will override the value given with --default-max-pods-per-node flag set at the cluster level. Must be used in conjunction with '--enable-ip-alias'. |
| `--max-surge-upgrade` | MAX_SURGE_UPGRADE | 1 | _[Enable vertical pod autoscaling for a cluster.]_ Number of extra (surge) nodes to be created on each upgrade of a node pool. Specifies the number of extra (surge) nodes to be created during this node pool's upgrades. For example, running the following command will result in creating an extra node each time the node pool is upgraded: $ gcloud container clusters create example-cluster \ --max-surge-upgrade=1 --max-unavailable-upgrade=0 Must be used in conjunction with '--max-unavailable-upgrade'. |
| `--max-unavailable-upgrade` | MAX_UNAVAILABLE_UPGRADE |  | _[Enable vertical pod autoscaling for a cluster.]_ Number of nodes that can be unavailable at the same time on each upgrade of a node pool. Specifies the number of nodes that can be unavailable at the same time while this node pool is being upgraded. For example, running the following command will result in having 3 nodes being upgraded in parallel (1 + 2), but keeping always at least 3 (5 - 2) available each time the node pool is upgraded: $ gcloud container clusters create example-cluster --num-nodes=5 \ --max-surge-upgrade=1 --max-unavailable-upgrade=2 Must be used in conjunction with '--max-surge-upgrade'. |
| `--membership-type` | MEMBERSHIP_TYPE |  | _[Enable vertical pod autoscaling for a cluster.]_ Specify a membership type for the cluster's fleet membership. Example: $ gcloud container clusters create --membership-type=LIGHTWEIGHT. \ MEMBERSHIP_TYPE must be (only one value is supported): LIGHTWEIGHT Fleet membership representing this cluster will be lightweight. |
| `--metadata` | KEY=VALUE,[KEY=VALUE,...] |  | _[Enable vertical pod autoscaling for a cluster.]_ Compute Engine metadata to be made available to the guest operating system running on nodes within the node pool. Each metadata entry is a key/value pair separated by an equals sign. Metadata keys must be unique and less than 128 bytes in length. Values must be less than or equal to 32,768 bytes in length. The total size of all keys and values must be less than 512 KB. Multiple arguments can be passed to this flag. For example: --metadata key-1=value-1,key-2=value-2,key-3=value-3 Additionally, the following keys are reserved for use by Kubernetes Engine: * cluster-location * cluster-name * cluster-uid * configure-sh * enable-os-login * gci-update-strategy * gci-ensure-gke-docker * instance-template * kube-env * startup-script * user-data Google Kubernetes Engine sets the following keys by default: * serial-port-logging-enable See also Compute Engine's documentation (https://cloud.google.com/compute/docs/storing-retrieving-metadata) on storing and retrieving instance metadata. |
| `--metadata-from-file` | KEY=LOCAL_FILE_PATH,[...] |  | _[Enable vertical pod autoscaling for a cluster.]_ Same as --metadata except that the value for the entry will be read from a local file. |
| `--min-cpu-platform` | PLATFORM |  | _[Enable vertical pod autoscaling for a cluster.]_ When specified, the nodes for the new cluster's default node pool will be scheduled on host with specified CPU architecture or a newer one. Examples: $ gcloud container clusters create example-cluster \ --min-cpu-platform=PLATFORM To list available CPU platforms in given zone, run: $ gcloud beta compute zones describe ZONE \ --format="value(availableCpuPlatforms)" CPU platform selection is available only in selected zones. |
| `--monitoring` | [COMPONENT,...] |  | _[Enable vertical pod autoscaling for a cluster.]_ Set the components that have monitoring enabled. Valid component values are: SYSTEM, WORKLOAD (Deprecated), NONE, API_SERVER, CONTROLLER_MANAGER, SCHEDULER, DAEMONSET, DEPLOYMENT, HPA, POD, STATEFULSET, STORAGE, CADVISOR, KUBELET, DCGM, JOBSET For more information, see https://cloud.google.com/kubernetes-engine/docs/how-to/configure-metrics#available-metrics Examples: $ gcloud container clusters create --monitoring=SYSTEM,API_SERVER,POD $ gcloud container clusters create --monitoring=NONE |
| `--network` | NETWORK |  | _[Enable vertical pod autoscaling for a cluster.]_ The Compute Engine Network that the cluster will connect to. Google Kubernetes Engine will use this network when creating routes and firewalls for the clusters. Defaults to the 'default' network. |
| `--network-performance-configs` | [PROPERTY1=VALUE1,...] |  | _[Enable vertical pod autoscaling for a cluster.]_ Configures network performance settings for the cluster. Node pools can override with their own settings. total-egress-bandwidth-tier Total egress bandwidth is the available outbound bandwidth from a VM, regardless of whether the traffic is going to internal IP or external IP destinations. The following tier values are allowed: [TIER_UNSPECIFIED,TIER_1]. See https://cloud.google.com/compute/docs/networking/configure-vm-with-high-bandwidth-configuration for more information. |
| `--node-labels` | [NODE_LABEL,...] |  | _[Enable vertical pod autoscaling for a cluster.]_ Applies the given Kubernetes labels on all nodes in the new node pool. Examples: $ gcloud container clusters create example-cluster \ --node-labels=label-a=value1,label-2=value2 Updating the node pool's --node-labels flag applies the labels to the Kubernetes Node objects for existing nodes in-place; it does not re-create or replace nodes. New nodes, including ones created by resizing or re-creating nodes, will have these labels on the Kubernetes API Node object. The labels can be used in the nodeSelector field. See https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node/ for examples. Note that Kubernetes labels, intended to associate cluster components and resources with one another and manage resource lifecycles, are different from Google Kubernetes Engine labels that are used for the purpose of tracking billing and usage information. |
| `--node-locations` | ZONE,[ZONE,...] |  | _[Enable vertical pod autoscaling for a cluster.]_ The set of zones in which the specified node footprint should be replicated. All zones must be in the same region as the cluster's master(s), specified by the -location, --zone, or --region flag. Additionally, for zonal clusters, --node-locations must contain the cluster's primary zone. If not specified, all nodes will be in the cluster's primary zone (for zonal clusters) or spread across three randomly chosen zones within the cluster's region (for regional clusters). Note that NUM_NODES nodes will be created in each zone, such that if you specify --num-nodes=4 and choose two locations, 8 nodes will be created. Multiple locations can be specified, separated by commas. For example: $ gcloud container clusters create example-cluster \ --location us-central1-a \ --node-locations us-central1-a,us-central1-b |
| `--node-taints` | [NODE_TAINT,...] |  | _[Enable vertical pod autoscaling for a cluster.]_ Applies the given kubernetes taints on all nodes in default node pool(s) in new cluster, which can be used with tolerations for pod scheduling. Examples: $ gcloud container clusters create example-cluster \ --node-taints=key1=val1:NoSchedule,key2=val2:PreferNoSchedule To read more about node-taints, see https://cloud.google.com/kubernetes-engine/docs/node-taints. |
| `--node-version` | NODE_VERSION |  | _[Enable vertical pod autoscaling for a cluster.]_ The Kubernetes version to use for nodes. Defaults to server-specified. The default Kubernetes version is available using the following command. $ gcloud container get-server-config |
| `--notification-config` | [pubsub=ENABLED\|DISABLED,pubsub-topic=TOPIC,...] |  | _[Enable vertical pod autoscaling for a cluster.]_ The notification configuration of the cluster. GKE supports publishing cluster upgrade notifications to any Pub/Sub topic you created in the same project. Create a subscription for the topic specified to receive notification messages. See https://cloud.google.com/pubsub/docs/admin on how to manage Pub/Sub topics and subscriptions. You can also use the filter option to specify which event types you'd like to receive from the following options: SecurityBulletinEvent, UpgradeEvent, UpgradeInfoEvent, UpgradeAvailableEvent. Examples: $ gcloud container clusters create example-cluster \ --notification-config=pubsub=ENABLED,pubsub-topic=projects/\ {project}/topics/{topic-name} $ gcloud container clusters create example-cluster \ --notification-config=pubsub=ENABLED,pubsub-topic=projects/\ {project}/topics/{topic-name},\ filter="SecurityBulletinEvent\|UpgradeEvent" The project of the Pub/Sub topic must be the same one as the cluster. It can be either the project ID or the project number. |
| `--num-nodes` | NUM_NODES | 3 | _[Enable vertical pod autoscaling for a cluster.]_ The number of nodes to be created in each of the cluster's zones. |
| `--patch-update` | one of: accelerated, default |  | _[Enable vertical pod autoscaling for a cluster.]_ The patch update to use for the cluster. Setting to 'accelerated' automatically upgrades the cluster to the latest patch available within the cluster's current minor version and release channel. Setting to 'default' automatically upgrades the cluster to the default patch upgrade targetversion available within the cluster's current minor version and release channel. PATCH_UPDATE must be one of: accelerated, default. |
| `--performance-monitoring-unit` | one of: architectural Enables architectural PMU events tied to non last level cache (LLC) events |  | _[Enable vertical pod autoscaling for a cluster.]_ Sets the Performance Monitoring Unit level. Valid values are architectural, standard and enhanced. PERFORMANCE_MONITORING_UNIT must be one of: architectural Enables architectural PMU events tied to non last level cache (LLC) events. enhanced Enables most documented core/L2 and LLC PMU events. standard Enables most documented core/L2 PMU events. |
| `--placement-policy` | PLACEMENT_POLICY |  | _[Enable vertical pod autoscaling for a cluster.]_ Indicates the desired resource policy to use. $ gcloud container clusters create node-pool-1 \ --cluster=example-cluster --placement-policy my-placement |
| `--placement-type` | one of: UNSPECIFIED, COMPACT |  | _[Enable vertical pod autoscaling for a cluster.]_ Placement type allows to define the type of node placement within the default node pool of this cluster. UNSPECIFIED - No requirements on the placement of nodes. This is the default option. COMPACT - GKE will attempt to place the nodes in a close proximity to each other. This helps to reduce the communication latency between the nodes, but imposes additional limitations on the node pool size. $ gcloud container clusters create example-cluster \ --placement-type=COMPACT PLACEMENT_TYPE must be one of: UNSPECIFIED, COMPACT. |
| `--preemptible` |  |  | _[Enable vertical pod autoscaling for a cluster.]_ Create nodes using preemptible VM instances in the new cluster. $ gcloud container clusters create example-cluster --preemptible New nodes, including ones created by resize or recreate, will use preemptible VM instances. See https://cloud.google.com/kubernetes-engine/docs/preemptible-vm for more information on how to use Preemptible VMs with Kubernetes Engine. |
| `--private-endpoint-subnetwork` | NAME |  | _[Enable vertical pod autoscaling for a cluster.]_ Sets the subnetwork GKE uses to provision the control plane's private endpoint. |
| `--private-ipv6-google-access-type` | one of: bidirectional Allows Google services to initiate connections to GKE pods in this cluster |  | _[Enable vertical pod autoscaling for a cluster.]_ Sets the type of private access to Google services over IPv6. PRIVATE_IPV6_GOOGLE_ACCESS_TYPE must be one of: bidirectional Allows Google services to initiate connections to GKE pods in this cluster. This is not intended for common use, and requires previous integration with Google services. disabled Default value. Disables private access to Google services over IPv6. outbound-only Allows GKE pods to make fast, secure requests to Google services over IPv6. This is the most common use of private IPv6 access. $ gcloud alpha container clusters create \ --private-ipv6-google-access-type=disabled $ gcloud alpha container clusters create \ --private-ipv6-google-access-type=outbound-only $ gcloud alpha container clusters create \ --private-ipv6-google-access-type=bidirectional PRIVATE_IPV6_GOOGLE_ACCESS_TYPE must be one of: bidirectional, disabled, outbound-only. |
| `--release-channel` | one of: None Use 'None' to opt-out of any release channel |  | _[Enable vertical pod autoscaling for a cluster.]_ Release channel a cluster is subscribed to. If left unspecified and a version is specified, the cluster is enrolled in the most mature release channel where the version is available (first checking STABLE, then REGULAR, and finally RAPID). Otherwise, if no release channel and no version is specified, the cluster is enrolled in the REGULAR channel with its default version. When a cluster is subscribed to a release channel, Google maintains both the master version and the node version. Node auto-upgrade is enabled by default for release channel clusters and can be controlled via upgrade-scope exclusions (https://cloud.google.com/kubernetes-engine/docs/concepts/maintenance-windows-and-exclusions#scope_of_maintenance_to_exclude). CHANNEL must be one of: None Use 'None' to opt-out of any release channel. extended Clusters subscribed to 'extended' can remain on a minor version for 24 months from when the minor version is made available in the Regular channel. rapid 'rapid' channel is offered on an early access basis for customers who want to test new releases. WARNING: Versions available in the 'rapid' channel may be subject to unresolved issues with no known workaround and are not subject to any SLAs. regular Clusters subscribed to 'regular' receive versions that are considered GA quality. 'regular' is intended for production users who want to take advantage of new features. stable Clusters subscribed to 'stable' receive versions that are known to be stable and reliable in production. |
| `--resource-manager-tags` | [KEY=VALUE,...] |  | _[Enable vertical pod autoscaling for a cluster.]_ Applies the specified comma-separated resource manager tags that has the GCE_FIREWALL purpose to all nodes in the new default node pool(s) of a new cluster. Examples: $ gcloud container clusters create example-cluster \ --resource-manager-tags=tagKeys/1234=tagValues/2345 $ gcloud container clusters create example-cluster \ --resource-manager-tags=my-project/key1=value1 $ gcloud container clusters create example-cluster \ --resource-manager-tags=12345/key1=value1,23456/key2=value2 $ gcloud container clusters create example-cluster \ --resource-manager-tags= All nodes, including nodes that are resized or re-created, will have the specified tags on the corresponding Instance object in the Compute Engine API. You can reference these tags in network firewall policy rules. For instructions, see https://cloud.google.com/firewall/docs/use-tags-for-firewalls. |
| `--security-group` | SECURITY_GROUP |  | _[Enable vertical pod autoscaling for a cluster.]_ The name of the RBAC security group for use with Google security groups in Kubernetes RBAC (https://kubernetes.io/docs/reference/access-authn-authz/rbac/). To include group membership as part of the claims issued by Google during authentication, a group must be designated as a security group by including it as a direct member of this group. If unspecified, no groups will be returned for use with RBAC. |
| `--security-posture` | one of: disabled, standard, enterprise |  | _[Enable vertical pod autoscaling for a cluster.]_ Sets the mode of the Kubernetes security posture API's off-cluster features. To enable advanced mode explicitly set the flag to --security-posture=enterprise. To enable in standard mode explicitly set the flag to --security-posture=standard To disable in an existing cluster, explicitly set the flag to --security-posture=disabled. For more information on enablement, see https://cloud.google.com/kubernetes-engine/docs/concepts/about-security-posture-dashboard#feature-enablement. SECURITY_POSTURE must be one of: disabled, standard, enterprise. |
| `--services-ipv4-cidr` | CIDR |  | _[Enable vertical pod autoscaling for a cluster.]_ Set the IP range for the services IPs. Can be specified as a netmask size (e.g. '/20') or as in CIDR notion (e.g. '10.100.0.0/20'). If given as a netmask size, the IP range will be chosen automatically from the available space in the network. If unspecified, the services CIDR range will be chosen with a default mask size. Cannot be specified unless '--enable-ip-alias' option is also specified. |
| `--services-secondary-range-name` | NAME |  | _[Enable vertical pod autoscaling for a cluster.]_ Set the secondary range to be used for services (e.g. ClusterIPs). NAME must be the name of an existing secondary range in the cluster subnetwork. Cannot be specified unless '--enable-ip-alias' option is also specified. Cannot be used with '--create-subnetwork' option. |
| `--shielded-integrity-monitoring` |  |  | _[Enable vertical pod autoscaling for a cluster.]_ Enables monitoring and attestation of the boot integrity of the instance. The attestation is performed against the integrity policy baseline. This baseline is initially derived from the implicitly trusted boot image when the instance is created. |
| `--shielded-secure-boot` |  |  | _[Enable vertical pod autoscaling for a cluster.]_ The instance will boot with secure boot enabled. |
| `--spot` |  |  | _[Enable vertical pod autoscaling for a cluster.]_ Create nodes using spot VM instances in the new cluster. $ gcloud container clusters create example-cluster --spot New nodes, including ones created by resize or recreate, will use spot VM instances. |
| `--stack-type` | one of: ipv4, ipv4-ipv6 |  | _[Enable vertical pod autoscaling for a cluster.]_ IP stack type of the cluster nodes. STACK_TYPE must be one of: ipv4, ipv4-ipv6. |
| `--storage-pools` | STORAGE_POOL,[...] |  | _[Enable vertical pod autoscaling for a cluster.]_ A list of storage pools where the cluster's boot disks will be provisioned. STORAGE_POOL must be in the format projects/project/zones/zone/storagePools/storagePool |
| `--subnetwork` | SUBNETWORK |  | _[Enable vertical pod autoscaling for a cluster.]_ The Google Compute Engine subnetwork (https://cloud.google.com/compute/docs/subnetworks) to which the cluster is connected. The subnetwork must belong to the network specified by --network. Cannot be used with the "--create-subnetwork" option. |
| `--system-config-from-file` | PATH_TO_FILE |  | _[Enable vertical pod autoscaling for a cluster.]_ Path of the YAML/JSON file that contains the node configuration, including Linux kernel parameters (sysctls) and kubelet configs. Examples: kubeletConfig: cpuManagerPolicy: static memoryManager: policy: Static topologyManager: policy: BestEffort scope: pod linuxConfig: sysctl: net.core.somaxconn: '2048' net.ipv4.tcp_rmem: '4096 87380 6291456' hugepageConfig: hugepage_size2m: '1024' hugepage_size1g: '2' swapConfig: enabled: true bootDiskProfile: swapSizeGib: 8 cgroupMode: 'CGROUP_MODE_V2' List of supported kubelet configs in 'kubeletConfig'. KEY VALUE cpuManagerPolicy either 'static' or 'none' cpuCFSQuota true or false (enabled by default) cpuCFSQuotaPeriod interval (e.g., '100ms'. The value must be between 1ms and 1 second, inclusive.) memoryManager specify memory manager policy topologyManager specify topology manager policy and scope podPidsLimit integer (The value must be greater than or equal to 1024 and less than 4194304.) containerLogMaxSize positive number plus unit suffix (e.g., '100Mi', '0.2Gi'. The value must be between 10Mi and 500Mi, inclusive.) containerLogMaxFiles integer (The value must be between [2, 10].) imageGcLowThresholdPercent integer (The value must be between [10, 85], and lower than imageGcHighThresholdPercent.) imageGcHighThresholdPercent integer (The value must be between [10, 85], and greater than imageGcLowThresholdPercent.) imageMinimumGcAge interval (e.g., '100s', '1m'. The value must be less than '2m'.) imageMaximumGcAge interval (e.g., '100s', '1m'. The value must be greater than imageMinimumGcAge.) evictionSoft specify eviction soft thresholds evictionSoftGracePeriod specify eviction soft grace period evictionMinimumReclaim specify eviction minimum reclaim thresholds evictionMaxPodGracePeriodSeconds integer (Max grace period for pod termination during eviction, in seconds. The value must be between [0, 300].) allowedUnsafeSysctls list of sysctls (Allowlisted groups: 'kernel.shm*', 'kernel.msg*', 'kernel.sem', 'fs.mqueue.*', and 'net.*', and sysctls under the groups.) singleProcessOomKill true or false maxParallelImagePulls integer (The value must be between [2, 5].) List of supported keys in memoryManager in 'kubeletConfig'. KEY VALUE policy either 'Static' or 'None' List of supported keys in topologyManager in 'kubeletConfig'. KEY VALUE policy either 'none' or 'best-effort' or 'single-numa-node' or 'restricted' scope either 'pod' or 'container' List of supported keys in evictionSoft in 'kubeletConfig'. KEY VALUE memoryAvailable quantity (e.g., '100Mi', '1Gi'. Represents the amount of memory available before soft eviction. The value must be at least 100Mi and less than 50% of the node's memory.) nodefsAvailable percentage (e.g., '20%'. Represents the nodefs available before soft eviction. The value must be between 10% and 50%, inclusive.) nodefsInodesFree percentage (e.g., '20%'. Represents the nodefs inodes free before soft eviction. The value must be between 5% and 50%, inclusive.) imagefsAvailable percentage (e.g., '20%'. Represents the imagefs available before soft eviction. The value must be between 15% and 50%, inclusive.) imagefsInodesFree percentage (e.g., '20%'. Represents the imagefs inodes free before soft eviction. The value must be between 5% and 50%, inclusive.) pidAvailable percentage (e.g., '20%'. Represents the pid available before soft eviction. The value must be between 10% and 50%, inclusive.) List of supported keys in evictionSoftGracePeriod in 'kubeletConfig'. KEY VALUE memoryAvailable duration (e.g., '30s', '1m'. The grace period for soft eviction for this resource. The value must be positive and no more than '5m'.) nodefsAvailable duration (e.g., '30s', '1m'. The grace period for soft eviction for this resource. The value must be positive and no more than '5m'.) nodefsInodesFree duration (e.g., '30s', '1m'. The grace period for soft eviction for this resource. The value must be positive and no more than '5m'.) imagefsAvailable duration (e.g., '30s', '1m'. The grace period for soft eviction for this resource. The value must be positive and no more than '5m'.) imagefsInodesFree duration (e.g., '30s', '1m'. The grace period for soft eviction for this resource. The value must be positive and no more than '5m'.) pidAvailable duration (e.g., '30s', '1m'. The grace period for soft eviction for this resource. The value must be positive and no more than '5m'.) List of supported keys in evictionMinimumReclaim in 'kubeletConfig'. KEY VALUE memoryAvailable percentage (e.g., '5%'. Represents the minimum reclaim threshold for memory available. The value must be positive and no more than 10%.) nodefsAvailable percentage (e.g., '5%'. Represents the minimum reclaim threshold for nodefs available. The value must be positive and no more than 10%.) nodefsInodesFree percentage (e.g., '5%'. Represents the minimum reclaim threshold for nodefs inodes free. The value must be positive and no more than 10%.) imagefsAvailable percentage (e.g., '5%'. Represents the minimum reclaim threshold for imagefs available. The value must be positive and no more than 10%.) imagefsInodesFree percentage (e.g., '5%'. Represents the minimum reclaim threshold for imagefs inodes free. The value must be positive and no more than 10%.) pidAvailable percentage (e.g., '5%'. Represents the minimum reclaim threshold for pid available. The value must be positive and no more than 10%.) List of supported sysctls in 'linuxConfig'. KEY VALUE net.core.netdev_max_backlog Any positive integer, less than 2147483647 net.core.rmem_default Must be between [2304, 2147483647] net.core.rmem_max Must be between [2304, 2147483647] net.core.wmem_default Must be between [4608, 2147483647] net.core.wmem_max Must be between [4608, 2147483647] net.core.optmem_max Any positive integer, less than 2147483647 net.core.somaxconn Must be between [128, 2147483647] net.ipv4.tcp_rmem Any positive integer tuple net.ipv4.tcp_wmem Any positive integer tuple net.ipv4.tcp_tw_reuse Must be {0, 1, 2} net.ipv4.tcp_mtu_probing Must be {0, 1, 2} net.ipv4.tcp_max_orphans Must be between [16384, 262144] net.ipv4.tcp_max_tw_buckets Must be between [4096, 2147483647] net.ipv4.tcp_syn_retries Must be between [1, 127] net.ipv4.tcp_ecn Must be {0, 1, 2} net.ipv4.tcp_congestion_control Supported values for COS: 'reno', 'cubic', 'bbr', 'lp', 'htcp'. Supported values for Ubuntu: 'reno', 'cubic', 'bbr', 'lp', 'htcp', 'vegas', 'dctcp', 'bic', 'cdg', 'highspeed', 'hybla', 'illinois', 'nv', 'scalable', 'veno', 'westwood', 'yeah'. net.netfilter.nf_conntrack_max Must be between [65536, 4194304] net.netfilter.nf_conntrack_buckets Must be between [65536, 524288]. Recommend setting: nf_conntrack_max = nf_conntrack_bucke ts * 4 net.netfilter.nf_conntrack_tcp_timeout_close_wait Must be between [60, 3600] net.netfilter.nf_conntrack_tcp_timeout_time_wait Must be between [1, 600] net.netfilter.nf_conntrack_tcp_timeout_established Must be between [600, 86400] net.netfilter.nf_conntrack_acct Must be {0, 1} kernel.shmmni Must be between [4096, 32768] kernel.shmmax Must be between [0, 184467440736927743 99] kernel.shmall Must be between [0, 184467440736927743 99] kernel.perf_event_paranoid Must be {-1, 0, 1, 2, 3} kernel.sched_rt_runtime_us Must be [-1, 1000000] kernel.softlockup_panic Must be {0, 1} kernel.yama.ptrace_scope Must be {0, 1, 2, 3} kernel.kptr_restrict Must be {0, 1, 2} kernel.dmesg_restrict Must be {0, 1} kernel.sysrq Must be [0, 511] fs.aio-max-nr Must be between [65536, 4194304] fs.file-max Must be between [104857, 67108864] fs.inotify.max_user_instances Must be between [8192, 1048576] fs.inotify.max_user_watches Must be between [8192, 1048576] fs.nr_open Must be between [1048576, 2147483584] vm.dirty_background_ratio Must be between [1, 100] vm.dirty_background_bytes Must be between [0, 68719476736] vm.dirty_expire_centisecs Must be between [0, 6000] vm.dirty_ratio Must be between [1, 100] vm.dirty_bytes Must be between [0, 68719476736] vm.dirty_writeback_centisecs Must be between [0, 1000] vm.max_map_count Must be between [65536, 2147483647] vm.overcommit_memory Must be one of {0, 1, 2}. Not supported on machines with less than 15 GB memory. vm.overcommit_ratio Must be between [0, 100] vm.vfs_cache_pressure Must be between [0, 100] vm.swappiness Must be between [0, 200] vm.watermark_scale_factor Must be between [10, 3000] vm.min_free_kbytes Must be between [67584, 1048576] List of supported hugepage size in 'hugepageConfig'. KEY VALUE hugepage_size2m Number of 2M huge pages, any positive integer hugepage_size1g Number of 1G huge pages, any positive integer List of supported keys in 'swapConfig' under 'linuxConfig'. KEY VALUE enabled boolean encryptionConfig specify encryption settings for the swap space bootDiskProfile specify swap on the node's boot disk ephemeralLocalSsdProfile specify swap on the local SSD shared with pod ephemeral storage dedicatedLocalSsdProfile specify swap on a new, separate local NVMe SSD exclusively for swap List of supported keys in 'encryptionConfig' under 'swapConfig'. KEY VALUE disabled boolean List of supported keys in 'bootDiskProfile' under 'swapConfig'. KEY VALUE swapSizeGib integer swapSizePercent integer List of supported keys in 'ephemeralLocalSsdProfile' under 'swapConfig'. KEY VALUE swapSizeGib integer swapSizePercent integer List of supported keys in 'dedicatedLocalSsdProfile' under 'swapConfig'. KEY VALUE diskCount integer The upper limit for total allocated hugepage size differs based upon machine size. * On machines with less than 30 GB memory: 60% of the total memory. For example, on e2-standard-2 machine with 8 GB of memory, you can't allocate more than 4.8 GB for hugepages. * On machines with more than 30 GB memory: 80% of the total memory. For example, on c4a-standard-8 machines with 32 GB of memory, hugepages cannot exceed 25.6 GB. 1G hugepages are only available in following machine familes: c3, m2, c2d, c3d, h3, m3, a2, a3, g2. Supported values for 'cgroupMode' under 'linuxConfig'. * CGROUP_MODE_V1: Use cgroupv1 on the node pool. * CGROUP_MODE_V2: Use cgroupv2 on the node pool. * CGROUP_MODE_UNSPECIFIED: Use the default GKE cgroup configuration. Supported values for 'transparentHugepageEnabled' under 'linuxConfig' which controls transparent hugepage support for anonymous memory. * TRANSPARENT_HUGEPAGE_ENABLED_ALWAYS: Transparent hugepage is enabled system wide. * TRANSPARENT_HUGEPAGE_ENABLED_MADVISE: Transparent hugepage is enabled inside MADV_HUGEPAGE regions. This is the default kernel configuration. * TRANSPARENT_HUGEPAGE_ENABLED_NEVER: Transparent hugepage is disabled. * TRANSPARENT_HUGEPAGE_ENABLED_UNSPECIFIED: Default value. GKE will not modify the kernel configuration. Supported values for 'transparentHugepageDefrag' under 'linuxConfig' which defines the transparent hugepage defrag configuration on the node. * TRANSPARENT_HUGEPAGE_DEFRAG_ALWAYS: It means that an application requesting THP will stall on allocation failure and directly reclaim pages and compact memory in an effort to allocate a THP immediately. * TRANSPARENT_HUGEPAGE_DEFRAG_DEFER: It means that an application will wake kswapd in the background to reclaim pages and wake kcompactd to compact memory so that THP is available in the near future. It is the responsibility of khugepaged to then install the THP pages later. * TRANSPARENT_HUGEPAGE_DEFRAG_DEFER_WITH_MADVISE: It means that an application will enter direct reclaim and compaction like always, but only for regions that have used madvise(MADV_HUGEPAGE); all other regions will wake kswapd in the background to reclaim pages and wake kcompactd to compact memory so that THP is available in the near future. * TRANSPARENT_HUGEPAGE_DEFRAG_MADVISE: It means that an application will enter direct reclaim and compaction like always, but only for regions that have used madvise(MADV_HUGEPAGE); all other regions will wake kswapd in the background to reclaim pages and wake kcompactd to compact memory so that THP is available in the near future. * TRANSPARENT_HUGEPAGE_DEFRAG_NEVER: It means that an application will never enter direct reclaim or compaction. * TRANSPARENT_HUGEPAGE_DEFRAG_UNSPECIFIED: Default value. GKE will not modify the kernel configuration. Note, updating the system configuration of an existing node pool requires recreation of the nodes which which might cause a disruption. Use a full or relative path to a local file containing the value of system_config. |
| `--tags` | TAG,[TAG,...] |  | _[Enable vertical pod autoscaling for a cluster.]_ Applies the given Compute Engine tags (comma separated) on all nodes in the new node-pool. Examples: $ gcloud container clusters create example-cluster --tags=tag1,tag2 New nodes, including ones created by resize or recreate, will have these tags on the Compute Engine API instance object and can be used in firewall rules. See https://cloud.google.com/sdk/gcloud/reference/compute/firewall-rules/create for examples. |
| `--threads-per-core` | THREADS_PER_CORE |  | _[Enable vertical pod autoscaling for a cluster.]_ The number of visible threads per physical core for each node. To disable simultaneous multithreading (SMT) set this to 1. |
| `--tier` | one of: standard, enterprise |  | _[Enable vertical pod autoscaling for a cluster.]_ (DEPRECATED) Set the desired tier for the cluster. The --tier flag is deprecated. More info: https://cloud.google.com/kubernetes-engine/docs/release-notes#September_02_2025. TIER must be one of: standard, enterprise. |
| `--workload-metadata` | one of: GCE_METADATA Pods running in this node pool have access to the node's underlying Compute Engine Metadata Server |  | _[Enable vertical pod autoscaling for a cluster.]_ Type of metadata server available to pods running in the node pool. WORKLOAD_METADATA must be one of: GCE_METADATA Pods running in this node pool have access to the node's underlying Compute Engine Metadata Server. GKE_METADATA Run the Kubernetes Engine Metadata Server on this node. The Kubernetes Engine Metadata Server exposes a metadata API to workloads that is compatible with the V1 Compute Metadata APIs exposed by the Compute Engine and App Engine Metadata Servers. This feature can only be enabled if Workload Identity is enabled at the cluster level. |
| `--workload-pool` | WORKLOAD_POOL |  | _[Enable vertical pod autoscaling for a cluster.]_ Enable Workload Identity on the cluster. When enabled, Kubernetes service accounts will be able to act as Cloud IAM Service Accounts, through the provided workload pool. Currently, the only accepted workload pool is the workload pool of the Cloud project containing the cluster, PROJECT_ID.svc.id.goog. For more information on Workload Identity, see https://cloud.google.com/kubernetes-engine/docs/how-to/workload-identity |
| `--workload-vulnerability-scanning` | one of: disabled, standard, enterprise |  | _[Enable vertical pod autoscaling for a cluster.]_ Sets the mode of the Kubernetes security posture API's workload vulnerability scanning. To enable Advanced vulnerability insights mode explicitly set the flag to --workload-vulnerability-scanning=enterprise. To enable in standard mode explicitly set the flag to --workload-vulnerability-scanning=standard. To disable in an existing cluster, explicitly set the flag to --workload-vulnerability-scanning=disabled. For more information on enablement, see https://cloud.google.com/kubernetes-engine/docs/concepts/about-security-posture-dashboard#feature-enablement. WORKLOAD_VULNERABILITY_SCANNING must be one of: disabled, standard, enterprise. |
| `--enable-insecure-binding-system-authenticated` |  |  | _[unless --enable-autoscaling is also specified.]_ Allow using system:authenticated as a subject in ClusterRoleBindings and RoleBindings. Allowing bindings that reference system:authenticated is a security risk and is not recommended. To disallow binding system:authenticated in a cluster, explicitly set the --no-enable-insecure-binding-system-authenticated flag instead. |
| `--enable-insecure-binding-system-unauthenticated` |  |  | _[unless --enable-autoscaling is also specified.]_ Allow using system:unauthenticated and system:anonymous as subjects in ClusterRoleBindings and RoleBindings. Allowing bindings that reference system:unauthenticated and system:anonymous are a security risk and is not recommended. To disallow binding system:authenticated in a cluster, explicitly set the --no-enable-insecure-binding-system-unauthenticated flag instead. |


**Examples:**
```bash
To create a cluster with the default configuration, run:

    $ gcloud container clusters create sample-cluster
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/clusters/create)

---
### `gcloud container clusters create-auto`

Create an Autopilot cluster for running containers

Create an Autopilot cluster for running containers.

**Synopsis:**
```
gcloud container clusters create-auto NAME
    [--anonymous-authentication-config=ANONYMOUS_AUTHENTICATION_CONFIG]
    [--async] [--auto-monitoring-scope=AUTO_MONITORING_SCOPE]
    [--autoprovisioning-enable-insecure-kubelet-readonly-port]
    [--autoprovisioning-network-tags=TAGS,[TAGS,...]]
    [--autoprovisioning-resource-manager-tags=[KEY=VALUE,...]]
    [--binauthz-evaluation-mode=BINAUTHZ_EVALUATION_MODE]
    [--boot-disk-kms-key=BOOT_DISK_KMS_KEY]
    [--cluster-ipv4-cidr=CLUSTER_IPV4_CIDR]
    [--cluster-secondary-range-name=NAME]
    [--cluster-version=CLUSTER_VERSION]
    [--containerd-config-from-file=PATH_TO_FILE]
    [--create-subnetwork=[KEY=VALUE,...]]
    [--database-encryption-key=DATABASE_ENCRYPTION_KEY]
    [--disable-l4-lb-firewall-reconciliation]
    [--enable-authorized-networks-on-private-endpoint] [--enable-auto-ipam]
    [--enable-backup-restore] [--enable-cilium-clusterwide-network-policy]
    [--enable-confidential-nodes] [--enable-default-compute-class]
    [--enable-dns-access] [--enable-fleet] [--enable-google-cloud-access]
    [--enable-ip-access] [--enable-k8s-certs-via-dns]
    [--enable-k8s-tokens-via-dns]
    [--enable-kernel-module-signature-enforcement]
    [--enable-kubernetes-unstable-apis=API,[API,...]]
    [--enable-legacy-lustre-port] [--enable-lustre-csi-driver]
    [--enable-master-global-access] [--enable-multi-networking]
    [--enable-ray-cluster-logging] [--enable-ray-cluster-monitoring]
    [--enable-ray-operator] [--fleet-project=PROJECT_ID_OR_NUMBER]
    [--hpa-profile=HPA_PROFILE] [--labels=[KEY=VALUE,...]]
    [--logging=[COMPONENT,...]] [--membership-type=MEMBERSHIP_TYPE]
    [--monitoring=[COMPONENT,...]] [--network=NETWORK]
    [--private-endpoint-subnetwork=NAME] [--release-channel=CHANNEL]
    [--security-group=SECURITY_GROUP] [--security-posture=SECURITY_POSTURE]
    [--services-ipv4-cidr=CIDR] [--services-secondary-range-name=NAME]
    [--subnetwork=SUBNETWORK] [--tier=TIER]
    [--workload-policies=WORKLOAD_POLICIES]
    [--workload-vulnerability-scanning=WORKLOAD_VULNERABILITY_SCANNING]
    [--additive-vpc-scope-dns-domain=ADDITIVE_VPC_SCOPE_DNS_DOMAIN
      | --disable-additive-vpc-scope]
    [--aggregation-ca=CA_POOL_PATH --cluster-ca=CA_POOL_PATH
      --control-plane-disk-encryption-key=KEY --etcd-api-ca=CA_POOL_PATH
      --etcd-peer-ca=CA_POOL_PATH --gkeops-etcd-backup-encryption-key=KEY
      --service-account-signing-keys=KEY_VERSION,[KEY_VERSION,...]
      --service-account-verification-keys=KEY_VERSION,[KEY_VERSION,...]]
    [--dataplane-v2-observability-mode=DATAPLANE_V2_OBSERVABILITY_MODE
      | --disable-dataplane-v2-flow-observability
      | --enable-dataplane-v2-flow-observability]
    [--enable-insecure-binding-system-authenticated
      --enable-insecure-binding-system-unauthenticated]
    [--enable-master-authorized-networks
      --master-authorized-networks=NETWORK,[NETWORK,...]]
    [--enable-private-endpoint
      --enable-private-nodes --master-ipv4-cidr=MASTER_IPV4_CIDR]
    [--enable-secret-manager --enable-secret-manager-rotation
      --secret-manager-rotation-interval=SECRET_MANAGER_ROTATION_INTERVAL]
    [--location=LOCATION | --region=REGION | --zone=ZONE, -z ZONE]
    [--scopes=[SCOPE,...];
      default="gke-default" --service-account=SERVICE_ACCOUNT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of the cluster to create.

   The name may contain only lowercase alphanumerics and '-', must start
   with a letter and end with an alphanumeric, and must be no longer than
   40 characters.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--anonymous-authentication-config` | one of: ENABLED 'ENABLED' enables anonymous calls |  | Enable or restrict anonymous access to the cluster. When enabled, anonymous users will be authenticated as system:anonymous with the group system:unauthenticated. Limiting access restricts anonymous access to only the health check endpoints /readyz, /livez, and /healthz. ANONYMOUS_AUTHENTICATION_CONFIG must be one of: ENABLED 'ENABLED' enables anonymous calls. LIMITED 'LIMITED' restricts anonymous access to the cluster. Only calls to the health check endpoints are allowed anonymously, all other calls will be rejected. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--auto-monitoring-scope` | one of: ALL, NONE |  | Enables Auto-Monitoring for a specific scope within the cluster. ALL: Enables Auto-Monitoring for all supported workloads within the cluster. NONE: Disables Auto-Monitoring. AUTO_MONITORING_SCOPE must be one of: ALL, NONE. |
| `--autoprovisioning-enable-insecure-kubelet-readonly-port` |  |  | Enables the Kubelet's insecure read only port for Autoprovisioned Node Pools. If not set, the value from nodePoolDefaults.nodeConfigDefaults will be used. To disable the readonly port --no-autoprovisioning-enable-insecure-kubelet-readonly-port. |
| `--autoprovisioning-network-tags` | TAGS,[TAGS,...] |  | Applies the given Compute Engine tags (comma separated) on all nodes in the auto-provisioned node pools of the new Standard cluster or the new Autopilot cluster. Examples: $ gcloud container clusters create-auto example-cluster \ --autoprovisioning-network-tags=tag1,tag2 New nodes in auto-provisioned node pools, including ones created by resize or recreate, will have these tags on the Compute Engine API instance object and can be used in firewall rules. See https://cloud.google.com/sdk/gcloud/reference/compute/firewall-rules/create for examples. |
| `--autoprovisioning-resource-manager-tags` | [KEY=VALUE,...] |  | Applies the specified comma-separated resource manager tags that has the GCE_FIREWALL purpose to all nodes in the new Autopilot cluster or all auto-provisioned nodes in the new Standard cluster. Examples: $ gcloud container clusters create-auto example-cluster \ --autoprovisioning-resource-manager-tags=tagKeys/\ 1234=tagValues/2345 $ gcloud container clusters create-auto example-cluster \ --autoprovisioning-resource-manager-tags=my-project/key1=value1 $ gcloud container clusters create-auto example-cluster \ --autoprovisioning-resource-manager-tags=12345/key1=value1,\ 23456/key2=value2 $ gcloud container clusters create-auto example-cluster \ --autoprovisioning-resource-manager-tags= All nodes in an Autopilot cluster or all auto-provisioned nodes in a Standard cluster, including nodes that are resized or re-created, will have the specified tags on the corresponding Instance object in the Compute Engine API. You can reference these tags in network firewall policy rules. For instructions, see https://cloud.google.com/firewall/docs/use-tags-for-firewalls. |
| `--boot-disk-kms-key` | BOOT_DISK_KMS_KEY |  | _[project-singleton-policy-enforce.]_ The Customer Managed Encryption Key used to encrypt the boot disk attached to each node in the node pool. This should be of the form projects/[KEY_PROJECT_ID]/locations/[LOCATION]/keyRings/[RING_NAME]/cryptoKeys/[KEY_NAME]. For more information about protecting resources with Cloud KMS Keys please see: https://cloud.google.com/compute/docs/disks/customer-managed-encryption |
| `--cluster-ipv4-cidr` | CLUSTER_IPV4_CIDR |  | _[project-singleton-policy-enforce.]_ The IP address range for the pods in this cluster in CIDR notation (e.g. 10.0.0.0/14). Prior to Kubernetes version 1.7.0 this must be a subset of 10.0.0.0/8; however, starting with version 1.7.0 can be any RFC 1918 IP range. If you omit this option, a range is chosen automatically. The automatically chosen range is randomly selected from 10.0.0.0/8 and will not include IP address ranges allocated to VMs, existing routes, or ranges allocated to other clusters. The automatically chosen range might conflict with reserved IP addresses, dynamic routes, or routes within VPCs that peer with this cluster. You should specify --cluster-ipv4-cidr to prevent conflicts. This field is not applicable in a Shared VPC setup where the IP address range for the pods must be specified with --cluster-secondary-range-name |
| `--cluster-secondary-range-name` | NAME |  | _[project-singleton-policy-enforce.]_ Set the secondary range to be used as the source for pod IPs. Alias ranges will be allocated from this secondary range. NAME must be the name of an existing secondary range in the cluster subnetwork. Cannot be used with '--create-subnetwork' option. |
| `--cluster-version` | CLUSTER_VERSION |  | _[project-singleton-policy-enforce.]_ The Kubernetes version to use for the master and nodes. Defaults to server-specified. The default Kubernetes version is available using the following command. $ gcloud container get-server-config |
| `--containerd-config-from-file` | PATH_TO_FILE |  | _[project-singleton-policy-enforce.]_ Path of the YAML file that contains containerd configuration entries like configuring access to private image registries. For detailed information on the configuration usage, please refer to https://cloud.google.com/kubernetes-engine/docs/how-to/customize-containerd-configuration. Note: Updating the containerd configuration of an existing cluster or node pool requires recreation of the existing nodes, which might cause disruptions in running workloads. Use a full or relative path to a local file containing the value of containerd_config. |
| `--create-subnetwork` | [KEY=VALUE,...] |  | _[project-singleton-policy-enforce.]_ Create a new subnetwork for the cluster. The name and range of the subnetwork can be customized via optional 'name' and 'range' key-value pairs. 'name' specifies the name of the subnetwork to be created. 'range' specifies the IP range for the new subnetwork. This can either be a netmask size (e.g. '/20') or a CIDR range (e.g. '10.0.0.0/20'). If a netmask size is specified, the IP is automatically taken from the free space in the cluster's network. Examples: Create a new subnetwork with a default name and size. $ gcloud container clusters create-auto --create-subnetwork "" Create a new subnetwork named "my-subnet" with netmask of size 21. $ gcloud container clusters create-auto \ --create-subnetwork name=my-subnet,range=/21 Create a new subnetwork with a default name with the primary range of 10.100.0.0/16. $ gcloud container clusters create-auto \ --create-subnetwork range=10.100.0.0/16 Create a new subnetwork with the name "my-subnet" with a default range. $ gcloud container clusters create-auto \ --create-subnetwork name=my-subnet Cannot be used in conjunction with '--subnetwork' option. |
| `--database-encryption-key` | DATABASE_ENCRYPTION_KEY |  | _[project-singleton-policy-enforce.]_ Enable Database Encryption. Enable database encryption that will be used to encrypt Kubernetes Secrets at the application layer. The key provided should be the resource ID in the format of projects/[KEY_PROJECT_ID]/locations/[LOCATION]/keyRings/[RING_NAME]/cryptoKeys/[KEY_NAME]. For more information, see https://cloud.google.com/kubernetes-engine/docs/how-to/encrypting-secrets. |
| `--disable-l4-lb-firewall-reconciliation` |  |  | _[project-singleton-policy-enforce.]_ Disable reconciliation on the cluster for L4 Load Balancer VPC firewalls targeting ingress traffic. |
| `--enable-authorized-networks-on-private-endpoint` |  |  | _[project-singleton-policy-enforce.]_ Enable enforcement of --master-authorized-networks CIDR ranges for traffic reaching cluster's control plane via private IP. |
| `--enable-auto-ipam` |  |  | _[project-singleton-policy-enforce.]_ Enable the Auto IP Address Management (Auto IPAM) feature for the cluster. |
| `--enable-backup-restore` |  |  | _[project-singleton-policy-enforce.]_ Enable the Backup for GKE add-on. This add-on is disabled by default. To learn more, see the Backup for GKE overview: https://cloud.google.com/kubernetes-engine/docs/add-on/backup-for-gke/concepts/backup-for-gke. |
| `--enable-cilium-clusterwide-network-policy` |  |  | _[project-singleton-policy-enforce.]_ Enable Cilium Clusterwide Network Policies on the cluster. Disabled by default. |
| `--enable-confidential-nodes` |  |  | _[project-singleton-policy-enforce.]_ Enable confidential nodes for the cluster. Enabling Confidential Nodes will create nodes using Confidential VM https://docs.cloud.google.com/compute/docs/about-confidential-vm. |
| `--enable-default-compute-class` |  |  | _[project-singleton-policy-enforce.]_ Enable the default compute class to use for the cluster. To disable Default Compute Class in an existing cluster, explicitly set flag --no-enable-default-compute-class. |
| `--enable-dns-access` |  |  | _[project-singleton-policy-enforce.]_ Enable access to the cluster's control plane over DNS-based endpoint. DNS-based control plane access is recommended. |
| `--enable-fleet` |  |  | _[project-singleton-policy-enforce.]_ Set cluster project as the fleet host project. This will register the cluster to the same project. To register the cluster to a fleet in a different project, please use --fleet-project=FLEET_HOST_PROJECT. Example: $ gcloud container clusters create-auto --enable-fleet |
| `--enable-google-cloud-access` |  |  | _[project-singleton-policy-enforce.]_ When you enable Google Cloud Access, any public IP addresses owned by Google Cloud can reach the public control plane endpoint of your cluster. |
| `--enable-ip-access` |  |  | _[project-singleton-policy-enforce.]_ Enable access to the cluster's control plane over private IP and public IP if --enable-private-endpoint is not enabled. |
| `--enable-k8s-certs-via-dns` |  |  | _[project-singleton-policy-enforce.]_ Enable K8s client certificates Authentication to the cluster's control plane over DNS-based endpoint. |
| `--enable-k8s-tokens-via-dns` |  |  | _[project-singleton-policy-enforce.]_ Enable K8s Service Account tokens Authentication to the cluster's control plane over DNS-based endpoint. |
| `--enable-kernel-module-signature-enforcement` |  |  | _[project-singleton-policy-enforce.]_ Enforces that kernel modules are signed on all new nodes in the cluster unless explicitly overridden with --no-enable-kernel-module-signature-enforcement when creating the nodepool. Use --no-enable-kernel-module-signature-enforcement to disable. Examples: $ gcloud container clusters create-auto example-cluster \ --enable-kernel-module-signature-enforcement |
| `--enable-kubernetes-unstable-apis` | API,[API,...] |  | _[project-singleton-policy-enforce.]_ Enable Kubernetes beta API features on this cluster. Beta APIs are not expected to be production ready and should be avoided in production-grade environments. |
| `--enable-legacy-lustre-port` |  |  | _[project-singleton-policy-enforce.]_ Allow the Lustre CSI driver to initialize LNet (the virtual network layer for Lustre kernel module) using port 6988. This flag is required to workaround a port conflict with the gke-metadata-server on GKE nodes. |
| `--enable-lustre-csi-driver` |  |  | _[project-singleton-policy-enforce.]_ Enable the Lustre CSI Driver GKE add-on. This add-on is disabled by default. |
| `--enable-master-global-access` |  |  | _[project-singleton-policy-enforce.]_ Use with private clusters to allow access to the master's private endpoint from any Google Cloud region or on-premises environment regardless of the private cluster's region. |
| `--enable-multi-networking` |  |  | _[project-singleton-policy-enforce.]_ Enables multi-networking on the cluster. Multi-networking is disabled by default. |
| `--enable-ray-cluster-logging` |  |  | _[project-singleton-policy-enforce.]_ Enable automatic log processing sidecar for Ray clusters. |
| `--enable-ray-cluster-monitoring` |  |  | _[project-singleton-policy-enforce.]_ Enable automatic metrics collection for Ray clusters. |
| `--enable-ray-operator` |  |  | _[project-singleton-policy-enforce.]_ Enable the Ray Operator GKE add-on. This add-on is disabled by default. |
| `--fleet-project` | PROJECT_ID_OR_NUMBER |  | _[project-singleton-policy-enforce.]_ Sets fleet host project for the cluster. If specified, the current cluster will be registered as a fleet membership under the fleet host project. Example: $ gcloud container clusters create-auto --fleet-project=my-project |
| `--hpa-profile` | HPA_PROFILE |  | _[project-singleton-policy-enforce.]_ Set Horizontal Pod Autoscaler behavior. Accepted values are: none, performance. For more information, see https://cloud.google.com/kubernetes-engine/docs/how-to/horizontal-pod-autoscaling#hpa-profile. |
| `--labels` | [KEY=VALUE,...] |  | _[project-singleton-policy-enforce.]_ Labels to apply to the Google Cloud resources in use by the Kubernetes Engine cluster. These are unrelated to Kubernetes labels. Examples: $ gcloud container clusters create-auto example-cluster \ --labels=label_a=value1,label_b=,label_c=value3 |
| `--logging` | [COMPONENT,...] |  | _[project-singleton-policy-enforce.]_ Set the components that have logging enabled. Valid component values are: SYSTEM, WORKLOAD, API_SERVER, CONTROLLER_MANAGER, SCHEDULER The default is SYSTEM,WORKLOAD. If this flag is set, then SYSTEM must be included. For more information, see https://cloud.google.com/kubernetes-engine/docs/concepts/about-logs#available-logs Examples: $ gcloud container clusters create-auto --logging=SYSTEM $ gcloud container clusters create-auto --logging=SYSTEM,WORKLOAD $ gcloud container clusters create-auto \ --logging=SYSTEM,WORKLOAD,API_SERVER,CONTROLLER_MANAGER,\ SCHEDULER |
| `--membership-type` | MEMBERSHIP_TYPE |  | _[project-singleton-policy-enforce.]_ Specify a membership type for the cluster's fleet membership. Example: $ gcloud container clusters create-auto \ --membership-type=LIGHTWEIGHT. MEMBERSHIP_TYPE must be (only \ one value is supported): LIGHTWEIGHT Fleet membership representing this cluster will be lightweight. |
| `--monitoring` | [COMPONENT,...] |  | _[project-singleton-policy-enforce.]_ Set the components that have monitoring enabled. Valid component values are: SYSTEM, WORKLOAD (Deprecated), NONE, API_SERVER, CONTROLLER_MANAGER, SCHEDULER, DAEMONSET, DEPLOYMENT, HPA, POD, STATEFULSET, STORAGE, CADVISOR, KUBELET, DCGM, JOBSET For more information, see https://cloud.google.com/kubernetes-engine/docs/how-to/configure-metrics#available-metrics Examples: $ gcloud container clusters create-auto \ --monitoring=SYSTEM,API_SERVER,POD,DCGM $ gcloud container clusters create-auto --monitoring=SYSTEM |
| `--network` | NETWORK |  | _[project-singleton-policy-enforce.]_ The Compute Engine Network that the cluster will connect to. Google Kubernetes Engine will use this network when creating routes and firewalls for the clusters. Defaults to the 'default' network. |
| `--private-endpoint-subnetwork` | NAME |  | _[project-singleton-policy-enforce.]_ Sets the subnetwork GKE uses to provision the control plane's private endpoint. |
| `--release-channel` | one of: extended Clusters subscribed to 'extended' can remain on a minor version for 24 months from when the minor version is made available in the Regular channel |  | _[project-singleton-policy-enforce.]_ Release channel a cluster is subscribed to. If left unspecified and a version is specified, the cluster is enrolled in the most mature release channel where the version is available (first checking STABLE, then REGULAR, and finally RAPID). Otherwise, if no release channel and no version is specified, the cluster is enrolled in the REGULAR channel with its default version. When a cluster is subscribed to a release channel, Google maintains both the master version and the node version. Node auto-upgrade is enabled by default for release channel clusters and can be controlled via upgrade-scope exclusions (https://cloud.google.com/kubernetes-engine/docs/concepts/maintenance-windows-and-exclusions#scope_of_maintenance_to_exclude). CHANNEL must be one of: extended Clusters subscribed to 'extended' can remain on a minor version for 24 months from when the minor version is made available in the Regular channel. rapid 'rapid' channel is offered on an early access basis for customers who want to test new releases. WARNING: Versions available in the 'rapid' channel may be subject to unresolved issues with no known workaround and are not subject to any SLAs. regular Clusters subscribed to 'regular' receive versions that are considered GA quality. 'regular' is intended for production users who want to take advantage of new features. stable Clusters subscribed to 'stable' receive versions that are known to be stable and reliable in production. |
| `--security-group` | SECURITY_GROUP |  | _[project-singleton-policy-enforce.]_ The name of the RBAC security group for use with Google security groups in Kubernetes RBAC (https://kubernetes.io/docs/reference/access-authn-authz/rbac/). To include group membership as part of the claims issued by Google during authentication, a group must be designated as a security group by including it as a direct member of this group. If unspecified, no groups will be returned for use with RBAC. |
| `--security-posture` | one of: disabled, standard, enterprise |  | _[project-singleton-policy-enforce.]_ Sets the mode of the Kubernetes security posture API's off-cluster features. To enable advanced mode explicitly set the flag to --security-posture=enterprise. To enable in standard mode explicitly set the flag to --security-posture=standard To disable in an existing cluster, explicitly set the flag to --security-posture=disabled. For more information on enablement, see https://cloud.google.com/kubernetes-engine/docs/concepts/about-security-posture-dashboard#feature-enablement. SECURITY_POSTURE must be one of: disabled, standard, enterprise. |
| `--services-ipv4-cidr` | CIDR |  | _[project-singleton-policy-enforce.]_ Set the IP range for the services IPs. Can be specified as a netmask size (e.g. '/20') or as in CIDR notion (e.g. '10.100.0.0/20'). If given as a netmask size, the IP range will be chosen automatically from the available space in the network. If unspecified, the services CIDR range will be chosen with a default mask size. |
| `--services-secondary-range-name` | NAME |  | _[project-singleton-policy-enforce.]_ Set the secondary range to be used for services (e.g. ClusterIPs). NAME must be the name of an existing secondary range in the cluster subnetwork. Cannot be used with '--create-subnetwork' option. |
| `--subnetwork` | SUBNETWORK |  | _[project-singleton-policy-enforce.]_ The Google Compute Engine subnetwork (https://cloud.google.com/compute/docs/subnetworks) to which the cluster is connected. The subnetwork must belong to the network specified by --network. Cannot be used with the "--create-subnetwork" option. |
| `--tier` | one of: standard, enterprise |  | _[project-singleton-policy-enforce.]_ (DEPRECATED) Set the desired tier for the cluster. The --tier flag is deprecated. More info: https://cloud.google.com/kubernetes-engine/docs/release-notes#September_02_2025. TIER must be one of: standard, enterprise. |
| `--workload-policies` | WORKLOAD_POLICIES |  | _[project-singleton-policy-enforce.]_ Add Autopilot workload policies to the cluster. Examples: $ gcloud container clusters create-auto example-cluster \ --workload-policies=allow-net-admin The only supported workload policy is 'allow-net-admin'. |
| `--workload-vulnerability-scanning` | one of: disabled, standard, enterprise |  | _[project-singleton-policy-enforce.]_ Sets the mode of the Kubernetes security posture API's workload vulnerability scanning. To enable Advanced vulnerability insights mode explicitly set the flag to --workload-vulnerability-scanning=enterprise. To enable in standard mode explicitly set the flag to --workload-vulnerability-scanning=standard. To disable in an existing cluster, explicitly set the flag to --workload-vulnerability-scanning=disabled. For more information on enablement, see https://cloud.google.com/kubernetes-engine/docs/concepts/about-security-posture-dashboard#feature-enablement. WORKLOAD_VULNERABILITY_SCANNING must be one of: disabled, standard, enterprise. |
| `--enable-insecure-binding-system-authenticated` |  |  | _[view into pod-to-pod traffic within your cluster.]_ Allow using system:authenticated as a subject in ClusterRoleBindings and RoleBindings. Allowing bindings that reference system:authenticated is a security risk and is not recommended. To disallow binding system:authenticated in a cluster, explicitly set the --no-enable-insecure-binding-system-authenticated flag instead. |
| `--enable-insecure-binding-system-unauthenticated` |  |  | _[view into pod-to-pod traffic within your cluster.]_ Allow using system:unauthenticated and system:anonymous as subjects in ClusterRoleBindings and RoleBindings. Allowing bindings that reference system:unauthenticated and system:anonymous are a security risk and is not recommended. To disallow binding system:authenticated in a cluster, explicitly set the --no-enable-insecure-binding-system-unauthenticated flag instead. |


**Examples:**
```bash
To create a cluster with the default configuration, run:

    $ gcloud container clusters create-auto sample-cluster
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/clusters/create-auto)

---
### `gcloud container clusters delete`

Delete an existing cluster for running containers

When you delete a cluster, the following resources are deleted:

  o The control plane resources
  o All of the node instances in the cluster
  o Any Pods that are running on those instances
  o Any firewalls and routes created by Kubernetes Engine at the time of
    cluster creation
  o Data stored in host hostPath and emptyDir volumes

GKE will attempt to delete the following resources. Deletion of these
resources is not always guaranteed:

  o External load balancers created by the cluster
  o Internal load balancers created by the cluster
  o Persistent disk volumes

**Synopsis:**
```
gcloud container clusters delete NAME [NAME ...] [--async]
    [--location=LOCATION | --region=REGION | --zone=ZONE, -z ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME [NAME ...]
   The names of the clusters to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete an existing cluster, run:

    $ gcloud container clusters delete sample-cluster
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/clusters/delete)

---
### `gcloud container clusters describe`

Describe an existing cluster for running containers

Describe an existing cluster for running containers.

**Synopsis:**
```
gcloud container clusters describe NAME
    [--location=LOCATION | --region=REGION | --zone=ZONE, -z ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of this cluster.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[At most one of these can be specified:]_ Compute zone or region (e.g. us-central1-a or us-central1) for the cluster. Overrides the default compute/region or compute/zone value for this command invocation. Prefer using this flag over the --region or --zone flags. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Compute region (e.g. us-central1) for a regional cluster. Overrides the default compute/region property value for this command invocation. |
| `--zone` | ZONE, -z ZONE |  | _[At most one of these can be specified:]_ Compute zone (e.g. us-central1-a) for a zonal cluster. Overrides the default compute/zone property value for this command invocation. |


**Examples:**
```bash
To describe an existing cluster, run:

    $ gcloud container clusters describe sample-cluster
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/clusters/describe)

---
### `gcloud container clusters get-credentials`

Fetch credentials for a running cluster

gcloud container clusters get-credentials updates a kubeconfig file with
appropriate credentials and endpoint information to point kubectl at a
specific cluster in Google Kubernetes Engine.

It takes a project and a zone as parameters, passed through by set defaults
or flags. By default, credentials are written to HOME/.kube/config. You can
provide an alternate path by setting the KUBECONFIG environment variable.
If KUBECONFIG contains multiple paths, the first one is used.

This command enables switching to a specific cluster, when working with
multiple clusters. It can also be used to access a previously created
cluster from a new workstation.

By default, gcloud container clusters get-credentials will configure
kubectl to automatically refresh its credentials using the same identity as
gcloud. If you are running kubectl as part of an application, it is
recommended to use application default credentials
(https://cloud.google.com/docs/authentication/production). To configure a
kubeconfig file to use application default credentials, set the
container/use_application_default_credentials Cloud SDK property
(https://cloud.google.com/sdk/docs/properties) to true before running
gcloud container clusters get-credentials

See
https://cloud.google.com/kubernetes-engine/docs/how-to/cluster-access-for-kubectl
for kubectl usage with Google Kubernetes Engine and
https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands for
available kubectl commands.

**Synopsis:**
```
gcloud container clusters get-credentials NAME [--dns-endpoint]
    [--internal-ip]
    [--location=LOCATION | --region=REGION | --zone=ZONE, -z ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the cluster to get credentials for. Overrides the default
   container/cluster property value for this command invocation.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--dns-endpoint` |  |  | Whether to use the DNS-based endpoint for the cluster address. |
| `--internal-ip` |  |  | Whether to use the internal IP address of the cluster endpoint. |


**Examples:**
```bash
To switch to working on your cluster 'sample-cluster', run:

    $ gcloud container clusters get-credentials sample-cluster \
        --location=us-central1-f
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/clusters/get-credentials)

---
### `gcloud container clusters get-upgrade-info`

Get information about upgrades for existing clusters including auto upgrade status, upgrade history, upgrade targets, and end of support timelines

Get information about upgrades for existing clusters including auto upgrade
status, upgrade history, upgrade targets, and end of support timelines.

**Synopsis:**
```
gcloud container clusters get-upgrade-info NAME
    [--location=LOCATION | --region=REGION | --zone=ZONE, -z ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of your existing cluster.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[At most one of these can be specified:]_ Compute zone or region (e.g. us-central1-a or us-central1) for the cluster. Overrides the default compute/region or compute/zone value for this command invocation. Prefer using this flag over the --region or --zone flags. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Compute region (e.g. us-central1) for a regional cluster. Overrides the default compute/region property value for this command invocation. |
| `--zone` | ZONE, -z ZONE |  | _[At most one of these can be specified:]_ Compute zone (e.g. us-central1-a) for a zonal cluster. Overrides the default compute/zone property value for this command invocation. |


**Examples:**
```bash
To get upgrade information for an existing cluster, run:

    $ gcloud container clusters get-upgrade-info sample-cluster
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/clusters/get-upgrade-info)

---
### `gcloud container clusters list`

List existing clusters for running containers

List existing clusters for running containers.

This command queries cluster across all locations unless either
'--location', '--region', or '--zone' are specified.

**Synopsis:**
```
gcloud container clusters list
    [--location=LOCATION | --region=REGION | --zone=ZONE, -z ZONE]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[At most one of these can be specified:]_ Compute zone or region (e.g. us-central1-a or us-central1) for the cluster. Overrides the default compute/region or compute/zone value for this command invocation. Prefer using this flag over the --region or --zone flags. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Compute region (e.g. us-central1) for a regional cluster. Overrides the default compute/region property value for this command invocation. |
| `--zone` | ZONE, -z ZONE |  | _[At most one of these can be specified:]_ Compute zone (e.g. us-central1-a) for a zonal cluster. Overrides the default compute/zone property value for this command invocation. |


**Examples:**
```bash
To list existing clusters in all locations, run:

    $ gcloud container clusters list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/clusters/list)

---
### `gcloud container clusters resize`

Resizes an existing cluster for running containers

Resize an existing cluster to a provided size.

If you have multiple node pools, you must specify which node pool to resize
by using the --node-pool flag. You are not required to use the flag if you
have a single node pool.

When increasing the size of a container cluster, the new instances are
created with the same configuration as the existing instances. Existing
pods are not moved onto the new instances, but new pods (such as those
created by resizing a replication controller) will be scheduled onto the
new instances.

When decreasing a cluster, the nodes are drained. As a result, the pods
running on these nodes are gracefully terminated. If your pods are being
managed by a workload controller, the controller will attempt to reschedule
them onto the remaining instances. If your pods are not managed by a
workload controller, they will not be restarted. Note that when resizing
down, instances running pods and instances without pods are not
differentiated. Resize will pick instances to remove at random.

When you resize a node pool that spans multiple zones, the new size
represents the number of nodes in the node pool per zone. For example, if
you have a node pool of size 2 spanning two zones, the total node count is
4. If you resize the node pool with --num-nodes=4, the total node count
becomes 8.

**Synopsis:**
```
gcloud container clusters resize NAME
    (--num-nodes=NUM_NODES | --size=NUM_NODES) [--async]
    [--node-pool=NODE_POOL]
    [--location=LOCATION | --region=REGION | --zone=ZONE, -z ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of this cluster.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--num-nodes` | NUM_NODES |  | _[Exactly one of these must be specified:]_ Target number of nodes in the cluster. |
| `--size` | NUM_NODES |  | _[Exactly one of these must be specified:]_ (DEPRECATED) Target number of nodes in the cluster. The --size flag is now deprecated. Please use --num-nodes instead. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--node-pool` | NODE_POOL |  | The node pool to resize. |


**Examples:**
```bash
To resize the default node pool of an existing cluster, run:

    $ gcloud container clusters resize sample-cluster --num-nodes=2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/clusters/resize)

---
### `gcloud container clusters update`

Update cluster settings for an existing container cluster

Update cluster settings for an existing container cluster.

**Synopsis:**
```
gcloud container clusters update NAME
    (--anonymous-authentication-config=ANONYMOUS_AUTHENTICATION_CONFIG
      | --autopilot-workload-policies=WORKLOAD_POLICIES
      | --autoprovisioning-cgroup-mode=AUTOPROVISIONING_CGROUP_MODE
      | --autoprovisioning-enable-insecure-kubelet-readonly-port
      | --autoprovisioning-network-tags=[TAGS,...]
      | --autoprovisioning-resource-manager-tags=[KEY=VALUE,...]
      | --autoscaling-profile=AUTOSCALING_PROFILE
      | --complete-credential-rotation | --complete-ip-rotation
      | --containerd-config-from-file=PATH_TO_FILE
      | --database-encryption-key=DATABASE_ENCRYPTION_KEY
      | --disable-database-encryption | --disable-default-snat
      | --disable-workload-identity
      | --[no-]enable-autopilot-compatibility-auditing
      | --enable-autoscaling
      | --[no-]enable-cilium-clusterwide-network-policy
      | --enable-cost-allocation | --enable-default-compute-class
      | --enable-fqdn-network-policy | --enable-identity-service
      | --enable-image-streaming | --enable-insecure-kubelet-readonly-port
      | --enable-intra-node-visibility
      | --enable-kernel-module-signature-enforcement
      | --enable-kubernetes-unstable-apis=API,[API,...]
      | --enable-l4-ilb-subsetting | --enable-legacy-authorization
      | --enable-legacy-lustre-port | --enable-multi-networking
      | --enable-network-policy | --enable-private-nodes
      | --[no-]enable-ray-cluster-logging
      | --[no-]enable-ray-cluster-monitoring | --enable-service-externalips
      | --enable-shielded-nodes | --enable-stackdriver-kubernetes
      | --enable-vertical-pod-autoscaling | --gateway-api=GATEWAY_API
      | --generate-password | --hpa-profile=HPA_PROFILE
      | --in-transit-encryption=IN_TRANSIT_ENCRYPTION
      | --logging-variant=LOGGING_VARIANT | --maintenance-window=START_TIME
      | --network-performance-configs=[PROPERTY1=VALUE1,...]
      | --node-locations=ZONE,[ZONE,...]
      | --notification-config=[pubsub=ENABLED|DISABLED,
      pubsub-topic=TOPIC,...] | --patch-update=[PATCH_UPDATE]
      | --private-ipv6-google-access-type=PRIVATE_IPV6_GOOGLE_ACCESS_TYPE
      | --release-channel=CHANNEL
      | --remove-autopilot-workload-policies=REMOVE_WORKLOAD_POLICIES
      | --remove-labels=[KEY,...]
      | --remove-workload-policies=REMOVE_WORKLOAD_POLICIES
      | --security-group=SECURITY_GROUP
      | --security-posture=SECURITY_POSTURE | --set-password
      | --stack-type=STACK_TYPE | --start-credential-rotation
      | --start-ip-rotation | --tier=TIER
      | --update-addons=[ADDON=ENABLED|DISABLED,...]
      | --update-labels=[KEY=VALUE,...]
      | --workload-policies=WORKLOAD_POLICIES
      | --workload-pool=WORKLOAD_POOL
      | --workload-vulnerability-scanning=WORKLOAD_VULNERABILITY_SCANNING
      | --additional-ip-ranges=[subnetwork=NAME,pod-ipv4-range=NAME,...]
      --remove-additional-ip-ranges=[subnetwork=NAME,
      pod-ipv4-range=NAME,...]
      | --additional-pod-ipv4-ranges=NAME,[NAME,...]
      --remove-additional-pod-ipv4-ranges=NAME,[NAME,...]
      | --auto-monitoring-scope=AUTO_MONITORING_SCOPE
      --logging=[COMPONENT,...]
      --monitoring=[COMPONENT,...] --disable-managed-prometheus
      | --enable-managed-prometheus
      | --binauthz-evaluation-mode=BINAUTHZ_EVALUATION_MODE
      | --enable-binauthz | --clear-fleet-project --enable-fleet
      --fleet-project=PROJECT_ID_OR_NUMBER
      --membership-type=MEMBERSHIP_TYPE --unset-membership-type
      | --clear-maintenance-window | --remove-maintenance-exclusion=NAME
      | [(--add-maintenance-exclusion-end=TIME_STAMP
      | --add-maintenance-exclusion-until-end-of-support)
      : --add-maintenance-exclusion-name=NAME
      --add-maintenance-exclusion-scope=SCOPE
      --add-maintenance-exclusion-start=TIME_STAMP]
      | --maintenance-window-end=TIME_STAMP
      --maintenance-window-recurrence=RRULE
      --maintenance-window-start=TIME_STAMP
      | --clear-resource-usage-bigquery-dataset
      | --enable-network-egress-metering
      --enable-resource-consumption-metering
      --resource-usage-bigquery-dataset=RESOURCE_USAGE_BIGQUERY_DATASET
      | --cluster-dns=CLUSTER_DNS --cluster-dns-domain=CLUSTER_DNS_DOMAIN
      --cluster-dns-scope=CLUSTER_DNS_SCOPE
      --additive-vpc-scope-dns-domain=ADDITIVE_VPC_SCOPE_DNS_DOMAIN
      | --disable-additive-vpc-scope
      | --dataplane-v2-observability-mode=DATAPLANE_V2_OBSERVABILITY_MODE
      | --disable-dataplane-v2-flow-observability
      | --enable-dataplane-v2-flow-observability
      --disable-dataplane-v2-metrics | --enable-dataplane-v2-metrics
      | --disable-auto-ipam | --enable-auto-ipam
      | --disable-l4-lb-firewall-reconciliation
      | --enable-l4-lb-firewall-reconciliation
      | --enable-authorized-networks-on-private-endpoint
      --enable-dns-access --enable-google-cloud-access --enable-ip-access
      --enable-k8s-certs-via-dns --enable-k8s-tokens-via-dns
      --enable-master-global-access --enable-private-endpoint
      --enable-master-authorized-networks
      --master-authorized-networks=NETWORK,[NETWORK,...]
      | [--enable-autoprovisioning
      : --autoprovisioning-config-file=PATH_TO_FILE
      | --autoprovisioning-image-type=AUTOPROVISIONING_IMAGE_TYPE
      --autoprovisioning-locations=ZONE,[ZONE,...]
      --autoprovisioning-min-cpu-platform=PLATFORM --max-cpu=MAX_CPU
      --max-memory=MAX_MEMORY --min-cpu=MIN_CPU --min-memory=MIN_MEMORY
      --autoprovisioning-max-surge-upgrade=AUTOPROVISIONING_MAX_SURGE_UPGRADE --autoprovisioning-max-unavailable-upgrade=AUTOPROVISIONING_MAX_UNAVAILABLE_UPGRADE --autoprovisioning-node-pool-soak-duration=AUTOPROVISIONING_NODE_POOL_SOAK_DURATION --autoprovisioning-standard-rollout-policy=[batch-node-count=BATCH_NODE_COUNT,
      batch-percent=BATCH_NODE_PERCENTAGE,
      batch-soak-duration=BATCH_SOAK_DURATION,...]
      --enable-autoprovisioning-blue-green-upgrade
      | --enable-autoprovisioning-surge-upgrade
      --autoprovisioning-scopes=[SCOPE,...]
      --autoprovisioning-service-account=AUTOPROVISIONING_SERVICE_ACCOUNT
      --enable-autoprovisioning-autorepair
      --enable-autoprovisioning-autoupgrade
      [--max-accelerator=[type=TYPE,count=COUNT,...]
      : --min-accelerator=[type=TYPE,count=COUNT,...]]]
      | --enable-insecure-binding-system-authenticated
      --enable-insecure-binding-system-unauthenticated
      | --logging-service=LOGGING_SERVICE
      --monitoring-service=MONITORING_SERVICE
      | --[no-]enable-secret-manager --[no-]enable-secret-manager-rotation
      --secret-manager-rotation-interval=SECRET_MANAGER_ROTATION_INTERVAL
      | --password=PASSWORD --enable-basic-auth
      | --username=USERNAME, -u USERNAME) [--async]
    [--cloud-run-config=[load-balancer-type=EXTERNAL,...]]
    [--node-pool=NODE_POOL]
    [--location=LOCATION | --region=REGION | --zone=ZONE, -z ZONE]
    [--location-policy=LOCATION_POLICY --max-nodes=MAX_NODES
      --min-nodes=MIN_NODES
      --total-max-nodes=TOTAL_MAX_NODES --total-min-nodes=TOTAL_MIN_NODES]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of the cluster to update.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--anonymous-authentication-config` | one of: ENABLED 'ENABLED' enables anonymous calls |  | _[Exactly one of these must be specified:]_ Enable or restrict anonymous access to the cluster. When enabled, anonymous users will be authenticated as system:anonymous with the group system:unauthenticated. Limiting access restricts anonymous access to only the health check endpoints /readyz, /livez, and /healthz. ANONYMOUS_AUTHENTICATION_CONFIG must be one of: ENABLED 'ENABLED' enables anonymous calls. LIMITED 'LIMITED' restricts anonymous access to the cluster. Only calls to the health check endpoints are allowed anonymously, all other calls will be rejected. |
| `--autopilot-workload-policies` | WORKLOAD_POLICIES |  | _[Exactly one of these must be specified:]_ Add Autopilot workload policies to the cluster. Examples: $ gcloud container clusters update example-cluster \ --autopilot-workload-policies=allow-net-admin The only supported workload policy is 'allow-net-admin'. |
| `--autoprovisioning-cgroup-mode` | one of: default, v1, v2 |  | _[Exactly one of these must be specified:]_ Sets the cgroup mode for auto-provisioned nodes. Updating this flag triggers an update using surge upgrades of all existing auto-provisioned nodes to apply the new value of cgroup mode. For an Autopilot cluster, the specified cgroup mode will be set on all existing and new nodes in the cluster. For a Standard cluster, the specified cgroup mode will be set on all existing and new auto-provisioned node pools in the cluster. If not set, GKE uses cgroupv2 for new nodes when the cluster was created running 1.26 or later, and cgroupv1 for clusters created running 1.25 or earlier. To check your initial cluster version, run gcloud container clusters describe [NAME] --format="value(initialClusterVersion)" For clusters created running version 1.26 or later, you can't set the cgroup mode to v1. To learn more, see: https://cloud.google.com/kubernetes-engine/docs/how-to/migrate-cgroupv2. AUTOPROVISIONING_CGROUP_MODE must be one of: default, v1, v2. |
| `--autoprovisioning-enable-insecure-kubelet-readonly-port` |  |  | _[Exactly one of these must be specified:]_ Enables the Kubelet's insecure read only port for Autoprovisioned Node Pools. If not set, the value from nodePoolDefaults.nodeConfigDefaults will be used. To disable the readonly port --no-autoprovisioning-enable-insecure-kubelet-readonly-port. |
| `--autoprovisioning-network-tags` | [TAGS,...] |  | _[Exactly one of these must be specified:]_ Replaces the user specified Compute Engine tags on all nodes in all the existing auto-provisioned node pools in the Standard cluster or the Autopilot with the given tags (comma separated). Examples: $ gcloud container clusters update example-cluster \ --autoprovisioning-network-tags=tag1,tag2 New nodes in auto-provisioned node pools, including ones created by resize or recreate, will have these tags on the Compute Engine API instance object and these tags can be used in firewall rules. See https://cloud.google.com/sdk/gcloud/reference/compute/firewall-rules/create for examples. |
| `--autoprovisioning-resource-manager-tags` | [KEY=VALUE,...] |  | _[Exactly one of these must be specified:]_ For an Autopilot cluster, the specified comma-separated resource manager tags that has the GCP_FIREWALL purpose replace the existing tags on all nodes in the cluster. For a Standard cluster, the specified comma-separated resource manager tags that has the GCE_FIREWALL purpose are applied to all nodes in the new newly created auto-provisioned node pools. Existing auto-provisioned node pools retain the tags that they had before the update. To update tags on an existing auto-provisioned node pool, use the node pool level flag '--resource-manager-tags'. Examples: $ gcloud container clusters update example-cluster \ --autoprovisioning-resource-manager-tags=tagKeys/\ 1234=tagValues/2345 $ gcloud container clusters update example-cluster \ --autoprovisioning-resource-manager-tags=my-project/key1=value1 $ gcloud container clusters update example-cluster \ --autoprovisioning-resource-manager-tags=12345/key1=value1,\ 23456/key2=value2 $ gcloud container clusters update example-cluster \ --autoprovisioning-resource-manager-tags= All nodes in an Autopilot cluster or all newly created auto-provisioned nodes in a Standard cluster, including nodes that are resized or re-created, will have the specified tags on the corresponding Instance object in the Compute Engine API. You can reference these tags in network firewall policy rules. For instructions, see https://cloud.google.com/firewall/docs/use-tags-for-firewalls. |
| `--autoscaling-profile` | AUTOSCALING_PROFILE |  | _[Exactly one of these must be specified:]_ Set autoscaling behaviour, choices are 'optimize-utilization' and 'balanced'. Default is 'balanced'. |
| `--complete-credential-rotation` |  |  | _[Exactly one of these must be specified:]_ Complete the IP and credential rotation for this cluster. For example: $ gcloud container clusters update example-cluster \ --complete-credential-rotation This causes the cluster to stop serving its old IP, return to a single IP, and invalidate old credentials. See documentation for more details: https://cloud.google.com/kubernetes-engine/docs/how-to/credential-rotation. |
| `--complete-ip-rotation` |  |  | _[Exactly one of these must be specified:]_ Complete the IP rotation for this cluster. For example: $ gcloud container clusters update example-cluster \ --complete-ip-rotation This causes the cluster to stop serving its old IP, and return to a single IP state. See documentation for more details: https://cloud.google.com/kubernetes-engine/docs/how-to/ip-rotation. |
| `--containerd-config-from-file` | PATH_TO_FILE |  | _[Exactly one of these must be specified:]_ Path of the YAML file that contains containerd configuration entries like configuring access to private image registries. For detailed information on the configuration usage, please refer to https://cloud.google.com/kubernetes-engine/docs/how-to/customize-containerd-configuration. Note: Updating the containerd configuration of an existing cluster or node pool requires recreation of the existing nodes, which might cause disruptions in running workloads. Use a full or relative path to a local file containing the value of containerd_config. |
| `--database-encryption-key` | DATABASE_ENCRYPTION_KEY |  | _[Exactly one of these must be specified:]_ Enable Database Encryption. Enable database encryption that will be used to encrypt Kubernetes Secrets at the application layer. The key provided should be the resource ID in the format of projects/[KEY_PROJECT_ID]/locations/[LOCATION]/keyRings/[RING_NAME]/cryptoKeys/[KEY_NAME]. For more information, see https://cloud.google.com/kubernetes-engine/docs/how-to/encrypting-secrets. |
| `--disable-database-encryption` |  |  | _[Exactly one of these must be specified:]_ Disable database encryption. Disable Database Encryption which encrypt Kubernetes Secrets at the application layer. For more information, see https://cloud.google.com/kubernetes-engine/docs/how-to/encrypting-secrets. |
| `--disable-default-snat` |  |  | _[Exactly one of these must be specified:]_ Disable default source NAT rules applied in cluster nodes. By default, cluster nodes perform source network address translation (SNAT) for packets sent from Pod IP address sources to destination IP addresses that are not in the non-masquerade CIDRs list. For more details about SNAT and IP masquerading, see: https://cloud.google.com/kubernetes-engine/docs/how-to/ip-masquerade-agent#how_ipmasq_works SNAT changes the packet's source IP address to the node's internal IP address. When this flag is set, GKE does not perform SNAT for packets sent to any destination. You must set this flag if the cluster uses privately reused public IPs. The --disable-default-snat flag is only applicable to private GKE clusters, which are inherently VPC-native. Thus, --disable-default-snat requires that the cluster was created with both --enable-ip-alias and --enable-private-nodes. |
| `--disable-workload-identity` |  |  | _[Exactly one of these must be specified:]_ Disable Workload Identity on the cluster. For more information on Workload Identity, see https://cloud.google.com/kubernetes-engine/docs/how-to/workload-identity |
| `--[no-]enable-autopilot-compatibility-auditing` |  |  | _[Exactly one of these must be specified:]_ Lets you run the gcloud container clusters check-autopilot-compatibility (https://cloud.google.com/sdk/gcloud/reference/container/clusters/check-autopilot-compatibility) command to check whether your workloads are compatible with Autopilot mode. This flag is only applicable to clusters that run version 1.31.6-gke.1027000 or later. Note: This flag causes a control plane restart. Use --enable-autopilot-compatibility-auditing to enable and --no-enable-autopilot-compatibility-auditing to disable. |
| `--enable-autoscaling` |  |  | _[Exactly one of these must be specified:]_ Enables autoscaling for a node pool. Enables autoscaling in the node pool specified by --node-pool or the default node pool if --node-pool is not provided. If not already, --max-nodes or --total-max-nodes must also be set. |
| `--[no-]enable-cilium-clusterwide-network-policy` |  |  | _[Exactly one of these must be specified:]_ Enable Cilium Clusterwide Network Policies on the cluster. Use --enable-cilium-clusterwide-network-policy to enable and --no-enable-cilium-clusterwide-network-policy to disable. |
| `--enable-cost-allocation` |  |  | _[Exactly one of these must be specified:]_ Enable the cost management feature. When enabled, you can get informational GKE cost breakdowns by cluster, namespace and label in your billing data exported to BigQuery (https://cloud.google.com/billing/docs/how-to/export-data-bigquery). Use --no-enable-cost-allocation to disable this feature. |
| `--enable-default-compute-class` |  |  | _[Exactly one of these must be specified:]_ Enable the default compute class to use for the cluster. To disable Default Compute Class in an existing cluster, explicitly set flag --no-enable-default-compute-class. |
| `--enable-fqdn-network-policy` |  |  | _[Exactly one of these must be specified:]_ Enable FQDN Network Policies on the cluster. FQDN Network Policies are disabled by default. |
| `--enable-identity-service` |  |  | _[Exactly one of these must be specified:]_ Enable Identity Service component on the cluster. When enabled, users can authenticate to Kubernetes cluster with external identity providers. Identity Service is by default disabled when creating a new cluster. To disable Identity Service in an existing cluster, explicitly set flag --no-enable-identity-service. |
| `--enable-image-streaming` |  |  | _[Exactly one of these must be specified:]_ Specifies whether to enable image streaming on cluster. |
| `--enable-insecure-kubelet-readonly-port` |  |  | _[Exactly one of these must be specified:]_ Enables the Kubelet's insecure read only port. To disable the readonly port on a cluster or node-pool set the flag to --no-enable-insecure-kubelet-readonly-port. |
| `--enable-intra-node-visibility` |  |  | _[Exactly one of these must be specified:]_ Enable Intra-node visibility for this cluster. Enabling intra-node visibility makes your intra-node pod-to-pod traffic visible to the networking fabric. With this feature, you can use VPC flow logging or other VPC features for intra-node traffic. Enabling it on an existing cluster causes the cluster master and the cluster nodes to restart, which might cause a disruption. |
| `--enable-kernel-module-signature-enforcement` |  |  | _[Exactly one of these must be specified:]_ Enforces that kernel modules are signed on all new nodes in the cluster unless explicitly overridden with --no-enable-kernel-module-signature-enforcement when creating the nodepool. Use --no-enable-kernel-module-signature-enforcement to disable. Examples: $ gcloud container clusters update example-cluster \ --enable-kernel-module-signature-enforcement |
| `--enable-kubernetes-unstable-apis` | API,[API,...] |  | _[Exactly one of these must be specified:]_ Enable Kubernetes beta API features on this cluster. Beta APIs are not expected to be production ready and should be avoided in production-grade environments. |
| `--enable-l4-ilb-subsetting` |  |  | _[Exactly one of these must be specified:]_ Enable Subsetting for L4 ILB services created on this cluster. |
| `--enable-legacy-authorization` |  |  | _[Exactly one of these must be specified:]_ Enables the legacy ABAC authentication for the cluster. User rights are granted through the use of policies which combine attributes together. For a detailed look at these properties and related formats, see https://kubernetes.io/docs/admin/authorization/abac/. To use RBAC permissions instead, create or update your cluster with the option --no-enable-legacy-authorization. |
| `--enable-legacy-lustre-port` |  |  | _[Exactly one of these must be specified:]_ Allow the Lustre CSI driver to initialize LNet (the virtual network layer for Lustre kernel module) using port 6988. This flag is required to workaround a port conflict with the gke-metadata-server on GKE nodes. |
| `--enable-multi-networking` |  |  | _[Exactly one of these must be specified:]_ Enables multi-networking on the cluster. Multi-networking is disabled by default. |
| `--enable-network-policy` |  |  | _[Exactly one of these must be specified:]_ Enable network policy enforcement for this cluster. If you are enabling network policy on an existing cluster the network policy addon must first be enabled on the master by using --update-addons=NetworkPolicy=ENABLED flag. |
| `--enable-private-nodes` |  |  | _[Exactly one of these must be specified:]_ Standard cluster: Enable private nodes as a default behavior for all newly created node pools, if --enable-private-nodes is not provided at node pool creation time. Modifications to this flag do not affect `--enable-private-nodes` state of the existing node pools. Autopilot cluster: Force new and existing workloads, without explicit cloud.google.com/private-node=true node selector, to run on nodes with no public IP address. Modifications to this flag trigger a re-schedule operation on all existng workloads to run on different node VMs. |
| `--[no-]enable-ray-cluster-logging` |  |  | _[Exactly one of these must be specified:]_ Enable automatic log processing sidecar for Ray clusters. Use --enable-ray-cluster-logging to enable and --no-enable-ray-cluster-logging to disable. |
| `--[no-]enable-ray-cluster-monitoring` |  |  | _[Exactly one of these must be specified:]_ Enable automatic metrics collection for Ray clusters. Use --enable-ray-cluster-monitoring to enable and --no-enable-ray-cluster-monitoring to disable. |
| `--enable-service-externalips` |  |  | _[Exactly one of these must be specified:]_ Enables use of services with externalIPs field. |
| `--enable-shielded-nodes` |  |  | _[Exactly one of these must be specified:]_ Enable Shielded Nodes for this cluster. Enabling Shielded Nodes will enable a more secure Node credential bootstrapping implementation. Starting with version 1.18, clusters will have Shielded GKE nodes by default. |
| `--enable-stackdriver-kubernetes` |  |  | _[Exactly one of these must be specified:]_ (DEPRECATED) Enable Cloud Operations for GKE. The --enable-stackdriver-kubernetes flag is deprecated and will be removed in an upcoming release. Please use --logging and --monitoring instead. For more information, please read: https://cloud.google.com/kubernetes-engine/docs/concepts/about-logs and https://cloud.google.com/kubernetes-engine/docs/how-to/configure-metrics. |
| `--gateway-api` | one of: disabled Gateway controller will be disabled in the cluster |  | _[Enable vertical pod autoscaling for a cluster.]_ Enables GKE Gateway controller in this cluster. The value of the flag specifies which Open Source Gateway API release channel will be used to define Gateway resources. GATEWAY_API must be one of: disabled Gateway controller will be disabled in the cluster. standard Gateway controller will be enabled in the cluster. Resource definitions from the standard OSS Gateway API release channel will be installed. |
| `--generate-password` |  |  | _[Enable vertical pod autoscaling for a cluster.]_ Ask the server to generate a secure password and use that as the basic auth password, keeping the existing username. |
| `--hpa-profile` | HPA_PROFILE |  | _[Enable vertical pod autoscaling for a cluster.]_ Set Horizontal Pod Autoscaler behavior. Accepted values are: none, performance. For more information, see https://cloud.google.com/kubernetes-engine/docs/how-to/horizontal-pod-autoscaling#hpa-profile. |
| `--in-transit-encryption` | one of: inter-node-transparent, none |  | _[Enable vertical pod autoscaling for a cluster.]_ Enable Dataplane V2 in-transit encryption. Dataplane v2 in-transit encryption is disabled by default. IN_TRANSIT_ENCRYPTION must be one of: inter-node-transparent, none. |
| `--logging-variant` | one of: DEFAULT 'DEFAULT' variant requests minimal resources but may not guarantee high throughput |  | _[Enable vertical pod autoscaling for a cluster.]_ Specifies the logging variant that will be deployed on all the nodes in the cluster. Valid logging variants are MAX_THROUGHPUT, DEFAULT. If no value is specified, DEFAULT is used. LOGGING_VARIANT must be one of: DEFAULT 'DEFAULT' variant requests minimal resources but may not guarantee high throughput. MAX_THROUGHPUT 'MAX_THROUGHPUT' variant requests more node resources and is able to achieve logging throughput up to 10MB per sec. |
| `--maintenance-window` | START_TIME |  | _[Enable vertical pod autoscaling for a cluster.]_ Set a time of day when you prefer maintenance to start on this cluster. For example: $ gcloud container clusters update example-cluster \ --maintenance-window=12:43 The time corresponds to the UTC time zone, and must be in HH:MM format. Non-emergency maintenance will occur in the 4 hour block starting at the specified time. This is mutually exclusive with the recurring maintenance windows and will overwrite any existing window. Compatible with maintenance exclusions. To remove an existing maintenance window from the cluster, use '--clear-maintenance-window'. |
| `--network-performance-configs` | [PROPERTY1=VALUE1,...] |  | _[Enable vertical pod autoscaling for a cluster.]_ Configures network performance settings for the cluster. Node pools can override with their own settings. total-egress-bandwidth-tier Total egress bandwidth is the available outbound bandwidth from a VM, regardless of whether the traffic is going to internal IP or external IP destinations. The following tier values are allowed: [TIER_UNSPECIFIED,TIER_1]. See https://cloud.google.com/compute/docs/networking/configure-vm-with-high-bandwidth-configuration for more information. |
| `--node-locations` | ZONE,[ZONE,...] |  | _[Enable vertical pod autoscaling for a cluster.]_ The set of zones in which the specified node footprint should be replicated. All zones must be in the same region as the cluster's master(s), specified by the -location, --zone, or --region flag. Additionally, for zonal clusters, --node-locations must contain the cluster's primary zone. If not specified, all nodes will be in the cluster's primary zone (for zonal clusters) or spread across three randomly chosen zones within the cluster's region (for regional clusters). Note that NUM_NODES nodes will be created in each zone, such that if you specify --num-nodes=4 and choose two locations, 8 nodes will be created. Multiple locations can be specified, separated by commas. For example: $ gcloud container clusters update example-cluster \ --location us-central1-a \ --node-locations us-central1-a,us-central1-b |
| `--notification-config` | [pubsub=ENABLED\|DISABLED,pubsub-topic=TOPIC,...] |  | _[Enable vertical pod autoscaling for a cluster.]_ The notification configuration of the cluster. GKE supports publishing cluster upgrade notifications to any Pub/Sub topic you created in the same project. Create a subscription for the topic specified to receive notification messages. See https://cloud.google.com/pubsub/docs/admin on how to manage Pub/Sub topics and subscriptions. You can also use the filter option to specify which event types you'd like to receive from the following options: SecurityBulletinEvent, UpgradeEvent, UpgradeInfoEvent, UpgradeAvailableEvent. Examples: $ gcloud container clusters update example-cluster \ --notification-config=pubsub=ENABLED,pubsub-topic=projects/\ {project}/topics/{topic-name} $ gcloud container clusters update example-cluster \ --notification-config=pubsub=ENABLED,pubsub-topic=projects/\ {project}/topics/{topic-name},\ filter="SecurityBulletinEvent\|UpgradeEvent" The project of the Pub/Sub topic must be the same one as the cluster. It can be either the project ID or the project number. |
| `--patch-update` | one of: accelerated, default |  | _[Enable vertical pod autoscaling for a cluster.]_ The patch update to use for the cluster. Setting to 'accelerated' automatically upgrades the cluster to the latest patch available within the cluster's current minor version and release channel. Setting to 'default' automatically upgrades the cluster to the default patch upgrade targetversion available within the cluster's current minor version and release channel. PATCH_UPDATE must be one of: accelerated, default. |
| `--private-ipv6-google-access-type` | one of: bidirectional Allows Google services to initiate connections to GKE pods in this cluster |  | _[Enable vertical pod autoscaling for a cluster.]_ Sets the type of private access to Google services over IPv6. PRIVATE_IPV6_GOOGLE_ACCESS_TYPE must be one of: bidirectional Allows Google services to initiate connections to GKE pods in this cluster. This is not intended for common use, and requires previous integration with Google services. disabled Default value. Disables private access to Google services over IPv6. outbound-only Allows GKE pods to make fast, secure requests to Google services over IPv6. This is the most common use of private IPv6 access. $ gcloud alpha container clusters create \ --private-ipv6-google-access-type=disabled $ gcloud alpha container clusters create \ --private-ipv6-google-access-type=outbound-only $ gcloud alpha container clusters create \ --private-ipv6-google-access-type=bidirectional PRIVATE_IPV6_GOOGLE_ACCESS_TYPE must be one of: bidirectional, disabled, outbound-only. |
| `--release-channel` | one of: None Use 'None' to opt-out of any release channel |  | _[Enable vertical pod autoscaling for a cluster.]_ Subscribe or unsubscribe this cluster to a release channel. When a cluster is subscribed to a release channel, Google maintains both the master version and the node version. Node auto-upgrade is enabled by default for release channel clusters and can be controlled via upgrade-scope exclusions (https://cloud.google.com/kubernetes-engine/docs/concepts/maintenance-windows-and-exclusions#scope_of_maintenance_to_exclude). CHANNEL must be one of: None Use 'None' to opt-out of any release channel. extended Clusters subscribed to 'extended' can remain on a minor version for 24 months from when the minor version is made available in the Regular channel. rapid 'rapid' channel is offered on an early access basis for customers who want to test new releases. WARNING: Versions available in the 'rapid' channel may be subject to unresolved issues with no known workaround and are not subject to any SLAs. regular Clusters subscribed to 'regular' receive versions that are considered GA quality. 'regular' is intended for production users who want to take advantage of new features. stable Clusters subscribed to 'stable' receive versions that are known to be stable and reliable in production. |
| `--remove-autopilot-workload-policies` | REMOVE_WORKLOAD_POLICIES |  | _[Enable vertical pod autoscaling for a cluster.]_ Remove Autopilot workload policies from the cluster. Examples: $ gcloud container clusters update example-cluster \ --remove-autopilot-workload-policies=allow-net-admin The only supported workload policy is 'allow-net-admin'. |
| `--remove-labels` | [KEY,...] |  | _[Enable vertical pod autoscaling for a cluster.]_ Labels to remove from the Google Cloud resources in use by the Kubernetes Engine cluster. These are unrelated to Kubernetes labels. Examples: $ gcloud container clusters update example-cluster \ --remove-labels=label_a,label_b |
| `--remove-workload-policies` | REMOVE_WORKLOAD_POLICIES |  | _[Enable vertical pod autoscaling for a cluster.]_ Remove Autopilot workload policies from the cluster. Examples: $ gcloud container clusters update example-cluster \ --remove-workload-policies=allow-net-admin The only supported workload policy is 'allow-net-admin'. |
| `--security-group` | SECURITY_GROUP |  | _[Enable vertical pod autoscaling for a cluster.]_ The name of the RBAC security group for use with Google security groups in Kubernetes RBAC (https://kubernetes.io/docs/reference/access-authn-authz/rbac/). To include group membership as part of the claims issued by Google during authentication, a group must be designated as a security group by including it as a direct member of this group. If unspecified, no groups will be returned for use with RBAC. |
| `--security-posture` | one of: disabled, standard, enterprise |  | _[Enable vertical pod autoscaling for a cluster.]_ Sets the mode of the Kubernetes security posture API's off-cluster features. To enable advanced mode explicitly set the flag to --security-posture=enterprise. To enable in standard mode explicitly set the flag to --security-posture=standard To disable in an existing cluster, explicitly set the flag to --security-posture=disabled. For more information on enablement, see https://cloud.google.com/kubernetes-engine/docs/concepts/about-security-posture-dashboard#feature-enablement. SECURITY_POSTURE must be one of: disabled, standard, enterprise. |
| `--set-password` |  |  | _[Enable vertical pod autoscaling for a cluster.]_ Set the basic auth password to the specified value, keeping the existing username. |
| `--stack-type` | one of: ipv4, ipv4-ipv6 |  | _[Enable vertical pod autoscaling for a cluster.]_ IP stack type of the cluster nodes. STACK_TYPE must be one of: ipv4, ipv4-ipv6. |
| `--start-credential-rotation` |  |  | _[Enable vertical pod autoscaling for a cluster.]_ Start the rotation of IP and credentials for this cluster. For example: $ gcloud container clusters update example-cluster \ --start-credential-rotation This causes the cluster to serve on two IPs, and will initiate a node upgrade to point to the new IP. See documentation for more details: https://cloud.google.com/kubernetes-engine/docs/how-to/credential-rotation. |
| `--start-ip-rotation` |  |  | _[Enable vertical pod autoscaling for a cluster.]_ Start the rotation of this cluster to a new IP. For example: $ gcloud container clusters update example-cluster \ --start-ip-rotation This causes the cluster to serve on two IPs, and will initiate a node upgrade to point to the new IP. See documentation for more details: https://cloud.google.com/kubernetes-engine/docs/how-to/ip-rotation. |
| `--tier` | one of: standard, enterprise |  | _[Enable vertical pod autoscaling for a cluster.]_ (DEPRECATED) Set the desired tier for the cluster. The --tier flag is deprecated. More info: https://cloud.google.com/kubernetes-engine/docs/release-notes#September_02_2025. TIER must be one of: standard, enterprise. |
| `--update-addons` | [ADDON=ENABLED\|DISABLED,...] |  | _[Enable vertical pod autoscaling for a cluster.]_ Cluster addons to enable or disable. Options are HorizontalPodAutoscaling=ENABLED\|DISABLED HttpLoadBalancing=ENABLED\|DISABLED KubernetesDashboard=ENABLED\|DISABLED NetworkPolicy=ENABLED\|DISABLED BackupRestore=ENABLED\|DISABLED CloudRun=ENABLED\|DISABLED ConfigConnector=ENABLED\|DISABLED NodeLocalDNS=ENABLED\|DISABLED GcePersistentDiskCsiDriver=ENABLED\|DISABLED GcpFilestoreCsiDriver=ENABLED\|DISABLED GcsFuseCsiDriver=ENABLED\|DISABLED |
| `--update-labels` | [KEY=VALUE,...] |  | _[Enable vertical pod autoscaling for a cluster.]_ Labels to apply to the Google Cloud resources in use by the Kubernetes Engine cluster. These are unrelated to Kubernetes labels. Examples: $ gcloud container clusters update example-cluster \ --update-labels=label_a=value1,label_b=value2 |
| `--workload-policies` | WORKLOAD_POLICIES |  | _[Enable vertical pod autoscaling for a cluster.]_ Add Autopilot workload policies to the cluster. Examples: $ gcloud container clusters update example-cluster \ --workload-policies=allow-net-admin The only supported workload policy is 'allow-net-admin'. |
| `--workload-pool` | WORKLOAD_POOL |  | _[Enable vertical pod autoscaling for a cluster.]_ Enable Workload Identity on the cluster. When enabled, Kubernetes service accounts will be able to act as Cloud IAM Service Accounts, through the provided workload pool. Currently, the only accepted workload pool is the workload pool of the Cloud project containing the cluster, PROJECT_ID.svc.id.goog. For more information on Workload Identity, see https://cloud.google.com/kubernetes-engine/docs/how-to/workload-identity |
| `--workload-vulnerability-scanning` | one of: disabled, standard, enterprise |  | _[Enable vertical pod autoscaling for a cluster.]_ Sets the mode of the Kubernetes security posture API's workload vulnerability scanning. To enable Advanced vulnerability insights mode explicitly set the flag to --workload-vulnerability-scanning=enterprise. To enable in standard mode explicitly set the flag to --workload-vulnerability-scanning=standard. To disable in an existing cluster, explicitly set the flag to --workload-vulnerability-scanning=disabled. For more information on enablement, see https://cloud.google.com/kubernetes-engine/docs/concepts/about-security-posture-dashboard#feature-enablement. WORKLOAD_VULNERABILITY_SCANNING must be one of: disabled, standard, enterprise. |
| `--additional-ip-ranges` | [subnetwork=NAME,pod-ipv4-range=NAME,...] |  | _[Enable vertical pod autoscaling for a cluster.]_ Add additional subnetworks named "my-subnet" with pod ipv4 range named "my-range" to the cluster. Examples: $ gcloud container clusters update example-cluster \ --additional-ip-ranges=subnetwork=my-subnet,\ pod-ipv4-range=my-range |
| `--remove-additional-ip-ranges` | [subnetwork=NAME,pod-ipv4-range=NAME,...] |  | _[Enable vertical pod autoscaling for a cluster.]_ Additional subnetworks to be removed from the cluster. Examples: Remove pod range named "my-range" under additional subnetwork named "my-subnet" from the cluster. $ gcloud container clusters update example-cluster \ --remove-additional-ip-ranges=subnetwork=my-subnet,\ pod-ipv4-range=my-range Remove additional subnetwork named "my-subnet", including all the pod ipv4 ranges under the subnetwork. $ gcloud container clusters update example-cluster \ --remove-additional-ip-ranges=subnetwork=my-subnet |
| `--additional-pod-ipv4-ranges` | NAME,[NAME,...] |  | _[Enable vertical pod autoscaling for a cluster.]_ Additional IP address ranges(by name) for pods that need to be added to the cluster. Examples: $ gcloud container clusters update example-cluster \ --additional-pod-ipv4-ranges=range1,range2 |
| `--remove-additional-pod-ipv4-ranges` | NAME,[NAME,...] |  | _[Enable vertical pod autoscaling for a cluster.]_ Previously added additional pod ranges(by name) for pods that are to be removed from the cluster. Examples: $ gcloud container clusters update example-cluster \ --remove-additional-pod-ipv4-ranges=range1,range2 |
| `--auto-monitoring-scope` | one of: ALL, NONE |  | _[Enable vertical pod autoscaling for a cluster.]_ Enables Auto-Monitoring for a specific scope within the cluster. ALL: Enables Auto-Monitoring for all supported workloads within the cluster. NONE: Disables Auto-Monitoring. AUTO_MONITORING_SCOPE must be one of: ALL, NONE. |
| `--logging` | [COMPONENT,...] |  | _[Enable vertical pod autoscaling for a cluster.]_ Set the components that have logging enabled. Valid component values are: SYSTEM, WORKLOAD, API_SERVER, CONTROLLER_MANAGER, SCHEDULER, NONE For more information, see https://cloud.google.com/kubernetes-engine/docs/concepts/about-logs#available-logs Examples: $ gcloud container clusters update --logging=SYSTEM $ gcloud container clusters update \ --logging=SYSTEM,API_SERVER,WORKLOAD $ gcloud container clusters update --logging=NONE |
| `--monitoring` | [COMPONENT,...] |  | _[Enable vertical pod autoscaling for a cluster.]_ Set the components that have monitoring enabled. Valid component values are: SYSTEM, WORKLOAD (Deprecated), NONE, API_SERVER, CONTROLLER_MANAGER, SCHEDULER, DAEMONSET, DEPLOYMENT, HPA, POD, STATEFULSET, STORAGE, CADVISOR, KUBELET, DCGM, JOBSET For more information, see https://cloud.google.com/kubernetes-engine/docs/how-to/configure-metrics#available-metrics Examples: $ gcloud container clusters update --monitoring=SYSTEM,API_SERVER,POD $ gcloud container clusters update --monitoring=NONE |
| `--clear-fleet-project` |  |  | _[--binauthz-evaluation-mode instead.]_ Remove the cluster from current fleet host project. Example: $ gcloud container clusters update --clear-fleet-project |
| `--enable-fleet` |  |  | _[--binauthz-evaluation-mode instead.]_ Set cluster project as the fleet host project. This will register the cluster to the same project. To register the cluster to a fleet in a different project, please use --fleet-project=FLEET_HOST_PROJECT. Example: $ gcloud container clusters update --enable-fleet |
| `--fleet-project` | PROJECT_ID_OR_NUMBER |  | _[--binauthz-evaluation-mode instead.]_ Sets fleet host project for the cluster. If specified, the current cluster will be registered as a fleet membership under the fleet host project. Example: $ gcloud container clusters update --fleet-project=my-project |
| `--membership-type` | MEMBERSHIP_TYPE |  | _[--binauthz-evaluation-mode instead.]_ Specify a membership type for the cluster's fleet membership. Example: $ gcloud container clusters update --membership-type=LIGHTWEIGHT. \ MEMBERSHIP_TYPE must be (only one value is supported): LIGHTWEIGHT Fleet membership representing this cluster will be lightweight. |
| `--unset-membership-type` |  |  | _[--binauthz-evaluation-mode instead.]_ Set the membership type for the cluster's fleet membership to empty. Example: $ gcloud container clusters update --unset-membership-type |
| `--enable-authorized-networks-on-private-endpoint` |  |  | _[reconciliation is enabled by default.]_ Enable enforcement of --master-authorized-networks CIDR ranges for traffic reaching cluster's control plane via private IP. |
| `--enable-dns-access` |  |  | _[reconciliation is enabled by default.]_ Enable access to the cluster's control plane over DNS-based endpoint. DNS-based control plane access is recommended. |
| `--enable-google-cloud-access` |  |  | _[reconciliation is enabled by default.]_ When you enable Google Cloud Access, any public IP addresses owned by Google Cloud can reach the public control plane endpoint of your cluster. |
| `--enable-ip-access` |  |  | _[reconciliation is enabled by default.]_ Enable access to the cluster's control plane over private IP and public IP if --enable-private-endpoint is not enabled. |
| `--enable-k8s-certs-via-dns` |  |  | _[reconciliation is enabled by default.]_ Enable K8s client certificates Authentication to the cluster's control plane over DNS-based endpoint. |
| `--enable-k8s-tokens-via-dns` |  |  | _[reconciliation is enabled by default.]_ Enable K8s Service Account tokens Authentication to the cluster's control plane over DNS-based endpoint. |
| `--enable-master-global-access` |  |  | _[reconciliation is enabled by default.]_ Use with private clusters to allow access to the master's private endpoint from any Google Cloud region or on-premises environment regardless of the private cluster's region. |
| `--enable-private-endpoint` |  |  | _[reconciliation is enabled by default.]_ Enables cluster's control plane to be accessible using private IP address only. |
| `--enable-insecure-binding-system-authenticated` |  |  | _[the cluster can be scaled.]_ Allow using system:authenticated as a subject in ClusterRoleBindings and RoleBindings. Allowing bindings that reference system:authenticated is a security risk and is not recommended. To disallow binding system:authenticated in a cluster, explicitly set the --no-enable-insecure-binding-system-authenticated flag instead. |
| `--enable-insecure-binding-system-unauthenticated` |  |  | _[the cluster can be scaled.]_ Allow using system:unauthenticated and system:anonymous as subjects in ClusterRoleBindings and RoleBindings. Allowing bindings that reference system:unauthenticated and system:anonymous are a security risk and is not recommended. To disallow binding system:authenticated in a cluster, explicitly set the --no-enable-insecure-binding-system-unauthenticated flag instead. |
| `--logging-service` | LOGGING_SERVICE |  | _[the cluster can be scaled.]_ (DEPRECATED) Logging service to use for the cluster. Options are: "logging.googleapis.com/kubernetes" (the Google Cloud Logging service with Kubernetes-native resource model enabled), "logging.googleapis.com" (the Google Cloud Logging service), "none" (logs will not be exported from the cluster) The --logging-service flag is deprecated and will be removed in an upcoming release. Please use --logging instead. For more information, please read: https://cloud.google.com/kubernetes-engine/docs/concepts/about-logs. |
| `--monitoring-service` | MONITORING_SERVICE |  | _[the cluster can be scaled.]_ (DEPRECATED) Monitoring service to use for the cluster. Options are: "monitoring.googleapis.com/kubernetes" (the Google Cloud Monitoring service with Kubernetes-native resource model enabled), "monitoring.googleapis.com" (the Google Cloud Monitoring service), "none" (no metrics will be exported from the cluster) The --monitoring-service flag is deprecated and will be removed in an upcoming release. Please use --monitoring instead. For more information, please read: https://cloud.google.com/kubernetes-engine/docs/how-to/configure-metrics. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--cloud-run-config` | [load-balancer-type=EXTERNAL,...] |  | Configurations for Cloud Run addon, requires --addons=CloudRun for create and --update-addons=CloudRun=ENABLED for update. load-balancer-type (Optional) Type of load-balancer-type EXTERNAL or INTERNAL. Examples: $ gcloud container clusters update example-cluster \ --cloud-run-config=load-balancer-type=INTERNAL |
| `--node-pool` | NODE_POOL |  | Node pool to be updated. |


**Examples:**
```bash
To enable autoscaling for an existing cluster, run:

    $ gcloud container clusters update sample-cluster \
        --enable-autoscaling
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/clusters/update)

---
### `gcloud container clusters upgrade`

Upgrade the Kubernetes version of an existing container cluster

Upgrades the Kubernetes version of an existing container cluster.

This command upgrades the Kubernetes version of the node pools or master of
a cluster. Note that the Kubernetes version of the cluster's master is also
periodically upgraded automatically as new releases are available.

If desired cluster version is omitted, node pool upgrades default to the
current master version and master upgrades default to the default cluster
version, which can be found in the server config.

During node pool upgrades, nodes will be deleted and recreated. While
persistent Kubernetes resources, such as Pods backed by replication
controllers, will be rescheduled onto new nodes, a small cluster may
experience a few minutes where there are insufficient nodes available to
run all of the scheduled Kubernetes resources.

Please ensure that any data you wish to keep is stored on a persistent disk
before upgrading the cluster. Ephemeral Kubernetes resources--in
particular, Pods without replication controllers--will be lost, while
persistent Kubernetes resources will get rescheduled.

**Synopsis:**
```
gcloud container clusters upgrade NAME [--async]
    [--cluster-version=CLUSTER_VERSION] [--image-type=IMAGE_TYPE]
    [--master] [--node-pool=NODE_POOL]
    [--location=LOCATION | --region=REGION | --zone=ZONE, -z ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of the cluster to upgrade.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--cluster-version` | CLUSTER_VERSION |  | The GKE release version to which to upgrade the cluster's node pools or master. If desired cluster version is omitted, node pool upgrades default to the current master version and master upgrades default to the default cluster version, which can be found in the server config. You can find the list of allowed versions for upgrades by running: $ gcloud container get-server-config |
| `--image-type` | IMAGE_TYPE |  | The image type to use for the cluster/node pool. Defaults to server-specified. Image Type specifies the base OS that the nodes in the cluster/node pool will run on. If an image type is specified, that will be assigned to the cluster/node pool and all future upgrades will use the specified image type. If it is not specified the server will pick the default image type. The default image type and the list of valid image types are available using the following command. $ gcloud container get-server-config |
| `--master` |  |  | Upgrade the cluster's master. Node pools cannot be upgraded at the same time as the master. |
| `--node-pool` | NODE_POOL |  | The node pool to upgrade. |


**Examples:**
```bash
Upgrade the node pool pool-1 of sample-cluster to the Kubernetes version of
the cluster's master.

    $ gcloud container clusters upgrade sample-cluster --node-pool=pool-1

Upgrade the node pool pool-1 of sample-cluster to Kubernetes version
1.14.7-gke.14:

    $ gcloud container clusters upgrade sample-cluster \
        --node-pool=pool-1 --cluster-version="1.14.7-gke.14"

Upgrade the master of sample-cluster to the default cluster version:

    $ gcloud container clusters upgrade sample-cluster --master
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/clusters/upgrade)

---
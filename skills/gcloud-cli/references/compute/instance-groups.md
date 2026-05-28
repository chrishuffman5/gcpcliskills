# gcloud compute instance-groups

read and manipulate Compute Engine instance groups

### `gcloud compute instance-groups describe`

Display detailed information about an instance group

gcloud compute instance-groups describe displays all data associated with
an instance group in a project.

**Synopsis:**
```
gcloud compute instance-groups describe NAME
    [--region=REGION | --zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the instance group to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the instance group to describe. If not specified, you might be prompted to select a region (interactive mode only). A list of regions can be fetched by running: $ gcloud compute regions list Overrides the default compute/region property value for this command invocation. |
| `--zone` | ZONE |  | _[At most one of these can be specified:]_ Zone of the instance group to describe. If not specified, you might be prompted to select a zone (interactive mode only). A list of zones can be fetched by running: $ gcloud compute zones list Overrides the default compute/zone property value for this command invocation. |


**Examples:**
```bash
To get details about a regional instance group in the us-central1 regions,
run:

    $ gcloud compute instance-groups describe --region=us-central1

To get details about a zonal instance group in the us-central1-b zone, run:

    $ gcloud compute instance-groups describe --zone=us-central1-b
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/describe)

---
### `gcloud compute instance-groups get-named-ports`

Lists the named ports for an instance group resource

Named ports are key:value pairs metadata representing the service name and
the port that it's running on. Named ports can be assigned to an instance
group, which indicates that the service is available on all instances in
the group. This information is used by Application Load Balancers and proxy
Network Load Balancers.

gcloud compute instance-groups get-named-ports lists the named ports (name
and port tuples) for an instance group.

**Synopsis:**
```
gcloud compute instance-groups get-named-ports NAME
    [--region=REGION | --zone=ZONE] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the instance group to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the instance group to operate on. If not specified, you might be prompted to select a region (interactive mode only). A list of regions can be fetched by running: $ gcloud compute regions list Overrides the default compute/region property value for this command invocation. |
| `--zone` | ZONE |  | _[At most one of these can be specified:]_ Zone of the instance group to operate on. If not specified, you might be prompted to select a zone (interactive mode only). A list of zones can be fetched by running: $ gcloud compute zones list Overrides the default compute/zone property value for this command invocation. |


**Examples:**
```bash
For example, to list named ports for an instance group:

    $ gcloud compute instance-groups get-named-ports \
        example-instance-group --zone=us-central1-a

The above example lists named ports assigned to an instance group named
'example-instance-group' in the us-central1-a zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/get-named-ports)

---
### `gcloud compute instance-groups list`

List Google Compute Engine instance groups

gcloud compute instance-groups list displays all Google Compute Engine
instance groups in a project.

By default, instance groups from all regions and instance groups from all
zones are listed. The results can be narrowed down by providing the
--regions or --zones flag.

**Synopsis:**
```
gcloud compute instance-groups list [NAME ...] [--regexp=REGEXP, -r REGEXP]
    [--only-managed | --only-unmanaged]
    [--regions=[REGION,...] | --zones=[ZONE,...]] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
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


**Examples:**
```bash
To list all instance groups in a project in table form, run:

    $ gcloud compute instance-groups list

To list the URIs of all instance groups in a project, run:

    $ gcloud compute instance-groups list --uri

To list all instance groups in the us-central1 and europe-west1 regions,
given they are regional resources, run:

    $ gcloud compute instance-groups list \
        --filter="region:( europe-west1 us-central1 )"

To list all instance groups in zones us-central1-b and europe-west1-d,
given they are zonal resources, run:

    $ gcloud compute instance-groups list \
        --filter="zone:( europe-west1-d us-central1-b )"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/list)

---
### `gcloud compute instance-groups list-instances`

List instances present in the instance group

gcloud compute instance-groups list-instances list instances in an instance
group.

The required permission to execute this command is
compute.instanceGroups.list. If needed, you can include this permission, or
choose any of the following preexisting IAM roles that contain this
particular permission:

  o Compute Admin
  o Compute Viewer
  o Compute Instance Admin (v1)
  o Compute Instance Admin (beta)
  o Compute Network Admin
  o Compute Network Viewer
  o Editor
  o Owner
  o Security Reviewer
  o Viewer

For more information regarding permissions required by instance groups,
refer to Compute Engine's access control guide:
https://cloud.google.com/compute/docs/access/iam.

**Synopsis:**
```
gcloud compute instance-groups list-instances NAME
    [--regexp=REGEXP, -r REGEXP] [--region=REGION | --zone=ZONE]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the instance group to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--regexp` | REGEXP, -r REGEXP |  | A regular expression to filter the names of the results on. Any names that do not match the entire regular expression will be filtered out. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/list-instances)

---
### `gcloud compute instance-groups set-named-ports`

Sets the list of named ports for an instance group

Named ports are key:value pairs metadata representing the service name and
the port that it's running on. Named ports can be assigned to an instance
group, which indicates that the service is available on all instances in
the group. This information is used by Application Load Balancers and proxy
Network Load Balancers.

gcloud compute instance-groups set-named-ports sets the list of named ports
for all instances in an instance group.

Note: Running this command will clear all existing named ports.

**Synopsis:**
```
gcloud compute instance-groups set-named-ports NAME
    --named-ports=[NAME:PORT,...] [--region=REGION | --zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the instance group to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--named-ports` | [NAME:PORT,...] |  | The comma-separated list of key:value pairs representing the service name and the port that it is running on. To clear the list of named ports pass empty list as flag value. For example: $ gcloud compute instance-groups set-named-ports \ example-instance-group --named-ports "" |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the instance group to operate on. If not specified, you might be prompted to select a region (interactive mode only). A list of regions can be fetched by running: $ gcloud compute regions list Overrides the default compute/region property value for this command invocation. |
| `--zone` | ZONE |  | _[At most one of these can be specified:]_ Zone of the instance group to operate on. If not specified, you might be prompted to select a zone (interactive mode only). A list of zones can be fetched by running: $ gcloud compute zones list Overrides the default compute/zone property value for this command invocation. |


**Examples:**
```bash
For example, to apply the named ports to an entire instance group:

    $ gcloud compute instance-groups set-named-ports \
        example-instance-group --named-ports=example-service:1111 \
        --zone=us-central1-a

The above example will assign a name 'example-service' for port 1111 to the
instance group called 'example-instance-group' in the us-central1-a zone.
The command removes any named ports that are already set for this instance
group.

To clear named ports from instance group provide empty named ports list as
parameter:

    $ gcloud compute instance-groups set-named-ports \
        example-instance-group --named-ports="" --zone=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/set-named-ports)

---

## `gcloud compute instance-groups managed` — read and manipulate Compute Engine managed instance groups
### `gcloud compute instance-groups managed abandon-instances`

Abandon instances owned by a managed instance group

gcloud compute instance-groups managed abandon-instances abandons one or
more instances from a managed instance group, thereby reducing the
targetSize of the group. Once instances have been abandoned, the
currentSize of the group is automatically reduced as well to reflect the
change.

Abandoning an instance does not reboot or delete the underlying virtual
machine instances, but just removes the instances from the instance group.
If you would like to delete the underlying instances, use the
delete-instances command instead.

The command returns the operation status per instance, which might be FAIL,
SUCCESS, or MEMBER_NOT_FOUND. MEMBER_NOT_FOUND is returned only for
regional groups when the gcloud command-line tool wasn't able to resolve
the zone from the instance name.

For a more detailed overview of how abandoning instances from a managed
instance group works, see Abandoning instances from a MIG
(https://cloud.google.com/compute/docs/instance-groups/add-remove-vms-in-mig#abandoning_instances).

**Synopsis:**
```
gcloud compute instance-groups managed abandon-instances NAME
    --instances=INSTANCE,[INSTANCE,...] [--region=REGION | --zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the managed instance group to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instances` | INSTANCE,[INSTANCE,...] |  | Names of instances to abandon. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the managed instance group to operate on. If not specified, you might be prompted to select a region (interactive mode only). A list of regions can be fetched by running: $ gcloud compute regions list Overrides the default compute/region property value for this command invocation. |
| `--zone` | ZONE |  | _[At most one of these can be specified:]_ Zone of the managed instance group to operate on. If not specified, you might be prompted to select a zone (interactive mode only). A list of zones can be fetched by running: $ gcloud compute zones list Overrides the default compute/zone property value for this command invocation. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/abandon-instances)

---
### `gcloud compute instance-groups managed create`

Create a Compute Engine managed instance group

gcloud compute instance-groups managed create creates a Compute Engine
managed instance group.

**Synopsis:**
```
gcloud compute instance-groups managed create NAME --size=SIZE
    --template=TEMPLATE [--base-instance-name=BASE_INSTANCE_NAME]
    [--default-action-on-vm-failure=ACTION_ON_VM_FAILURE]
    [--description=DESCRIPTION] [--[no-]force-update-on-repair]
    [--initial-delay=INITIAL_DELAY] [--instance-redistribution-type=TYPE]
    [--instance-selection=name=NAME,
      machine-type=MACHINE_TYPE[,machine-type=MACHINE_TYPE...][,rank=RANK]]
    [--instance-selection-machine-types=[MACHINE_TYPE,...]]
    [--list-managed-instances-results=MODE]
    [--standby-policy-initial-delay=STANDBY_POLICY_INITIAL_DELAY]
    [--standby-policy-mode=STANDBY_POLICY_MODE]
    [--stateful-disk=[auto-delete=AUTO-DELETE],[device-name=DEVICE-NAME]]
    [--stateful-external-ip=[enabled],
      [auto-delete=AUTO-DELETE],[interface-name=INTERFACE-NAME]]
    [--stateful-internal-ip=[enabled],
      [auto-delete=AUTO-DELETE],[interface-name=INTERFACE-NAME]]
    [--stopped-size=STOPPED_SIZE] [--suspended-size=SUSPENDED_SIZE]
    [--target-distribution-shape=SHAPE] [--target-pool=[TARGET_POOL,...]]
    [--workload-policy=WORKLOAD_POLICY] [--zones=ZONE,[ZONE,...]]
    [--health-check=HEALTH_CHECK | --http-health-check=HTTP_HEALTH_CHECK
      | --https-health-check=HTTPS_HEALTH_CHECK]
    [--region=REGION | --zone=ZONE]
    [--update-policy-max-surge=MAX_SURGE
      --update-policy-max-unavailable=MAX_UNAVAILABLE
      --update-policy-minimal-action=UPDATE_POLICY_MINIMAL_ACTION
      --update-policy-most-disruptive-action=UPDATE_POLICY_MOST_DISRUPTIVE_ACTION --update-policy-replacement-method=UPDATE_POLICY_REPLACEMENT_METHOD --update-policy-type=UPDATE_TYPE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the managed instance group to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--size` | SIZE |  | Initial number of instances you want in this group. |
| `--template` | TEMPLATE |  | Specifies the instance template to use when creating new instances. An instance template is either a global or regional resource. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--base-instance-name` | BASE_INSTANCE_NAME |  | Base name to use for the Compute Engine instances that will be created with the managed instance group. If not provided base instance name will be the prefix of instance group name. |
| `--default-action-on-vm-failure` | one of: do-nothing MIG does not repair a failed or an unhealthy VM |  | Specifies the action that a MIG performs on a failed or an unhealthy VM. A VM is marked as unhealthy when the application running on that VM fails a health check. By default, the value of the flag is set to repair. ACTION_ON_VM_FAILURE must be one of: do-nothing MIG does not repair a failed or an unhealthy VM. repair MIG automatically repairs a failed or an unhealthy VM. |
| `--description` | DESCRIPTION |  | An optional description for this group. |
| `--[no-]force-update-on-repair` |  |  | Specifies whether to apply the group's latest configuration when repairing a VM. If you updated the group's instance template or per-instance configurations after the VM was created, then these changes are applied when VM is repaired. If this flag is disabled with -no-force-update-on-repair, then updates are applied in accordance with the group's update policy type. By default, this flag is disabled. Use --force-update-on-repair to enable and --no-force-update-on-repair to disable. |
| `--initial-delay` | INITIAL_DELAY |  | Specifies the number of seconds that a new VM takes to initialize and run its startup script. During a VM's initial delay period, the MIG ignores unsuccessful health checks because the VM might be in the startup process. This prevents the MIG from prematurely recreating a VM. If the health check receives a healthy response during the initial delay, it indicates that the startup process is complete and the VM is ready. The value of initial delay must be between 0 and 3600 seconds. The default value is 0. See $ gcloud topic datetimes for information on duration formats. |
| `--instance-redistribution-type` | one of: none The managed instance group does not redistribute instances across zones |  | Specifies the type of the instance redistribution policy. An instance redistribution type lets you enable or disable automatic instance redistribution across zones to meet the group's target distribution shape. An instance redistribution type can be specified only for a non-autoscaled regional managed instance group. By default it is set to proactive. TYPE must be one of: none The managed instance group does not redistribute instances across zones. proactive The managed instance group proactively redistributes instances to meet its target distribution. |
| `--instance-selection` | name=NAME,machine-type=MACHINE_TYPE[,machine-type=MACHINE_TYPE...][,rank=RANK] |  | Named selection of machine types with an optional rank. For example, --instance-selection="name=instance-selection-1,machine-type=e2-standard-8,machine-type=t2d-standard-8,rank=0" |
| `--instance-selection-machine-types` | [MACHINE_TYPE,...] |  | Machine types that are used to create VMs in the managed instance group. If not provided, the machine type specified in the instance template is used. |
| `--list-managed-instances-results` | one of: pageless Pagination is disabled for the group's listManagedInstances API method |  | Pagination behavior for the group's listManagedInstances API method. This flag does not affect the group's gcloud or console list-instances behavior. By default it is set to pageless. MODE must be one of: pageless Pagination is disabled for the group's listManagedInstances API method. maxResults and pageToken query parameters are ignored and all instances are returned in a single response. paginated Pagination is enabled for the group's listManagedInstances API method. maxResults and pageToken query parameters are respected. |
| `--standby-policy-initial-delay` | STANDBY_POLICY_INITIAL_DELAY |  | Specifies the number of seconds that the MIG should wait before suspending or stopping a VM. The initial delay gives the initialization script the time to prepare your VM for a quick scale out. |
| `--standby-policy-mode` | one of: manual MIG does not automatically resume or start VMs in the standby pool when the group scales out |  | Defines how a MIG resumes or starts VMs from a standby pool when the group scales out. The default mode is manual. STANDBY_POLICY_MODE must be one of: manual MIG does not automatically resume or start VMs in the standby pool when the group scales out. scale-out-pool MIG automatically resumes or starts VMs in the standby pool when the group scales out, and replenishes the standby pool afterwards. |
| `--stateful-disk` | [auto-delete=AUTO-DELETE],[device-name=DEVICE-NAME] |  | Disks considered stateful by the instance group. Managed instance groups preserve and reattach stateful disks on VM autohealing, update, and recreate events. Use this argument multiple times to attach more disks. device-name (Required) Device name of the disk to mark stateful. auto-delete (Optional) Specifies the auto deletion policy of the stateful disk. The following options are available: + never: (Default) Never delete this disk. Instead, detach the disk when its instance is deleted. + on-permanent-instance-deletion: Delete the stateful disk when the instance that it's attached to is permanently deleted from the group; for example, when the instance is deleted manually or when the group size is decreased. |
| `--stateful-external-ip` | [enabled],[auto-delete=AUTO-DELETE],[interface-name=INTERFACE-NAME] |  | External IPs considered stateful by the instance group. Managed instance groups preserve stateful IPs on VM autohealing, update, and recreate events. Use this argument multiple times to make more external IPs stateful. At least one of the following is required: enabled Marks the IP address as stateful. The network interface named nic0 is assumed by default when interface-name is not specified. This flag can be omitted when interface-name is provided explicitly. interface-name Marks the IP address from this network interface as stateful. This flag can be omitted when enabled is provided. Additional arguments: auto-delete (Optional) Prescribes what should happen to an associated static Address resource when a VM instance is permanently deleted. Regardless of the value of the delete rule, stateful IP addresses are always preserved on instance autohealing, update, and recreation operations. The following options are available: + never: (Default) Never delete the static IP address. Instead, unassign the address when its instance is permanently deleted and keep the address reserved. + on-permanent-instance-deletion: Delete the static IP address reservation when the instance that it's assigned to is permanently deleted from the instance group; for example, when the instance is deleted manually or when the group size is decreased. |
| `--stateful-internal-ip` | [enabled],[auto-delete=AUTO-DELETE],[interface-name=INTERFACE-NAME] |  | Internal IPs considered stateful by the instance group. Managed instance groups preserve stateful IPs on VM autohealing, update, and recreate events. Use this argument multiple times to make more internal IPs stateful. At least one of the following is required: enabled Marks the IP address as stateful. The network interface named nic0 is assumed by default when interface-name is not specified. This flag can be omitted when interface-name is provided explicitly. interface-name Marks the IP address from this network interface as stateful. This flag can be omitted when enabled is provided. Additional arguments: auto-delete (Optional) Prescribes what should happen to an associated static Address resource when a VM instance is permanently deleted. Regardless of the value of the delete rule, stateful IP addresses are always preserved on instance autohealing, update, and recreation operations. The following options are available: + never: (Default) Never delete the static IP address. Instead, unassign the address when its instance is permanently deleted and keep the address reserved. + on-permanent-instance-deletion: Delete the static IP address reservation when the instance that it's assigned to is permanently deleted from the instance group; for example, when the instance is deleted manually or when the group size is decreased. |
| `--stopped-size` | STOPPED_SIZE |  | Specifies the target size of stopped VMs in the group. |
| `--suspended-size` | SUSPENDED_SIZE |  | Specifies the target size of suspended VMs in the group. |
| `--target-distribution-shape` | one of: any The group picks zones for creating VM instances to fulfill the requested number of VMs within present resource constraints and to maximize utilization of unused zonal reservations |  | Specifies how a regional managed instance group distributes its instances across zones within the region. The default shape is even. SHAPE must be one of: any The group picks zones for creating VM instances to fulfill the requested number of VMs within present resource constraints and to maximize utilization of unused zonal reservations. Recommended for batch workloads that do not require high availability. any-single-zone The group schedules all instances within a single zone. The zone is chosen based on hardware support, current resources availability, and matching reservations. The group might not be able to create the requested number of VMs in case of zonal resource availability constraints. Recommended for workloads requiring extensive communication between VMs. balanced The group prioritizes acquisition of resources, scheduling VMs in zones where resources are available while distributing VMs as evenly as possible across selected zones to minimize the impact of zonal failure. Recommended for highly available serving or batch workloads that do not require autoscaling. even The group schedules VM instance creation and deletion to achieve and maintain an even number of managed instances across the selected zones. The distribution is even when the number of managed instances does not differ by more than 1 between any two zones. Recommended for highly available serving workloads. |
| `--target-pool` | [TARGET_POOL,...] |  | Specifies any target pools you want the instances of this managed instance group to be part of. |
| `--workload-policy` | WORKLOAD_POLICY |  | Specifies the workload policy for the managed instance group. It can be a full or partial URL to a resource policy containing the workload policy. |
| `--zones` | ZONE,[ZONE,...] |  | If this flag is specified a regional managed instance group will be created. The managed instance group will be in the same region as specified zones and will spread instances in it between specified zones. All zones must belong to the same region. You may specify --region flag but it must be the region to which zones belong. This flag is mutually exclusive with --zone flag. |


**Examples:**
```bash
Running:

    $ gcloud compute instance-groups managed create \
    example-managed-instance-group --zone=us-central1-a \
    --template=example-global-instance-template --size=1

will create a managed instance group called
'example-managed-instance-group' in the us-central1-a zone with a global
instance template resource 'example-global-instance-template'.

To use a regional instance template, specify the full or partial URL of the
template.

Running:

    $ gcloud compute instance-groups managed create \
    example-managed-instance-group --zone=us-central1-a \
    --template=projects/example-project/regions/us-central1/\
    instanceTemplates/example-regional-instance-template --size=1

will create a managed instance group called
'example-managed-instance-group' in the us-central1-a zone with a regional
instance template resource 'example-regional-instance-template'.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/create)

---
### `gcloud compute instance-groups managed create-instance`

Create a new virtual machine instance in a managed instance group with a defined name and optionally its stateful configuration

gcloud compute instance-groups managed create-instance creates a virtual
machine instance with a defined name and optionally its stateful
configuration: stateful disk, stateful metadata key-values, and stateful IP
addresses. Stateful configuration is stored in the corresponding newly
created per-instance config. An instance with a per-instance config will
preserve its given name, specified disks, specified metadata key-values,
and specified internal and external IPs during instance recreation,
auto-healing, updates, and any other lifecycle transitions of the instance.

**Synopsis:**
```
gcloud compute instance-groups managed create-instance NAME
    --instance=INSTANCE
    [--stateful-disk=[auto-delete=AUTO-DELETE],
      [device-name=DEVICE-NAME],[mode=MODE],[source=SOURCE]]
    [--stateful-external-ip=[address=ADDRESS],
      [auto-delete=AUTO-DELETE],[interface-name=INTERFACE-NAME]]
    [--stateful-internal-ip=[address=ADDRESS],
      [auto-delete=AUTO-DELETE],[interface-name=INTERFACE-NAME]]
    [--stateful-metadata=KEY=VALUE,[KEY=VALUE,...]]
    [--region=REGION | --zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the managed instance group to create instance in.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE |  | Name of the new instance to create. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--stateful-disk` | [auto-delete=AUTO-DELETE],[device-name=DEVICE-NAME],[mode=MODE],[source=SOURCE] |  | Disks considered stateful by the instance group. Managed instance groups preserve and reattach stateful disks on VM autohealing, update, and recreate events. You can also attach and preserve disks, not defined in the group's instance template, to a given instance. The same disk can be attached to more than one instance but only in read-only mode. |
| `--stateful-external-ip` | [address=ADDRESS],[auto-delete=AUTO-DELETE],[interface-name=INTERFACE-NAME] |  | Managed instance groups preserve stateful IPs on VM autohealing, update, and recreate events. Use this argument multiple times to update more IPs. If a stateful external IP with the given interface name already exists in the current instance configuration, its properties are replaced by the newly provided ones. Otherwise, a new stateful external IP definition is added to the instance configuration. interface-name (Optional) Network interface name. If omitted, the default network interface named nic0 is assumed. *address*::: Static IP address to assign to the instance in one of the following formats: + Address: URL of a static IP address reservation. For example: projects/example-project/regions/us-east1/addresses/example-ip-name. + Literal: For example: 130.211.181.55. If the provided IP address is not yet reserved, the managed instance group automatically creates the corresponding IP address reservation. If the provided IP address is reserved, the group assigns the reservation to the instance. auto-delete (Optional) Prescribes what should happen to an associated static Address resource when a VM instance is permanently deleted. Regardless of the value of the delete rule, stateful IP addresses are always preserved on instance autohealing, update, and recreation operations. The following options are available: + never: (Default) Never delete the static IP address. Instead, unassign the address when its instance is permanently deleted and keep the address reserved. + on-permanent-instance-deletion: Delete the static IP address reservation when the instance that it's assigned to is permanently deleted from the instance group; for example, when the instance is deleted manually or when the group size is decreased. |
| `--stateful-internal-ip` | [address=ADDRESS],[auto-delete=AUTO-DELETE],[interface-name=INTERFACE-NAME] |  | Managed instance groups preserve stateful IPs on VM autohealing, update, and recreate events. Use this argument multiple times to update more IPs. If a stateful internal IP with the given interface name already exists in the current instance configuration, its properties are replaced by the newly provided ones. Otherwise, a new stateful internal IP definition is added to the instance configuration. interface-name (Optional) Network interface name. If omitted, the default network interface named nic0 is assumed. *address*::: Static IP address to assign to the instance in one of the following formats: + Address: URL of a static IP address reservation. For example: projects/example-project/regions/us-east1/addresses/example-ip-name. + Literal: For example: 130.211.181.55. If the provided IP address is not yet reserved, the managed instance group automatically creates the corresponding IP address reservation. If the provided IP address is reserved, the group assigns the reservation to the instance. auto-delete (Optional) Prescribes what should happen to an associated static Address resource when a VM instance is permanently deleted. Regardless of the value of the delete rule, stateful IP addresses are always preserved on instance autohealing, update, and recreation operations. The following options are available: + never: (Default) Never delete the static IP address. Instead, unassign the address when its instance is permanently deleted and keep the address reserved. + on-permanent-instance-deletion: Delete the static IP address reservation when the instance that it's assigned to is permanently deleted from the instance group; for example, when the instance is deleted manually or when the group size is decreased. |
| `--stateful-metadata` | KEY=VALUE,[KEY=VALUE,...] |  | Additional metadata to be made available to the guest operating system in addition to the metadata defined in the instance template. Stateful metadata may be used to define a key/value pair specific for the one given instance to differentiate it from the other instances in the managed instance group. Stateful metadata key/value pairs are preserved on instance recreation, autohealing, updates, and any other lifecycle transitions of the instance. Stateful metadata have priority over the metadata defined in the instance template. This means that stateful metadata that is defined for a key that already exists in the instance template overrides the instance template value. Each metadata entry is a key/value pair separated by an equals sign. Metadata keys must be unique and less than 128 bytes in length. Multiple entries can be passed to this flag, e.g., --stateful-metadata key-1=value-1,key-2=value-2,key-3=value-3. |


**Examples:**
```bash
To create an instance instance-1 in my-group (in region europe-west4) with
metadata my-key: my-value, a disk disk-1 attached to it as the device
device-1, stateful internal IP 192.168.0.10 on the default interface
(nic0), and existing address reservation my-address for stateful external
IP on interface nic1, run:

    $ gcloud compute instance-groups managed create-instance my-group \
      --region=europe-west4 --instance=instance-1 \
      --stateful-disk='device-name=foo,source=https://compute.googleap\
    is.com/compute/alpha/projects/my-project/zones/europe-west4/disks/di\
    sk-1,mode=rw,auto-delete=on-permanent-instance-deletion' \
        --stateful-metadata='my-key=my-value' \
        --stateful-internal-ip=address=192.168.0.10,\
    auto-delete=on-permanent-instance-deletion \
        --stateful-external-ip=address=/projects/example-project/\
    regions/europe-west4/addresses/my-address,interface-name=nic1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/create-instance)

---
### `gcloud compute instance-groups managed delete`

Delete Compute Engine managed instance groups

gcloud compute instance-groups managed delete deletes one or more Compute
Engine managed instance groups.

**Synopsis:**
```
gcloud compute instance-groups managed delete NAMES [NAMES ...]
    [--region=REGION | --zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAMES [NAMES ...]
   Names of the managed instance groups to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the managed instance groups to delete. If not specified, you might be prompted to select a region (interactive mode only). A list of regions can be fetched by running: $ gcloud compute regions list Overrides the default compute/region property value for this command invocation. |
| `--zone` | ZONE |  | _[At most one of these can be specified:]_ Zone of the managed instance groups to delete. If not specified, you might be prompted to select a zone (interactive mode only). A list of zones can be fetched by running: $ gcloud compute zones list Overrides the default compute/zone property value for this command invocation. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/delete)

---
### `gcloud compute instance-groups managed delete-instances`

Delete instances that are managed by a managed instance group

gcloud compute instance-groups managed delete-instances is used to delete
one or more instances from a managed instance group. Once the instances are
deleted, the size of the group is automatically reduced to reflect the
changes.

The command returns the operation status per instance, which might be FAIL,
SUCCESS, SKIPPED, or MEMBER_NOT_FOUND. MEMBER_NOT_FOUND is returned only
for regional groups when the gcloud command-line tool wasn't able to
resolve the zone from the instance name. SKIPPED is returned only when the
--skip-instances-on-validation-error flag is used and the instance is not a
member of the group or is already being deleted or abandoned.

If you want to keep the underlying virtual machines but still remove them
from the managed instance group, use the abandon-instances command instead.

**Synopsis:**
```
gcloud compute instance-groups managed delete-instances NAME
    --instances=INSTANCE,[INSTANCE,...]
    [--skip-instances-on-validation-error] [--region=REGION | --zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the managed instance group to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instances` | INSTANCE,[INSTANCE,...] |  | Names of instances to delete. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--skip-instances-on-validation-error` |  |  | Specifies whether the request should proceed even if the request includes instances that are not members of the group or that are already being deleted or abandoned. By default, if you omit this flag and such an instance is specified in the request, the operation fails. The operation always fails if the request contains a badly formatted instance name or a reference to an instance that exists in a zone or region other than the group's zone or region. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/delete-instances)

---
### `gcloud compute instance-groups managed describe`

Display detailed information about an instance group

gcloud compute instance-groups managed describe displays all data
associated with an instance group in a project.

**Synopsis:**
```
gcloud compute instance-groups managed describe NAME
    [--region=REGION | --zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the managed instance group to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the managed instance group to describe. If not specified, you might be prompted to select a region (interactive mode only). A list of regions can be fetched by running: $ gcloud compute regions list Overrides the default compute/region property value for this command invocation. |
| `--zone` | ZONE |  | _[At most one of these can be specified:]_ Zone of the managed instance group to describe. If not specified, you might be prompted to select a zone (interactive mode only). A list of zones can be fetched by running: $ gcloud compute zones list Overrides the default compute/zone property value for this command invocation. |


**Examples:**
```bash
To get details about a regional instance group in the us-central1 regions,
run:

    $ gcloud compute instance-groups managed describe \
        --region=us-central1

To get details about a zonal instance group in the us-central1-b zone, run:

    $ gcloud compute instance-groups managed describe \
        --zone=us-central1-b
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/describe)

---
### `gcloud compute instance-groups managed describe-instance`

Describe an instance in a managed instance group

gcloud compute instance-groups managed describe-instance describes an
instance in a managed instance group, listing all its attributes in YAML
format.

**Synopsis:**
```
gcloud compute instance-groups managed describe-instance NAME
    --instance=INSTANCE [--region=REGION | --zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the managed instance group to describe an instance in.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE |  | Name of the managed instance to describe. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the managed instance group to describe an instance in. If not specified, you might be prompted to select a region (interactive mode only). A list of regions can be fetched by running: $ gcloud compute regions list Overrides the default compute/region property value for this command invocation. |
| `--zone` | ZONE |  | _[At most one of these can be specified:]_ Zone of the managed instance group to describe an instance in. If not specified, you might be prompted to select a zone (interactive mode only). A list of zones can be fetched by running: $ gcloud compute zones list Overrides the default compute/zone property value for this command invocation. |


**Examples:**
```bash
To describe an instance instance-1 in my-group (in region europe-west4),
run:

    $ gcloud compute instance-groups managed describe-instance \
      my-group --instance=instance-1 --region=europe-west4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/describe-instance)

---
### `gcloud compute instance-groups managed get-named-ports`

Lists the named ports for an instance group resource

Named ports are key:value pairs metadata representing the service name and
the port that it's running on. Named ports can be assigned to an instance
group, which indicates that the service is available on all instances in
the group. This information is used by Application Load Balancers and proxy
Network Load Balancers.

gcloud compute instance-groups managed get-named-ports lists the named
ports (name and port tuples) for an instance group.

**Synopsis:**
```
gcloud compute instance-groups managed get-named-ports NAME
    [--region=REGION | --zone=ZONE] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the instance group to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the instance group to operate on. If not specified, you might be prompted to select a region (interactive mode only). A list of regions can be fetched by running: $ gcloud compute regions list Overrides the default compute/region property value for this command invocation. |
| `--zone` | ZONE |  | _[At most one of these can be specified:]_ Zone of the instance group to operate on. If not specified, you might be prompted to select a zone (interactive mode only). A list of zones can be fetched by running: $ gcloud compute zones list Overrides the default compute/zone property value for this command invocation. |


**Examples:**
```bash
For example, to list named ports for an instance group:

    $ gcloud compute instance-groups managed get-named-ports \
        example-instance-group --zone=us-central1-a

The above example lists named ports assigned to an instance group named
'example-instance-group' in the us-central1-a zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/get-named-ports)

---
### `gcloud compute instance-groups managed list`

List Google Compute Engine managed instance groups

gcloud compute instance-groups managed list displays all Google Compute
Engine managed instance groups in a project.

By default, managed instance groups from all regions and managed instance
groups from all zones are listed. The results can be narrowed down by
providing the --regions or --zones flag.

**Synopsis:**
```
gcloud compute instance-groups managed list [NAME ...]
    [--regexp=REGEXP, -r REGEXP]
    [--regions=[REGION,...] | --zones=[ZONE,...]] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
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


**Examples:**
```bash
To list all managed instance groups in a project in table form, run:

    $ gcloud compute instance-groups managed list

To list the URIs of all managed instance groups in a project, run:

    $ gcloud compute instance-groups managed list --uri

To list all managed instance groups in the us-central1 and europe-west1
regions, given they are regional resources, run:

    $ gcloud compute instance-groups managed list \
        --filter="region:( europe-west1 us-central1 )"

To list all managed instance groups in zones us-central1-b and
europe-west1-d, given they are zonal resources, run:

    $ gcloud compute instance-groups managed list \
        --filter="zone:( europe-west1-d us-central1-b )"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/list)

---
### `gcloud compute instance-groups managed list-errors`

List errors produced by managed instances in a managed instance group

gcloud compute instance-groups managed list-errors List errors that are
produced by managed instances in a managed instance group.

The required permission to execute this command is
compute.instanceGroupManagers.list. If needed, you can include this
permission in a custom IAM role, or choose any of the following preexisting
IAM roles that contain this particular permission:

  o Compute Admin
  o Compute Viewer
  o Compute Instance Admin (v1)
  o Compute Instance Admin (beta)
  o Compute Network Admin
  o Editor
  o Owner
  o Security Reviewer
  o Viewer

For more information regarding permissions required by managed instance
groups, refer to Compute Engine's access control guide:
https://cloud.google.com/compute/docs/access/iam#managed-instance-groups-and-iam.

**Synopsis:**
```
gcloud compute instance-groups managed list-errors NAME
    [--region=REGION | --zone=ZONE] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the managed instance group to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the managed instance group to operate on. If not specified, you might be prompted to select a region (interactive mode only). A list of regions can be fetched by running: $ gcloud compute regions list Overrides the default compute/region property value for this command invocation. |
| `--zone` | ZONE |  | _[At most one of these can be specified:]_ Zone of the managed instance group to operate on. If not specified, you might be prompted to select a zone (interactive mode only). A list of zones can be fetched by running: $ gcloud compute zones list Overrides the default compute/zone property value for this command invocation. |


**Examples:**
```bash
To list errors on managed instance group 'my-group', run:

    $ gcloud compute instance-groups managed list-errors my-group \
      --format=yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/list-errors)

---
### `gcloud compute instance-groups managed list-instances`

List instances present in the managed instance group

gcloud compute instance-groups managed list-instances lists instances in a
managed instance group.

The required permission to execute this command is
compute.instanceGroupManagers.list. If needed, you can include this
permission, or choose any of the following preexisting IAM roles that
contain this particular permission:

  o Compute Admin
  o Compute Viewer
  o Compute Instance Admin (v1)
  o Compute Instance Admin (beta)
  o Compute Network Admin
  o Editor
  o Owner
  o Security Reviewer
  o Viewer

For more information regarding permissions required by managed instance
groups, refer to Compute Engine's access control guide :
https://cloud.google.com/compute/docs/access/iam#managed-instance-groups-and-iam.

**Synopsis:**
```
gcloud compute instance-groups managed list-instances NAME
    [--region=REGION | --zone=ZONE] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the managed instance group to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the managed instance group to operate on. If not specified, you might be prompted to select a region (interactive mode only). A list of regions can be fetched by running: $ gcloud compute regions list Overrides the default compute/region property value for this command invocation. |
| `--zone` | ZONE |  | _[At most one of these can be specified:]_ Zone of the managed instance group to operate on. If not specified, you might be prompted to select a zone (interactive mode only). A list of zones can be fetched by running: $ gcloud compute zones list Overrides the default compute/zone property value for this command invocation. |


**Examples:**
```bash
To see additional details about the instances in a managed instance group
my-group, including per-instance overrides, run:

    $ gcloud compute instance-groups managed list-instances my-group \
      --format=yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/list-instances)

---
### `gcloud compute instance-groups managed recreate-instances`

Recreate instances managed by a managed instance group

gcloud compute instance-groups managed recreate-instances is used to
recreate one or more instances in a managed instance group. The underlying
virtual machine instances are deleted and recreated based on the latest
instance template configured for the managed instance group.

The command returns the operation status per instance, which might be FAIL,
SUCCESS, or MEMBER_NOT_FOUND. MEMBER_NOT_FOUND is returned only for
regional groups when the gcloud command-line tool wasn't able to resolve
the zone from the instance name.

**Synopsis:**
```
gcloud compute instance-groups managed recreate-instances NAME
    --instances=INSTANCE,[INSTANCE,...] [--region=REGION | --zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the managed instance group to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instances` | INSTANCE,[INSTANCE,...] |  | Names of instances to recreate. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the managed instance group to operate on. If not specified, you might be prompted to select a region (interactive mode only). A list of regions can be fetched by running: $ gcloud compute regions list Overrides the default compute/region property value for this command invocation. |
| `--zone` | ZONE |  | _[At most one of these can be specified:]_ Zone of the managed instance group to operate on. If not specified, you might be prompted to select a zone (interactive mode only). A list of zones can be fetched by running: $ gcloud compute zones list Overrides the default compute/zone property value for this command invocation. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/recreate-instances)

---
### `gcloud compute instance-groups managed resize`

Set managed instance group size

gcloud compute instance-groups managed resize resize a managed instance
group to a provided size.

If you resize down, the Instance Group Manager service deletes instances
from the group until the group reaches the desired size. Instances are
deleted in arbitrary order but the Instance Group Manager takes into
account some considerations before it chooses which instance to delete. For
more information, see
https://cloud.google.com/compute/docs/reference/rest/v1/instanceGroupManagers/resize.

If you resize up, the service adds instances to the group using the current
instance template until the group reaches the desired size.

**Synopsis:**
```
gcloud compute instance-groups managed resize NAME --size=SIZE
    [--region=REGION | --zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the managed instance group to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--size` | SIZE |  | Target number of running instances in managed instance group. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the managed instance group to operate on. If not specified, you might be prompted to select a region (interactive mode only). A list of regions can be fetched by running: $ gcloud compute regions list Overrides the default compute/region property value for this command invocation. |
| `--zone` | ZONE |  | _[At most one of these can be specified:]_ Zone of the managed instance group to operate on. If not specified, you might be prompted to select a zone (interactive mode only). A list of zones can be fetched by running: $ gcloud compute zones list Overrides the default compute/zone property value for this command invocation. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/resize)

---
### `gcloud compute instance-groups managed resume-instances`

Resume the suspended instances in a managed instance group

gcloud compute instance-groups managed resume-instances resumes one or more
instances from a managed instance group, thereby increasing the targetSize
and reducing the targetSuspendedSize of the group.

The command returns the operation status per instance, which might be FAIL,
SUCCESS, or MEMBER_NOT_FOUND. MEMBER_NOT_FOUND is returned only for
regional groups when the gcloud command-line tool wasn't able to resolve
the zone from the instance name.

**Synopsis:**
```
gcloud compute instance-groups managed resume-instances NAME
    --instances=INSTANCE,[INSTANCE,...] [--region=REGION | --zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the managed instance group to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instances` | INSTANCE,[INSTANCE,...] |  | Names of instances to resume. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the managed instance group to operate on. If not specified, you might be prompted to select a region (interactive mode only). A list of regions can be fetched by running: $ gcloud compute regions list Overrides the default compute/region property value for this command invocation. |
| `--zone` | ZONE |  | _[At most one of these can be specified:]_ Zone of the managed instance group to operate on. If not specified, you might be prompted to select a zone (interactive mode only). A list of zones can be fetched by running: $ gcloud compute zones list Overrides the default compute/zone property value for this command invocation. |


**Examples:**
```bash
To resume an instance from a managed instance group in the us-central1-a
zone, run:

    $ gcloud compute instance-groups managed resume-instances \
    example-managed-instance-group --zone=us-central1-a \
    --instances=example-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/resume-instances)

---
### `gcloud compute instance-groups managed set-autoscaling`

Set autoscaling parameters of a managed instance group

gcloud compute instance-groups managed set-autoscaling sets autoscaling
parameters of specified managed instance group.

Autoscalers can use one or more autoscaling signals. Information on using
multiple autoscaling signals can be found here:
https://cloud.google.com/compute/docs/autoscaler/multiple-signals

**Synopsis:**
```
gcloud compute instance-groups managed set-autoscaling NAME
    --max-num-replicas=MAX_NUM_REPLICAS
    [--cool-down-period=COOL_DOWN_PERIOD]
    [--cpu-utilization-predictive-method=CPU_UTILIZATION_PREDICTIVE_METHOD]
    [--custom-metric-utilization=[metric=METRIC],
      [utilization-target=UTILIZATION-TARGET],
      [utilization-target-type=UTILIZATION-TARGET-TYPE]]
    [--description=DESCRIPTION] [--min-num-replicas=MIN_NUM_REPLICAS]
    [--mode=MODE] [--remove-stackdriver-metric=METRIC]
    [--scale-based-on-cpu] [--scale-based-on-load-balancing]
    [--scale-in-control=[max-scaled-in-replicas=MAX-SCALED-IN-REPLICAS],
      [max-scaled-in-replicas-percent=MAX-SCALED-IN-REPLICAS-PERCENT],
      [time-window=TIME-WINDOW]] [--set-schedule=SCHEDULE_NAME]
    [--stackdriver-metric-filter=FILTER]
    [--stackdriver-metric-single-instance-assignment=ASSIGNMENT]
    [--stackdriver-metric-utilization-target=TARGET]
    [--stackdriver-metric-utilization-target-type=TARGET_TYPE]
    [--target-cpu-utilization=TARGET_CPU_UTILIZATION]
    [--target-load-balancing-utilization=TARGET_LOAD_BALANCING_UTILIZATION]
    [--update-stackdriver-metric=METRIC] [--region=REGION | --zone=ZONE]
    [--schedule-cron=CRON_EXPRESSION --schedule-description=DESCRIPTION
      --schedule-duration-sec=DURATION
      --schedule-min-required-replicas=MIN_REQUIRED_REPLICAS
      --schedule-time-zone=TIME_ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the managed instance group to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--max-num-replicas` | MAX_NUM_REPLICAS |  | Maximum number of replicas Autoscaler can set. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cool-down-period` | COOL_DOWN_PERIOD |  | The number of seconds that your application takes to initialize on a VM instance. This is referred to as the initialization period (https://cloud.google.com/compute/docs/autoscaler#cool_down_period). Specifying an accurate initialization period improves autoscaler decisions. For example, when scaling out, the autoscaler ignores data from VMs that are still initializing because those VMs might not yet represent normal usage of your application. The default initialization period is 60 seconds. See $ gcloud topic datetimes for information on duration formats. Initialization periods might vary because of numerous factors. We recommend that you test how long your application may take to initialize. To do this, create a VM and time your application's startup process. |
| `--cpu-utilization-predictive-method` | one of: none (Default) No predictions are made when calculating the number of VM instances |  | Indicates whether to use a predictive algorithm when scaling based on CPU. CPU_UTILIZATION_PREDICTIVE_METHOD must be one of: none (Default) No predictions are made when calculating the number of VM instances. optimize-availability Predictive autoscaling predicts the future values of the scaling metric and scales the group in advance to ensure that new VM instances are ready in time to cover the predicted peak. |
| `--custom-metric-utilization` | [metric=METRIC],[utilization-target=UTILIZATION-TARGET],[utilization-target-type=UTILIZATION-TARGET-TYPE] |  | Adds a target metric value for the Autoscaler to use. metric Protocol-free URL of a Google Cloud Monitoring metric. utilization-target Value of the metric Autoscaler aims to maintain (greater than 0.0). utilization-target-type How target is expressed. Valid values: DELTA_PER_MINUTE, DELTA_PER_SECOND, GAUGE. Mutually exclusive with --update-stackdriver-metric. |
| `--description` | DESCRIPTION |  | Notes about Autoscaler. |
| `--min-num-replicas` | MIN_NUM_REPLICAS |  | Minimum number of replicas Autoscaler can set. |
| `--mode` | one of: off Turns off autoscaling, while keeping the new configuration |  | Set the mode of an autoscaler for a managed instance group. You can turn off or restrict a group's autoscaler activities without affecting your autoscaler configuration. The autoscaler configuration persists while the activities are turned off or restricted, and the activities resume when the autoscaler is turned on again or when the restrictions are lifted. MODE must be one of: off Turns off autoscaling, while keeping the new configuration. on Permits autoscaling to scale out and in (default for new autoscalers). only-scale-out Permits autoscaling to scale only out and not in. only-up (DEPRECATED) Permits autoscaling to scale only out and not in. Value only-up is deprecated. Use --mode only-scale-out instead. |
| `--remove-stackdriver-metric` | METRIC |  | Stackdriver metric to remove from autoscaling configuration. If the metric is the only input used for autoscaling the command will fail. |
| `--scale-based-on-cpu` |  |  | Autoscaler will be based on CPU utilization. |
| `--scale-based-on-load-balancing` |  |  | Use autoscaling based on load balancing utilization. |
| `--scale-in-control` | [max-scaled-in-replicas=MAX-SCALED-IN-REPLICAS],[max-scaled-in-replicas-percent=MAX-SCALED-IN-REPLICAS-PERCENT],[time-window=TIME-WINDOW] |  | Configuration that allows slower scale in so that even if Autoscaler recommends an abrupt scale in of a managed instance group, it will be throttled as specified by the parameters. max-scaled-in-replicas Maximum allowed number of VMs that can be deducted from the peak recommendation during the window. Possibly all these VMs can be deleted at once so the application needs to be prepared to lose that many VMs in one step. Mutually exclusive with 'max-scaled-in-replicas-percent'. max-scaled-in-replicas-percent Maximum allowed percent of VMs that can be deducted from the peak recommendation during the window. Possibly all these VMs can be deleted at once so the application needs to be prepared to lose that many VMs in one step. Mutually exclusive with 'max-scaled-in-replicas'. time-window How long back autoscaling should look when computing recommendations. The autoscaler will not resize below the maximum allowed deduction subtracted from the peak size observed in this period. Measured in seconds. |
| `--set-schedule` | SCHEDULE_NAME |  | Unique name for the scaling schedule. |
| `--stackdriver-metric-filter` | FILTER |  | Expression for filtering samples used to autoscale, see https://cloud.google.com/monitoring/api/v3/filters. |
| `--stackdriver-metric-single-instance-assignment` | ASSIGNMENT |  | Value that indicates the amount of work that each instance is expected to handle. Autoscaler maintains enough VMs by dividing the available work by this value. Mutually exclusive with -stackdriver-metric-utilization-target-type, -stackdriver-metric-utilization-target-type, and --custom-metric-utilization. |
| `--stackdriver-metric-utilization-target` | TARGET |  | Value of the metric Autoscaler aims to maintain. When specifying this flag you must also provide --stackdriver-metric-utilization-target-type. Mutually exclusive with --stackdriver-metric-single-instance-assignment and --custom-metric-utilization. |
| `--stackdriver-metric-utilization-target-type` | one of: delta-per-minute, delta-per-second, gauge |  | Value of the metric Autoscaler aims to maintain. When specifying this flag you must also provide --stackdriver-metric-utilization-target. Mutually exclusive with --stackdriver-metric-single-instance-assignment and --custom-metric-utilization. TARGET_TYPE must be one of: delta-per-minute, delta-per-second, gauge. |
| `--target-cpu-utilization` | TARGET_CPU_UTILIZATION |  | Autoscaler aims to maintain CPU utilization at target level (0.0 to 1.0). |
| `--target-load-balancing-utilization` | TARGET_LOAD_BALANCING_UTILIZATION |  | Autoscaler aims to maintain the load balancing utilization level (greater than 0.0). |
| `--update-stackdriver-metric` | METRIC |  | Stackdriver metric to use as an input for autoscaling. When using this flag, the target value of the metric must also be specified by using the following flags: --stackdriver-metric-single-instance-assignment or --stackdriver-metric-utilization-target and --stackdriver-metric-utilization-target-type. Mutually exclusive with --custom-metric-utilization. |
| `--schedule-cron` | CRON_EXPRESSION |  | _[invocation.]_ Start time of the scaling schedule in cron format. This is when the autoscaler starts creating new VMs, if the group's current size is less than the minimum required instances. Set the start time to allow enough time for new VMs to boot and initialize. For example if your workload takes 10 minutes from VM creation to start serving then set the start time 10 minutes earlier than the time you need VMs to be ready. |
| `--schedule-description` | DESCRIPTION |  | _[invocation.]_ A verbose description of the scaling schedule. |
| `--schedule-duration-sec` | DURATION |  | _[invocation.]_ How long should the scaling schedule be active, measured in seconds. Minimum duration is 5 minutes. A scaling schedule is active from its start time and for its configured duration. During this time, the autoscaler scales the group to have at least as many VMs as defined by the minimum required instances. After the configured duration, if there is no need to maintain capacity, the autoscaler starts removing instances after the usual stabilization period and after scale-in controls (if configured). For more information, see Delays in scaling in (https://cloud.google.com/compute/docs/autoscaler/understanding-autoscaler-decisions#delays_in_scaling_in) and Scale-in controls (https://cloud.google.com/compute/docs/autoscaler/understanding-autoscaler-decisions#scale-in_controls). This ensures you don't accidentally lose capacity immediately after the scaling schedule ends. |
| `--schedule-min-required-replicas` | MIN_REQUIRED_REPLICAS |  | _[invocation.]_ How many VMs the autoscaler should provision for the duration of this scaling schedule. Autoscaler provides at least this number of instances when the scaling schedule is active. A managed instance group can have more VMs if there are other scaling schedules active with more required instances or if another signal (for example, scaling based on CPU) requires more instances to meet its target. This configuration does not change autoscaling minimum and maximum instance limits which are always in effect. Autoscaler does not create more than the maximum number of instances configured for a group. |
| `--schedule-time-zone` | TIME_ZONE |  | _[invocation.]_ Name of the timezone that the scaling schedule's start time is in. It should be provided as a name from the IANA tz database (for example Europe/Paris or UTC). It automatically adjusts for daylight savings time (DST). If no time zone is provided, UTC is used as a default. See https://en.wikipedia.org/wiki/List_of_tz_database_time_zones for the list of valid timezones. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/set-autoscaling)

---
### `gcloud compute instance-groups managed set-instance-template`

Set the instance template for a managed instance group

gcloud compute instance-groups managed set-instance-template sets the
instance template for an existing managed instance group.

The new template applies to all new instances added to the managed instance
group.

To apply the new template to existing instances in the group, use one of
the following methods:

  o Update instances using the update-instances command.
  o Recreate instances using the recreate-instances command.
  o Use the rolling-action start-update command.
  o Use the API to set the group's updatePolicy.type to PROACTIVE.

**Synopsis:**
```
gcloud compute instance-groups managed set-instance-template NAME
    --template=TEMPLATE [--region=REGION | --zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the managed instance group to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--template` | TEMPLATE |  | Specifies the instance template to use when creating new instances. An instance template is either a global or regional resource. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the managed instance group to operate on. If not specified, you might be prompted to select a region (interactive mode only). A list of regions can be fetched by running: $ gcloud compute regions list Overrides the default compute/region property value for this command invocation. |
| `--zone` | ZONE |  | _[At most one of these can be specified:]_ Zone of the managed instance group to operate on. If not specified, you might be prompted to select a zone (interactive mode only). A list of zones can be fetched by running: $ gcloud compute zones list Overrides the default compute/zone property value for this command invocation. |


**Examples:**
```bash
Running:

    gcloud compute instance-groups managed set-instance-template \
    example-managed-instance-group --template=example-global-instance-template

Sets the instance template for the 'example-managed-instance-group' group
to a global resource 'example-global-instance-template'.

To use a regional instance template, specify the full or partial URL of the
template.

Running:

    gcloud compute instance-groups managed set-instance-template \
    example-managed-instance-group \
    --template=projects/example-project/regions/us-central1/instanceTemplates/example-regional-instance-template

Sets the instance template for the 'example-managed-instance-group' group
to a regional resource 'example-regional-instance-template'.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/set-instance-template)

---
### `gcloud compute instance-groups managed set-named-ports`

Sets the list of named ports for an instance group

Named ports are key:value pairs metadata representing the service name and
the port that it's running on. Named ports can be assigned to an instance
group, which indicates that the service is available on all instances in
the group. This information is used by Application Load Balancers and proxy
Network Load Balancers.

gcloud compute instance-groups managed set-named-ports sets the list of
named ports for all instances in an instance group.

Note: Running this command will clear all existing named ports.

**Synopsis:**
```
gcloud compute instance-groups managed set-named-ports NAME
    --named-ports=[NAME:PORT,...] [--region=REGION | --zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the instance group to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--named-ports` | [NAME:PORT,...] |  | The comma-separated list of key:value pairs representing the service name and the port that it is running on. To clear the list of named ports pass empty list as flag value. For example: $ gcloud compute instance-groups managed set-named-ports \ example-instance-group --named-ports "" |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the instance group to operate on. If not specified, you might be prompted to select a region (interactive mode only). A list of regions can be fetched by running: $ gcloud compute regions list Overrides the default compute/region property value for this command invocation. |
| `--zone` | ZONE |  | _[At most one of these can be specified:]_ Zone of the instance group to operate on. If not specified, you might be prompted to select a zone (interactive mode only). A list of zones can be fetched by running: $ gcloud compute zones list Overrides the default compute/zone property value for this command invocation. |


**Examples:**
```bash
For example, to apply the named ports to an entire instance group:

    $ gcloud compute instance-groups managed set-named-ports \
        example-instance-group --named-ports=example-service:1111 \
        --zone=us-central1-a

The above example will assign a name 'example-service' for port 1111 to the
instance group called 'example-instance-group' in the us-central1-a zone.
The command removes any named ports that are already set for this instance
group.

To clear named ports from instance group provide empty named ports list as
parameter:

    $ gcloud compute instance-groups managed set-named-ports \
        example-instance-group --named-ports="" --zone=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/set-named-ports)

---
### `gcloud compute instance-groups managed set-target-pools`

Set target pools of managed instance group

gcloud compute instance-groups managed set-target-pools sets the target
pools for an existing managed instance group. Instances that are part of
the managed instance group will be added to the target pool automatically.

**Synopsis:**
```
gcloud compute instance-groups managed set-target-pools NAME
    --target-pools=[TARGET_POOL,...] [--region=REGION | --zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the managed instance group to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--target-pools` | [TARGET_POOL,...] |  | Compute Engine Target Pools to add the instances to. Target Pools must be specified by name or by URL. Example: --target-pools=target-pool-1,target-pool-2. To clear the set of Target Pools pass in an empty list. Example: --target-pools="" |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the managed instance group to operate on. If not specified, you might be prompted to select a region (interactive mode only). A list of regions can be fetched by running: $ gcloud compute regions list Overrides the default compute/region property value for this command invocation. |
| `--zone` | ZONE |  | _[At most one of these can be specified:]_ Zone of the managed instance group to operate on. If not specified, you might be prompted to select a zone (interactive mode only). A list of zones can be fetched by running: $ gcloud compute zones list Overrides the default compute/zone property value for this command invocation. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/set-target-pools)

---
### `gcloud compute instance-groups managed start-instances`

Start the stopped instances in a managed instance group

gcloud compute instance-groups managed start-instances starts one or more
instances from a managed instance group, thereby increasing the targetSize
and reducing the targetStoppedSize of the group.

The command returns the operation status per instance, which might be FAIL,
SUCCESS, or MEMBER_NOT_FOUND. MEMBER_NOT_FOUND is returned only for
regional groups when the gcloud command-line tool wasn't able to resolve
the zone from the instance name.

**Synopsis:**
```
gcloud compute instance-groups managed start-instances NAME
    --instances=INSTANCE,[INSTANCE,...] [--region=REGION | --zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the managed instance group to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instances` | INSTANCE,[INSTANCE,...] |  | Names of instances to start. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the managed instance group to operate on. If not specified, you might be prompted to select a region (interactive mode only). A list of regions can be fetched by running: $ gcloud compute regions list Overrides the default compute/region property value for this command invocation. |
| `--zone` | ZONE |  | _[At most one of these can be specified:]_ Zone of the managed instance group to operate on. If not specified, you might be prompted to select a zone (interactive mode only). A list of zones can be fetched by running: $ gcloud compute zones list Overrides the default compute/zone property value for this command invocation. |


**Examples:**
```bash
To start an instance from a managed instance group in the us-central1-a
zone, run:

    $ gcloud compute instance-groups managed start-instances \
    example-managed-instance-group --zone=us-central1-a \
    --instances=example-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/start-instances)

---
### `gcloud compute instance-groups managed stop-autoscaling`

Stop autoscaling a managed instance group

gcloud compute instance-groups managed stop-autoscaling stops autoscaling a
managed instance group and deletes the autoscaler configuration. If
autoscaling is not enabled for the managed instance group, this command
does nothing and will report an error.

If you need to keep the autoscaler configuration, you can temporarily
disable an autoscaler by setting its mode to off using the
update-autoscaling command instead.

**Synopsis:**
```
gcloud compute instance-groups managed stop-autoscaling NAME
    [--region=REGION | --zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the managed instance group to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the managed instance group to operate on. If not specified, you might be prompted to select a region (interactive mode only). A list of regions can be fetched by running: $ gcloud compute regions list Overrides the default compute/region property value for this command invocation. |
| `--zone` | ZONE |  | _[At most one of these can be specified:]_ Zone of the managed instance group to operate on. If not specified, you might be prompted to select a zone (interactive mode only). A list of zones can be fetched by running: $ gcloud compute zones list Overrides the default compute/zone property value for this command invocation. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/stop-autoscaling)

---
### `gcloud compute instance-groups managed stop-instances`

Stop instances owned by a managed instance group

gcloud compute instance-groups managed stop-instances stops one or more
instances from a managed instance group

**Synopsis:**
```
gcloud compute instance-groups managed stop-instances NAME
    --instances=INSTANCE,[INSTANCE,...] [--force]
    [--region=REGION | --zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the managed instance group to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instances` | INSTANCE,[INSTANCE,...] |  | Names of instances to stop. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--force` |  |  | Immediately stop the specified instances, skipping the initial delay, if one is specified in the standby policy. |


**Examples:**
```bash
To stop an instance from a managed instance group in the us-central1-a
zone, run:

    $ gcloud compute instance-groups managed stop-instances \
    example-managed-instance-group --zone=us-central1-a \
    --instances=example-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/stop-instances)

---
### `gcloud compute instance-groups managed suspend-instances`

Suspend instances owned by a managed instance group

gcloud compute instance-groups managed suspend-instances suspends one or
more instances from a managed instance group, thereby reducing the
targetSize and increasing the targetSuspendedSize of the group.

The command returns the operation status per instance, which might be FAIL,
SUCCESS, or MEMBER_NOT_FOUND. MEMBER_NOT_FOUND is returned only for
regional groups when the gcloud command-line tool wasn't able to resolve
the zone from the instance name.

**Synopsis:**
```
gcloud compute instance-groups managed suspend-instances NAME
    --instances=INSTANCE,[INSTANCE,...] [--force]
    [--region=REGION | --zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the managed instance group to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instances` | INSTANCE,[INSTANCE,...] |  | Names of instances to suspend. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--force` |  |  | Immediately suspend the specified instances, skipping the initial delay, if one is specified in the standby policy. |


**Examples:**
```bash
To suspend an instance from a managed instance group in the us-central1-a
zone, run:

    $ gcloud compute instance-groups managed suspend-instances \
    example-managed-instance-group --zone=us-central1-a \
    --instances=example-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/suspend-instances)

---
### `gcloud compute instance-groups managed update`

Update a Compute Engine managed instance group

Update a Compute Engine managed instance group.

gcloud compute instance-groups managed update allows you to specify or
modify the description and group policies for an existing managed instance
group, including the group's update policy and optional autohealing and
stateful policies

The group's update policy defines how an updated VM configuration is
applied to existing VMs in the group. For more information, see [Applying
new configurations]
(https://cloud.google.com/compute/docs/instance-groups/updating-migs) to
VMs in a MIG.

A stateful policy defines which resources should be preserved across the
group. When instances in the group are recreated, stateful resources are
preserved. This command allows you to update stateful resources,
specifically to add or remove stateful disks.

When updating the autohealing policy, you can specify the health check,
initial delay, or both. If either field is unspecified, its value won't be
modified. If --health-check is specified, the health check monitors the
health of your application. Whenever the health check signal for an
instance becomes UNHEALTHY, the autohealer recreates the instance.

If no health check exists, instance autohealing is triggered only by
instance status: if an instance is not RUNNING, the group recreates it.

**Synopsis:**
```
gcloud compute instance-groups managed update NAME
    [--default-action-on-vm-failure=ACTION_ON_VM_FAILURE]
    [--description=DESCRIPTION] [--[no-]force-update-on-repair]
    [--instance-redistribution-type=TYPE]
    [--instance-selection=name=NAME,
      machine-type=MACHINE_TYPE[,machine-type=MACHINE_TYPE...][,rank=RANK]]
    [--instance-selection-machine-types=[MACHINE_TYPE,...]]
    [--list-managed-instances-results=MODE]
    [--remove-instance-selections=[INSTANCE_SELECTION_NAME,...]]
    [--remove-instance-selections-all]
    [--remove-stateful-disks=DEVICE_NAME,[DEVICE_NAME,...]]
    [--remove-stateful-external-ips=INTERFACE_NAME,[...]]
    [--remove-stateful-internal-ips=INTERFACE_NAME,[...]] [--size=SIZE]
    [--standby-policy-initial-delay=STANDBY_POLICY_INITIAL_DELAY]
    [--standby-policy-mode=STANDBY_POLICY_MODE]
    [--stateful-disk=[auto-delete=AUTO-DELETE],[device-name=DEVICE-NAME]]
    [--stateful-external-ip=[enabled],
      [auto-delete=AUTO-DELETE],[interface-name=INTERFACE-NAME]]
    [--stateful-internal-ip=[enabled],
      [auto-delete=AUTO-DELETE],[interface-name=INTERFACE-NAME]]
    [--stopped-size=STOPPED_SIZE] [--suspended-size=SUSPENDED_SIZE]
    [--target-distribution-shape=SHAPE]
    [--clear-autohealing
      | --initial-delay=INITIAL_DELAY --health-check=HEALTH_CHECK
      | --http-health-check=HTTP_HEALTH_CHECK
      | --https-health-check=HTTPS_HEALTH_CHECK]
    [--region=REGION | --zone=ZONE]
    [--remove-workload-policy | --workload-policy=WORKLOAD_POLICY]
    [--update-policy-max-surge=MAX_SURGE
      --update-policy-max-unavailable=MAX_UNAVAILABLE
      --update-policy-minimal-action=UPDATE_POLICY_MINIMAL_ACTION
      --update-policy-most-disruptive-action=UPDATE_POLICY_MOST_DISRUPTIVE_ACTION --update-policy-replacement-method=UPDATE_POLICY_REPLACEMENT_METHOD --update-policy-type=UPDATE_TYPE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the managed instance group to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--default-action-on-vm-failure` | one of: do-nothing MIG does not repair a failed or an unhealthy VM |  | Specifies the action that a MIG performs on a failed or an unhealthy VM. A VM is marked as unhealthy when the application running on that VM fails a health check. By default, the value of the flag is set to repair. ACTION_ON_VM_FAILURE must be one of: do-nothing MIG does not repair a failed or an unhealthy VM. repair MIG automatically repairs a failed or an unhealthy VM. |
| `--description` | DESCRIPTION |  | An optional description for this group. To clear the description, set the value to an empty string. |
| `--[no-]force-update-on-repair` |  |  | Specifies whether to apply the group's latest configuration when repairing a VM. If you updated the group's instance template or per-instance configurations after the VM was created, then these changes are applied when VM is repaired. If this flag is disabled with -no-force-update-on-repair, then updates are applied in accordance with the group's update policy type. By default, this flag is disabled. Use --force-update-on-repair to enable and --no-force-update-on-repair to disable. |
| `--instance-redistribution-type` | one of: none The managed instance group does not redistribute instances across zones |  | Specifies the type of the instance redistribution policy. An instance redistribution type lets you enable or disable automatic instance redistribution across zones to meet the group's target distribution shape. An instance redistribution type can be specified only for a non-autoscaled regional managed instance group. By default it is set to proactive. TYPE must be one of: none The managed instance group does not redistribute instances across zones. proactive The managed instance group proactively redistributes instances to meet its target distribution. |
| `--instance-selection` | name=NAME,machine-type=MACHINE_TYPE[,machine-type=MACHINE_TYPE...][,rank=RANK] |  | Named selection of machine types with an optional rank. For example, --instance-selection="name=instance-selection-1,machine-type=e2-standard-8,machine-type=t2d-standard-8,rank=0" |
| `--instance-selection-machine-types` | [MACHINE_TYPE,...] |  | Machine types that are used to create VMs in the managed instance group. If not provided, the machine type specified in the instance template is used. |
| `--list-managed-instances-results` | one of: pageless Pagination is disabled for the group's listManagedInstances API method |  | Pagination behavior for the group's listManagedInstances API method. This flag does not affect the group's gcloud or console list-instances behavior. By default it is set to pageless. MODE must be one of: pageless Pagination is disabled for the group's listManagedInstances API method. maxResults and pageToken query parameters are ignored and all instances are returned in a single response. paginated Pagination is enabled for the group's listManagedInstances API method. maxResults and pageToken query parameters are respected. |
| `--remove-instance-selections` | [INSTANCE_SELECTION_NAME,...] |  | Remove specific instance selections from the instance flexibility policy. |
| `--remove-instance-selections-all` |  |  | Remove all instance selections from the instance flexibility policy. |
| `--remove-stateful-disks` | DEVICE_NAME,[DEVICE_NAME,...] |  | Remove stateful configuration for the specified disks. |
| `--remove-stateful-external-ips` | INTERFACE_NAME,[...] |  | Remove stateful configuration for the specified interfaces for external IPs. |
| `--remove-stateful-internal-ips` | INTERFACE_NAME,[...] |  | Remove stateful configuration for the specified interfaces for internal IPs. |
| `--size` | SIZE |  | Target number of running instances in managed instance group. |
| `--standby-policy-initial-delay` | STANDBY_POLICY_INITIAL_DELAY |  | Specifies the number of seconds that the MIG should wait before suspending or stopping a VM. The initial delay gives the initialization script the time to prepare your VM for a quick scale out. |
| `--standby-policy-mode` | one of: manual MIG does not automatically resume or start VMs in the standby pool when the group scales out |  | Defines how a MIG resumes or starts VMs from a standby pool when the group scales out. The default mode is manual. STANDBY_POLICY_MODE must be one of: manual MIG does not automatically resume or start VMs in the standby pool when the group scales out. scale-out-pool MIG automatically resumes or starts VMs in the standby pool when the group scales out, and replenishes the standby pool afterwards. |
| `--stateful-disk` | [auto-delete=AUTO-DELETE],[device-name=DEVICE-NAME] |  | Disks considered stateful by the instance group. Managed instance groups preserve and reattach stateful disks on VM autohealing, update, and recreate events. Use this argument multiple times to update more disks. If a stateful disk with the given device name already exists in the current instance configuration, its properties will be replaced by the newly provided ones. Otherwise, a new stateful disk definition will be added to the instance configuration. device-name (Required) Device name of the disk to mark stateful. auto-delete (Optional) Specifies the auto deletion policy of the stateful disk. The following options are available: + never: (Default) Never delete this disk. Instead, detach the disk when its instance is deleted. + on-permanent-instance-deletion: Delete the stateful disk when the instance that it's attached to is permanently deleted from the group; for example, when the instance is deleted manually or when the group size is decreased. |
| `--stateful-external-ip` | [enabled],[auto-delete=AUTO-DELETE],[interface-name=INTERFACE-NAME] |  | Managed instance groups preserve stateful IPs on VM autohealing, update, and recreate events. Use this argument multiple times to update more IPs. If a stateful external IP with the given interface name already exists in the current instance configuration, its properties are replaced by the newly provided ones. Otherwise, a new stateful external IP definition is added to the instance configuration. At least one of the following is required: enabled Marks the IP address as stateful. The network interface named nic0 is assumed by default when interface-name is not specified. This flag can be omitted when interface-name is provided explicitly. interface-name Marks the IP address from this network interface as stateful. This flag can be omitted when enabled is provided. Additional arguments: auto-delete (Optional) Prescribes what should happen to an associated static Address resource when a VM instance is permanently deleted. Regardless of the value of the delete rule, stateful IP addresses are always preserved on instance autohealing, update, and recreation operations. The following options are available: + never: (Default) Never delete the static IP address. Instead, unassign the address when its instance is permanently deleted and keep the address reserved. + on-permanent-instance-deletion: Delete the static IP address reservation when the instance that it's assigned to is permanently deleted from the instance group; for example, when the instance is deleted manually or when the group size is decreased. |
| `--stateful-internal-ip` | [enabled],[auto-delete=AUTO-DELETE],[interface-name=INTERFACE-NAME] |  | Managed instance groups preserve stateful IPs on VM autohealing, update, and recreate events. Use this argument multiple times to update more IPs. If a stateful internal IP with the given interface name already exists in the current instance configuration, its properties are replaced by the newly provided ones. Otherwise, a new stateful internal IP definition is added to the instance configuration. At least one of the following is required: enabled Marks the IP address as stateful. The network interface named nic0 is assumed by default when interface-name is not specified. This flag can be omitted when interface-name is provided explicitly. interface-name Marks the IP address from this network interface as stateful. This flag can be omitted when enabled is provided. Additional arguments: auto-delete (Optional) Prescribes what should happen to an associated static Address resource when a VM instance is permanently deleted. Regardless of the value of the delete rule, stateful IP addresses are always preserved on instance autohealing, update, and recreation operations. The following options are available: + never: (Default) Never delete the static IP address. Instead, unassign the address when its instance is permanently deleted and keep the address reserved. + on-permanent-instance-deletion: Delete the static IP address reservation when the instance that it's assigned to is permanently deleted from the instance group; for example, when the instance is deleted manually or when the group size is decreased. |
| `--stopped-size` | STOPPED_SIZE |  | Specifies the target size of stopped VMs in the group. |
| `--suspended-size` | SUSPENDED_SIZE |  | Specifies the target size of suspended VMs in the group. |
| `--target-distribution-shape` | one of: any The group picks zones for creating VM instances to fulfill the requested number of VMs within present resource constraints and to maximize utilization of unused zonal reservations |  | Specifies how a regional managed instance group distributes its instances across zones within the region. The default shape is even. SHAPE must be one of: any The group picks zones for creating VM instances to fulfill the requested number of VMs within present resource constraints and to maximize utilization of unused zonal reservations. Recommended for batch workloads that do not require high availability. any-single-zone The group schedules all instances within a single zone. The zone is chosen based on hardware support, current resources availability, and matching reservations. The group might not be able to create the requested number of VMs in case of zonal resource availability constraints. Recommended for workloads requiring extensive communication between VMs. balanced The group prioritizes acquisition of resources, scheduling VMs in zones where resources are available while distributing VMs as evenly as possible across selected zones to minimize the impact of zonal failure. Recommended for highly available serving or batch workloads that do not require autoscaling. even The group schedules VM instance creation and deletion to achieve and maintain an even number of managed instances across the selected zones. The distribution is even when the number of managed instances does not differ by more than 1 between any two zones. Recommended for highly available serving workloads. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/update)

---
### `gcloud compute instance-groups managed update-autoscaling`

Update autoscaling parameters of a managed instance group

gcloud compute instance-groups managed update-autoscaling updates
autoscaling parameters of specified managed instance group.

Autoscalers can use one or more autoscaling signals. Information on using
multiple autoscaling signals can be found here:
https://cloud.google.com/compute/docs/autoscaler/multiple-signals

In contrast to gcloud compute instance-groups managed set-autoscaling, this
command only updates specified fields. For instance:

    $ gcloud compute instance-groups managed update-autoscaling \
      --mode only-scale-out

would change the mode field of the autoscaler policy, but leave the rest of
the settings intact.

**Synopsis:**
```
gcloud compute instance-groups managed update-autoscaling NAME
    [--cpu-utilization-predictive-method=CPU_UTILIZATION_PREDICTIVE_METHOD]
    [--max-num-replicas=MAX_NUM_REPLICAS]
    [--min-num-replicas=MIN_NUM_REPLICAS] [--mode=MODE]
    [--clear-scale-in-control
      | --scale-in-control=[max-scaled-in-replicas=MAX-SCALED-IN-REPLICAS],
      [max-scaled-in-replicas-percent=MAX-SCALED-IN-REPLICAS-PERCENT],
      [time-window=TIME-WINDOW]]
    [--disable-schedule=SCHEDULE_NAME | --enable-schedule=SCHEDULE_NAME
      | --remove-schedule=SCHEDULE_NAME | --set-schedule=SCHEDULE_NAME
      | --update-schedule=SCHEDULE_NAME] [--region=REGION | --zone=ZONE]
    [--schedule-cron=CRON_EXPRESSION --schedule-description=DESCRIPTION
      --schedule-duration-sec=DURATION
      --schedule-min-required-replicas=MIN_REQUIRED_REPLICAS
      --schedule-time-zone=TIME_ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the managed instance group to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cpu-utilization-predictive-method` | one of: none (Default) No predictions are made when calculating the number of VM instances |  | Indicates whether to use a predictive algorithm when scaling based on CPU. CPU_UTILIZATION_PREDICTIVE_METHOD must be one of: none (Default) No predictions are made when calculating the number of VM instances. optimize-availability Predictive autoscaling predicts the future values of the scaling metric and scales the group in advance to ensure that new VM instances are ready in time to cover the predicted peak. |
| `--max-num-replicas` | MAX_NUM_REPLICAS |  | Maximum number of replicas Autoscaler can set. |
| `--min-num-replicas` | MIN_NUM_REPLICAS |  | Minimum number of replicas Autoscaler can set. |
| `--mode` | one of: off Turns off autoscaling, while keeping the new configuration |  | Set the mode of an autoscaler for a managed instance group. You can turn off or restrict a group's autoscaler activities without affecting your autoscaler configuration. The autoscaler configuration persists while the activities are turned off or restricted, and the activities resume when the autoscaler is turned on again or when the restrictions are lifted. MODE must be one of: off Turns off autoscaling, while keeping the new configuration. on Permits autoscaling to scale out and in (default for new autoscalers). only-scale-out Permits autoscaling to scale only out and not in. only-up (DEPRECATED) Permits autoscaling to scale only out and not in. Value only-up is deprecated. Use --mode only-scale-out instead. |
| `--schedule-cron` | CRON_EXPRESSION |  | _[invocation.]_ Start time of the scaling schedule in cron format. This is when the autoscaler starts creating new VMs, if the group's current size is less than the minimum required instances. Set the start time to allow enough time for new VMs to boot and initialize. For example if your workload takes 10 minutes from VM creation to start serving then set the start time 10 minutes earlier than the time you need VMs to be ready. |
| `--schedule-description` | DESCRIPTION |  | _[invocation.]_ A verbose description of the scaling schedule. |
| `--schedule-duration-sec` | DURATION |  | _[invocation.]_ How long should the scaling schedule be active, measured in seconds. Minimum duration is 5 minutes. A scaling schedule is active from its start time and for its configured duration. During this time, the autoscaler scales the group to have at least as many VMs as defined by the minimum required instances. After the configured duration, if there is no need to maintain capacity, the autoscaler starts removing instances after the usual stabilization period and after scale-in controls (if configured). For more information, see Delays in scaling in (https://cloud.google.com/compute/docs/autoscaler/understanding-autoscaler-decisions#delays_in_scaling_in) and Scale-in controls (https://cloud.google.com/compute/docs/autoscaler/understanding-autoscaler-decisions#scale-in_controls). This ensures you don't accidentally lose capacity immediately after the scaling schedule ends. |
| `--schedule-min-required-replicas` | MIN_REQUIRED_REPLICAS |  | _[invocation.]_ How many VMs the autoscaler should provision for the duration of this scaling schedule. Autoscaler provides at least this number of instances when the scaling schedule is active. A managed instance group can have more VMs if there are other scaling schedules active with more required instances or if another signal (for example, scaling based on CPU) requires more instances to meet its target. This configuration does not change autoscaling minimum and maximum instance limits which are always in effect. Autoscaler does not create more than the maximum number of instances configured for a group. |
| `--schedule-time-zone` | TIME_ZONE |  | _[invocation.]_ Name of the timezone that the scaling schedule's start time is in. It should be provided as a name from the IANA tz database (for example Europe/Paris or UTC). It automatically adjusts for daylight savings time (DST). If no time zone is provided, UTC is used as a default. See https://en.wikipedia.org/wiki/List_of_tz_database_time_zones for the list of valid timezones. |


**Examples:**
```bash
To update an existing instance group:

    $ gcloud compute instance-groups managed update-autoscaling \
      --mode=only-scale-out
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/update-autoscaling)

---
### `gcloud compute instance-groups managed update-instances`

Immediately update selected instances in a Compute Engine managed instance group

When using a managed instance group, it's possible that your intended
specification for a VM is different from the current state of that VM. For
example, this can happen due to changes to the group's target instance
template. This command enables you to initiate the update process on the
given set of instances instantly, thus when your Managed Instance Group is
stable you can be sure that all the changes were applied.

gcloud compute instance-groups managed update-instances allows you to
specify the least and the most disruptive actions that can be performed
while updating the instances. This way you can reduce the risk of rolling
out too many changes at once. Possible actions are: none, refresh, restart
and replace. The level of disruption to the instance is ordered as: none <
refresh < restart < replace.

The command returns the operation status per instance, which might be FAIL,
SUCCESS, or MEMBER_NOT_FOUND. MEMBER_NOT_FOUND is returned only for
regional groups when the gcloud command-line tool wasn't able to resolve
the zone from the instance name.

**Synopsis:**
```
gcloud compute instance-groups managed update-instances NAME
    (--all-instances | --instances=INSTANCE,[INSTANCE,...])
    [--minimal-action=MINIMAL_ACTION; default="none"]
    [--most-disruptive-allowed-action=MOST_DISRUPTIVE_ALLOWED_ACTION;
      default="replace"] [--region=REGION | --zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the managed instance group to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--all-instances` |  |  | _[Exactly one of these must be specified:]_ Update all instances in the group. |
| `--instances` | INSTANCE,[INSTANCE,...] |  | _[Exactly one of these must be specified:]_ Names of instances to update. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--minimal-action` | one of: none No action refresh Apply the new configuration without stopping VMs, if possible | none | Use this flag to minimize disruption as much as possible or to apply a more disruptive action than is strictly necessary. The MIG performs at least this action on each instance while updating. If the update requires a more disruptive action than the one specified here, then the more disruptive action is performed. If you omit this flag, the update uses the minimal-action value from the MIG's update policy, unless it is not set in which case the default is replace. MINIMAL_ACTION must be one of: none No action refresh Apply the new configuration without stopping VMs, if possible. For example, use ``refresh`` to apply changes that only affect metadata or additional disks. restart Apply the new configuration without replacing VMs, if possible. For example, stopping VMs and starting them again is sufficient to apply changes to machine type. replace Replace old VMs according to the --replacement-method flag. |
| `--most-disruptive-allowed-action` | one of: none No action refresh Apply the new configuration without stopping VMs, if possible | replace | Use this flag to prevent an update if it requires more disruption than you can afford. At most, the MIG performs the specified action on each instance while updating. If the update requires a more disruptive action than the one specified here, then the update fails and no changes are made. If you omit this flag, the update uses the most-disruptive-allowed-action value from the MIG's update policy, unless it is not set in which case the default is replace. MOST_DISRUPTIVE_ALLOWED_ACTION must be one of: none No action refresh Apply the new configuration without stopping VMs, if possible. For example, use ``refresh`` to apply changes that only affect metadata or additional disks. restart Apply the new configuration without replacing VMs, if possible. For example, stopping VMs and starting them again is sufficient to apply changes to machine type. replace Replace old VMs according to the --replacement-method flag. |


**Examples:**
```bash
To update instances instance-1, instance-2 in my-group, with
minimal-action=none and most-disruptive-allowed-action=restart, run:

    $ gcloud compute instance-groups managed update-instances my-group \
      --instances=instance-1,instance2 --minimal-action=none \
      --most-disruptive-allowed-action=restart
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/update-instances)

---
### `gcloud compute instance-groups managed wait-until`

Wait until the managed instance group reaches the desired state

Wait until the managed instance group reaches the desired state.

**Synopsis:**
```
gcloud compute instance-groups managed wait-until NAME
    (--stable | --version-target-reached) [--timeout=TIMEOUT]
    [--region=REGION | --zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the managed instance group to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--stable` |  |  | _[Exactly one of these must be specified:]_ Wait until the group is stable. |
| `--version-target-reached` |  |  | _[Exactly one of these must be specified:]_ Wait until version target is reached. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--timeout` | TIMEOUT |  | Waiting time in seconds for the group to reach the desired state. |


**Examples:**
```bash
To wait until the managed instance group instance-group-1 is stable, run:

    $ gcloud compute instance-groups managed wait-until \
        --stable instance-group-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/wait-until)

---
### `gcloud compute instance-groups managed wait-until-stable`

Waits until state of managed instance group is stable

(DEPRECATED) Waits until state of managed instance group is stable.

gcloud compute instance-groups managed wait-until-stable is deprecated.
Please use gcloud compute instance-groups managed wait-until --stable
instead.

**Synopsis:**
```
gcloud compute instance-groups managed wait-until-stable NAME
    [--timeout=TIMEOUT] [--region=REGION | --zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the managed instance group to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--timeout` | TIMEOUT |  | Timeout in seconds for waiting for group becoming stable. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/wait-until-stable)

---

## `gcloud compute instance-groups managed all-instances-config` — override instance template settings for all instances in a managed instance group
### `gcloud compute instance-groups managed all-instances-config delete`

Delete values defined in the all-instances configuration of a managed instance group

gcloud compute instance-groups managed all-instances-config delete deletes
one or more values defined in the all-instances configuration of a managed
instance group.

To apply a revised all-instances configuration to existing instances in the
group, use one of the following methods:

  o Update instances using the update-instances command.
  o Recreate instances using the recreate-instances command.
  o Use the rolling-action start-update command.
  o Use the API to set the group's updatePolicy.type to PROACTIVE.

**Synopsis:**
```
gcloud compute instance-groups managed all-instances-config delete NAME
    [--labels=KEY,[KEY,...]] [--metadata=KEY,[KEY,...]]
    [--region=REGION | --zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the managed instance group to delete the all instances
   configuration for.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--labels` | KEY,[KEY,...] |  | Remove labels keys from the group's all instances configuration. |
| `--metadata` | KEY,[KEY,...] |  | Remove metadata keys from the group's all instances configuration. |


**Examples:**
```bash
To delete the group's all-instances configuration in order to stop
overriding the group's instance template for a label with the key label-key
and metadata with the key metadata-key in group my-group, run:

    $ gcloud compute instance-groups managed all-instances-config \
        delete my-group --metadata=metadata-key --labels=label-key
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/all-instances-config/delete)

---
### `gcloud compute instance-groups managed all-instances-config update`

Update the all-instances configuration of a managed instance group

gcloud compute instance-groups managed all-instances-config update updates
the group's all-instances configuration and applies it only to new
instances that are added to the group.

To apply a revised all-instances configuration to existing instances in the
group, use one of the following methods:

  o Update instances using the update-instances command.
  o Recreate instances using the recreate-instances command.
  o Use the rolling-action start-update command.
  o Use the API to set the group's updatePolicy.type to PROACTIVE.

**Synopsis:**
```
gcloud compute instance-groups managed all-instances-config update NAME
    [--labels=KEY=VALUE,[KEY=VALUE,...]]
    [--metadata=KEY=VALUE,[KEY=VALUE,...]] [--region=REGION | --zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the managed instance group to update the all instances
   configuration for.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--labels` | KEY=VALUE,[KEY=VALUE,...] |  | Add labels to the group's all instances configuration. |
| `--metadata` | KEY=VALUE,[KEY=VALUE,...] |  | Add metadata to the group's all instances configuration. |


**Examples:**
```bash
To update an all-instances configuration in order to override the group's
instance template for a label with the key label-key and metadata with the
key metadata-key in group my-group, run:

    $ gcloud compute instance-groups managed all-instances-config \
        update my-group \
        --metadata=metadata-key=metadata-override-value \
        --labels=qlabel-key=label-override-value
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/all-instances-config/update)

---

## `gcloud compute instance-groups managed instance-configs` — manage instance-specific settings in a managed instance group
### `gcloud compute instance-groups managed instance-configs create`

Create a per-instance config for an instance in a managed instance group

gcloud compute instance-groups managed instance-configs create creates a
per-instance config for an instance controlled by a Compute Engine managed
instance group. An instance with a per-instance config preserves the
specified metadata and/or disks during instance recreation and deletion.

Once created, the config is applied immediately to the corresponding
instance, by performing the necessary action (for example, REFRESH), unless
overridden by providing the --no-update-instance flag.

**Synopsis:**
```
gcloud compute instance-groups managed instance-configs create NAME
    --instance=INSTANCE
    [--instance-update-minimal-action=INSTANCE_UPDATE_MINIMAL_ACTION;
      default="none"]
    [--stateful-disk=[auto-delete=AUTO-DELETE],
      [device-name=DEVICE-NAME],[mode=MODE],[source=SOURCE]]
    [--stateful-external-ip=[address=ADDRESS],
      [auto-delete=AUTO-DELETE],[interface-name=INTERFACE-NAME]]
    [--stateful-internal-ip=[address=ADDRESS],
      [auto-delete=AUTO-DELETE],[interface-name=INTERFACE-NAME]]
    [--stateful-metadata=KEY=VALUE,[KEY=VALUE,...]] [--no-update-instance]
    [--region=REGION | --zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the managed instance group to create a per-instance config for.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE |  | URI/name of an existing instance in the managed instance group. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance-update-minimal-action` | one of: none No action refresh Apply the new configuration without stopping VMs, if possible | none | Perform at least this action on the instance while updating, if --update-instance is set to true. INSTANCE_UPDATE_MINIMAL_ACTION must be one of: none No action refresh Apply the new configuration without stopping VMs, if possible. For example, use ``refresh`` to apply changes that only affect metadata or additional disks. restart Apply the new configuration without replacing VMs, if possible. For example, stopping VMs and starting them again is sufficient to apply changes to machine type. replace Replace old VMs according to the --replacement-method flag. |
| `--stateful-disk` | [auto-delete=AUTO-DELETE],[device-name=DEVICE-NAME],[mode=MODE],[source=SOURCE] |  | Disks considered stateful by the instance group. Managed instance groups preserve and reattach stateful disks on VM autohealing, update, and recreate events. You can also attach and preserve disks, not defined in the group's instance template, to a given instance. The same disk can be attached to more than one instance but only in read-only mode. Use this argument multiple times to attach and preserve multiple disks. device-name Name under which disk is or will be attached. source Optional argument used to specify the URI of an existing persistent disk to attach under specified device-name. mode Specifies the mode of the disk to attach. Supported options are ro for read-only and rw for read-write. If omitted when source is specified, rw is used as a default. mode can only be specified if source is given. auto-delete (Optional) Specifies the auto deletion policy of the stateful disk. The following options are available: + never: (Default) Never delete this disk. Instead, detach the disk when its instance is deleted. + on-permanent-instance-deletion: Delete the stateful disk when the instance that it's attached to is permanently deleted from the group; for example, when the instance is deleted manually or when the group size is decreased. |
| `--stateful-external-ip` | [address=ADDRESS],[auto-delete=AUTO-DELETE],[interface-name=INTERFACE-NAME] |  | Managed instance groups preserve stateful IPs on VM autohealing, update, and recreate events. You can preserve the IP address that's specified in a network interface for a specific managed instance, even if that network interface is not defined in the group's instance template. Use this argument multiple times to attach and preserve multiple IPs. interface-name (Optional) Network interface name. If omitted, the default network interface named nic0 is assumed. *address*::: Static IP address to assign to the instance in one of the following formats: + Address: URL of a static IP address reservation. For example: projects/example-project/regions/us-east1/addresses/example-ip-name. + Literal: For example: 130.211.181.55. If the provided IP address is not yet reserved, the managed instance group automatically creates the corresponding IP address reservation. If the provided IP address is reserved, the group assigns the reservation to the instance. auto-delete (Optional) Prescribes what should happen to an associated static Address resource when a VM instance is permanently deleted. Regardless of the value of the delete rule, stateful IP addresses are always preserved on instance autohealing, update, and recreation operations. The following options are available: + never: (Default) Never delete the static IP address. Instead, unassign the address when its instance is permanently deleted and keep the address reserved. + on-permanent-instance-deletion: Delete the static IP address reservation when the instance that it's assigned to is permanently deleted from the instance group; for example, when the instance is deleted manually or when the group size is decreased. |
| `--stateful-internal-ip` | [address=ADDRESS],[auto-delete=AUTO-DELETE],[interface-name=INTERFACE-NAME] |  | Managed instance groups preserve stateful IPs on VM autohealing, update, and recreate events. You can preserve the IP address that's specified in a network interface for a specific managed instance, even if that network interface is not defined in the group's instance template. Use this argument multiple times to attach and preserve multiple IPs. interface-name (Optional) Network interface name. If omitted, the default network interface named nic0 is assumed. *address*::: Static IP address to assign to the instance in one of the following formats: + Address: URL of a static IP address reservation. For example: projects/example-project/regions/us-east1/addresses/example-ip-name. + Literal: For example: 130.211.181.55. If the provided IP address is not yet reserved, the managed instance group automatically creates the corresponding IP address reservation. If the provided IP address is reserved, the group assigns the reservation to the instance. auto-delete (Optional) Prescribes what should happen to an associated static Address resource when a VM instance is permanently deleted. Regardless of the value of the delete rule, stateful IP addresses are always preserved on instance autohealing, update, and recreation operations. The following options are available: + never: (Default) Never delete the static IP address. Instead, unassign the address when its instance is permanently deleted and keep the address reserved. + on-permanent-instance-deletion: Delete the static IP address reservation when the instance that it's assigned to is permanently deleted from the instance group; for example, when the instance is deleted manually or when the group size is decreased. |
| `--stateful-metadata` | KEY=VALUE,[KEY=VALUE,...] |  | Additional metadata to be made available to the guest operating system in addition to the metadata defined in the instance template. Stateful metadata may be used to define a key/value pair specific for the one given instance to differentiate it from the other instances in the managed instance group. Stateful metadata key/value pairs are preserved on instance recreation, autohealing, updates, and any other lifecycle transitions of the instance. Stateful metadata have priority over the metadata defined in the instance template. This means that stateful metadata that is defined for a key that already exists in the instance template overrides the instance template value. Each metadata entry is a key/value pair separated by an equals sign. Metadata keys must be unique and less than 128 bytes in length. Multiple entries can be passed to this flag, e.g., --stateful-metadata key-1=value-1,key-2=value-2,key-3=value-3. |
| `--update-instance` |  |  | Apply the configuration changes immediately to the instance. If you disable this flag, the managed instance group will apply the configuration update when you next recreate or update the instance. Example: say you have an instance with a disk attached to it and you created a stateful configuration for the disk. If you decide to delete the stateful configuration for the disk and you provide this flag, the group immediately refreshes the instance and removes the stateful configuration for the disk. Similarly if you have attached a new disk or changed its definition, with this flag the group immediately refreshes the instance with the new configuration. Enabled by default, use --no-update-instance to disable. |


**Examples:**
```bash
To create a per-instance config with a stateful disk my-disk and to add
stateful metadata my-key:my-value, on instance my-instance, run:

    $ gcloud compute instance-groups managed instance-configs create \
        my-group --region=europe-west4 --instance=my-instance \
        --stateful-disk=device-name=my-disk,source=projects/my-project/\
    zones/us-central1-a/disks/my-disk-3 \
        --stateful-metadata="my-key=my-value"

If my-disk did not exist previously in the per-instance config, and if it
does not exist in the group's instance template, then the command adds
my-disk to my-instance.

To create a per-instance config with a stateful internal IP 192.168.0.10
and a stateful external IP reserved in address my-address, on instance
my-instance, run:

    $ gcloud compute instance-groups managed instance-configs create \
        my-group --region=europe-west4 --instance=my-instance \
        --stateful-internal-ip=address=192.168.0.10,\
    interface-name=nic0 \
        --stateful-external-ip=address=/projects/example-project/\
    regions/europe-west4/addresses/my-address,interface-name=nic0

If the provided IP address is not yet reserved, the MIG automatically
creates a corresponding IP address reservation.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/instance-configs/create)

---
### `gcloud compute instance-groups managed instance-configs delete`

Delete per-instance configs from a managed instance group

gcloud compute instance-groups managed instance-configs delete deletes one
or more per-instance configs from a Google Compute Engine managed instance
group.

Changes are applied immediately to the corresponding instances, by
performing the necessary action (for example, REFRESH), unless overridden
by providing the --no-update-instance flag.

**Synopsis:**
```
gcloud compute instance-groups managed instance-configs delete NAME
    --instances=INSTANCE,[INSTANCE,...]
    [--instance-update-minimal-action=INSTANCE_UPDATE_MINIMAL_ACTION;
      default="none"] [--no-update-instance]
    [--region=REGION | --zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the managed instance group to delete.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instances` | INSTANCE,[INSTANCE,...] |  | Names of instances to delete instance-configs from. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance-update-minimal-action` | one of: none No action refresh Apply the new configuration without stopping VMs, if possible | none | Perform at least this action on the instance while updating, if --update-instance is set to true. INSTANCE_UPDATE_MINIMAL_ACTION must be one of: none No action refresh Apply the new configuration without stopping VMs, if possible. For example, use ``refresh`` to apply changes that only affect metadata or additional disks. restart Apply the new configuration without replacing VMs, if possible. For example, stopping VMs and starting them again is sufficient to apply changes to machine type. replace Replace old VMs according to the --replacement-method flag. |
| `--update-instance` |  |  | Apply the configuration changes immediately to the instance. If you disable this flag, the managed instance group will apply the configuration update when you next recreate or update the instance. Example: say you have an instance with a disk attached to it and you created a stateful configuration for the disk. If you decide to delete the stateful configuration for the disk and you provide this flag, the group immediately refreshes the instance and removes the stateful configuration for the disk. Similarly if you have attached a new disk or changed its definition, with this flag the group immediately refreshes the instance with the new configuration. Enabled by default, use --no-update-instance to disable. |


**Examples:**
```bash
To delete the per-instance config from my-instance, run:

    $ gcloud compute instance-groups managed instance-configs delete \
        my-group --region=europe-west4 --instances=my-instance

This removes all metadata and detaches all disks that were defined in the
per-instance config (except for disks that are also defined in the instance
template, which remain attached).
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/instance-configs/delete)

---
### `gcloud compute instance-groups managed instance-configs list`

List per-instance configs of a managed instance group

gcloud compute instance-groups managed instance-configs list lists
per-instance configs for each instance with preserved resources (like
disks). The list is presented by default in the form of a tree (YAML) due
to a potential for having multiple resources defined in a single
per-instance config.

**Synopsis:**
```
gcloud compute instance-groups managed instance-configs list NAME
    [--region=REGION | --zone=ZONE] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the managed instance group to list instance configs for.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the managed instance group to list instance configs for. If not specified, you might be prompted to select a region (interactive mode only). A list of regions can be fetched by running: $ gcloud compute regions list Overrides the default compute/region property value for this command invocation. |
| `--zone` | ZONE |  | _[At most one of these can be specified:]_ Zone of the managed instance group to list instance configs for. If not specified, you might be prompted to select a zone (interactive mode only). A list of zones can be fetched by running: $ gcloud compute zones list Overrides the default compute/zone property value for this command invocation. |


**Examples:**
```bash
To list all the per-instance configs for the managed instance group
my-group, run:

    $ gcloud compute instance-groups managed instance-configs list \
        my-group --region=europe-west4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/instance-configs/list)

---
### `gcloud compute instance-groups managed instance-configs update`

Update per-instance config of a managed instance group

gcloud compute instance-groups managed instance-configs update updates the
per-instance config of an instance controlled by a Compute Engine managed
instance group. The command lets you change the list of instance-specific
stateful resources, that is, the list of resources that are preserved
during instance restarts and recreations.

Changes are applied immediately to the corresponding instances, by
performing the necessary action (for example, REFRESH), unless overridden
by providing the --no-update-instance flag.

**Synopsis:**
```
gcloud compute instance-groups managed instance-configs update NAME
    --instance=INSTANCE
    [--instance-update-minimal-action=INSTANCE_UPDATE_MINIMAL_ACTION;
      default="none"]
    [--remove-stateful-disks=DEVICE_NAME,[DEVICE_NAME,...]]
    [--remove-stateful-external-ips=KEY,[KEY,...]]
    [--remove-stateful-internal-ips=KEY,[KEY,...]]
    [--remove-stateful-metadata=KEY,[KEY,...]]
    [--stateful-disk=[auto-delete=AUTO-DELETE],
      [device-name=DEVICE-NAME],[mode=MODE],[source=SOURCE]]
    [--stateful-external-ip=[address=ADDRESS],
      [auto-delete=AUTO-DELETE],[interface-name=INTERFACE-NAME]]
    [--stateful-internal-ip=[address=ADDRESS],
      [auto-delete=AUTO-DELETE],[interface-name=INTERFACE-NAME]]
    [--stateful-metadata=KEY=VALUE,[KEY=VALUE,...]] [--no-update-instance]
    [--region=REGION | --zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the managed instance group to update per-instance config for.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE |  | URI/name of an existing instance in the managed instance group. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance-update-minimal-action` | one of: none No action refresh Apply the new configuration without stopping VMs, if possible | none | Perform at least this action on the instance while updating, if --update-instance is set to true. INSTANCE_UPDATE_MINIMAL_ACTION must be one of: none No action refresh Apply the new configuration without stopping VMs, if possible. For example, use ``refresh`` to apply changes that only affect metadata or additional disks. restart Apply the new configuration without replacing VMs, if possible. For example, stopping VMs and starting them again is sufficient to apply changes to machine type. replace Replace old VMs according to the --replacement-method flag. |
| `--remove-stateful-disks` | DEVICE_NAME,[DEVICE_NAME,...] |  | Remove stateful configuration for the specified disks from the instance's configuration. |
| `--remove-stateful-external-ips` | KEY,[KEY,...] |  | List of all stateful IP network interface names to remove from the instance's per-instance configuration. |
| `--remove-stateful-internal-ips` | KEY,[KEY,...] |  | List of all stateful IP network interface names to remove from the instance's per-instance configuration. |
| `--remove-stateful-metadata` | KEY,[KEY,...] |  | Remove stateful configuration for the specified metadata keys from the instance's configuration. |
| `--stateful-disk` | [auto-delete=AUTO-DELETE],[device-name=DEVICE-NAME],[mode=MODE],[source=SOURCE] |  | Disks considered stateful by the instance group. Managed instance groups preserve and reattach stateful disks on VM autohealing, update, and recreate events. You can also attach and preserve disks, not defined in the group's instance template, to a given instance. The same disk can be attached to more than one instance but only in read-only mode. Use this argument multiple times to update multiple disks. If stateful disk with given device-name exists in current instance configuration, its properties will be replaced by the newly provided ones. In other case new stateful disk definition will be added to the instance configuration. device-name Name under which disk is or will be attached. source Optional argument used to specify the URI of an existing persistent disk to attach under specified device-name. mode Specifies the mode of the disk to attach. Supported options are ro for read-only and rw for read-write. If omitted when source is specified, rw is used as a default. mode can only be specified if source is given. auto-delete (Optional) Specifies the auto deletion policy of the stateful disk. The following options are available: + never: (Default) Never delete this disk. Instead, detach the disk when its instance is deleted. + on-permanent-instance-deletion: Delete the stateful disk when the instance that it's attached to is permanently deleted from the group; for example, when the instance is deleted manually or when the group size is decreased. |
| `--stateful-external-ip` | [address=ADDRESS],[auto-delete=AUTO-DELETE],[interface-name=INTERFACE-NAME] |  | Managed instance groups preserve stateful IPs on VM autohealing, update, and recreate events. You can preserve the IP address that's specified in a network interface for a specific managed instance, even if that network interface is not defined in the group's instance template. Use this argument multiple times to update multiple IPs. If a stateful IP with the given network interface name exists in the current per-instance configuration, its properties are replaced by the newly provided ones. Otherwise, a new stateful IP definition is added to the per-instance configuration. interface-name (Optional) Network interface name. If omitted, the default network interface named nic0 is assumed. address (Optional) Static IP address to assign to the instance in one of the following formats: + Address: URL of a static IP address reservation. For example: projects/example-project/regions/us-east1/addresses/example-ip-name. + Literal: For example: 130.211.181.55. If the provided IP address is not yet reserved, the managed instance group automatically creates the corresponding IP address reservation. If the provided IP address is reserved, the group assigns the reservation to the instance. The address flag is optional if an address is already defined in the instance's per-instance configuration. Otherwise it is required. If omitted, the currently configured address remains unchanged. auto-delete (Optional) Prescribes what should happen to an associated static Address resource when a VM instance is permanently deleted. Regardless of the value of the delete rule, stateful IP addresses are always preserved on instance autohealing, update, and recreation operations. The following options are available: + never: (Default) Never delete the static IP address. Instead, unassign the address when its instance is permanently deleted and keep the address reserved. + on-permanent-instance-deletion: Delete the static IP address reservation when the instance that it's assigned to is permanently deleted from the instance group; for example, when the instance is deleted manually or when the group size is decreased. |
| `--stateful-internal-ip` | [address=ADDRESS],[auto-delete=AUTO-DELETE],[interface-name=INTERFACE-NAME] |  | Managed instance groups preserve stateful IPs on VM autohealing, update, and recreate events. You can preserve the IP address that's specified in a network interface for a specific managed instance, even if that network interface is not defined in the group's instance template. Use this argument multiple times to update multiple IPs. If a stateful IP with the given network interface name exists in the current per-instance configuration, its properties are replaced by the newly provided ones. Otherwise, a new stateful IP definition is added to the per-instance configuration. interface-name (Optional) Network interface name. If omitted, the default network interface named nic0 is assumed. address (Optional) Static IP address to assign to the instance in one of the following formats: + Address: URL of a static IP address reservation. For example: projects/example-project/regions/us-east1/addresses/example-ip-name. + Literal: For example: 130.211.181.55. If the provided IP address is not yet reserved, the managed instance group automatically creates the corresponding IP address reservation. If the provided IP address is reserved, the group assigns the reservation to the instance. The address flag is optional if an address is already defined in the instance's per-instance configuration. Otherwise it is required. If omitted, the currently configured address remains unchanged. auto-delete (Optional) Prescribes what should happen to an associated static Address resource when a VM instance is permanently deleted. Regardless of the value of the delete rule, stateful IP addresses are always preserved on instance autohealing, update, and recreation operations. The following options are available: + never: (Default) Never delete the static IP address. Instead, unassign the address when its instance is permanently deleted and keep the address reserved. + on-permanent-instance-deletion: Delete the static IP address reservation when the instance that it's assigned to is permanently deleted from the instance group; for example, when the instance is deleted manually or when the group size is decreased. |
| `--stateful-metadata` | KEY=VALUE,[KEY=VALUE,...] |  | Additional metadata to be made available to the guest operating system in addition to the metadata defined in the instance template. Stateful metadata may be used to define a key/value pair specific for the one given instance to differentiate it from the other instances in the managed instance group. Stateful metadata key/value pairs are preserved on instance recreation, autohealing, updates, and any other lifecycle transitions of the instance. Stateful metadata have priority over the metadata defined in the instance template. This means that stateful metadata that is defined for a key that already exists in the instance template overrides the instance template value. Each metadata entry is a key/value pair separated by an equals sign. Metadata keys must be unique and less than 128 bytes in length. Multiple entries can be passed to this flag, e.g., --stateful-metadata key-1=value-1,key-2=value-2,key-3=value-3. If stateful metadata with the given key exists in current instance configuration, its value will be overridden with the newly provided one. If the key does not exist in the current instance configuration, a new key/value pair will be added. |
| `--update-instance` |  |  | Apply the configuration changes immediately to the instance. If you disable this flag, the managed instance group will apply the configuration update when you next recreate or update the instance. Example: say you have an instance with a disk attached to it and you created a stateful configuration for the disk. If you decide to delete the stateful configuration for the disk and you provide this flag, the group immediately refreshes the instance and removes the stateful configuration for the disk. Similarly if you have attached a new disk or changed its definition, with this flag the group immediately refreshes the instance with the new configuration. Enabled by default, use --no-update-instance to disable. |


**Examples:**
```bash
To updates the stateful disk my-disk-3 to the image provided by source, and
clear my-disk1 and my-disk2 as stateful disks, and to add stateful metadata
my-key: my-value, on instance my-instance, run:

    $ gcloud compute instance-groups managed instance-configs update \
        my-group --region=europe-west4 --instance=my-instance \
        --stateful-disk=device-name=my-disk-3,source=projects/\
    my-project/zones/us-central1-a/disks/my-disk-3 \
        --remove-stateful-disks=my-disk-1,my-disk-2 \
        --stateful-metadata='my-key=my-value'

If my-disk-3 did not exist previously in the per-instance config, and if it
does not exist in the group's instance template, then the command adds
my-disk-3 to my-instance. The command also removes stateful configuration
for my-disk-1 and my-disk-2; if these disk are not defined in the group's
instance template, then they are detached.

To update a per-instance configuration with a stateful internal IP
192.168.0.10, on instance my-instance, run:

    $ gcloud compute instance-groups managed instance-configs update \
        my-group --region=europe-west4 --instance=my-instance \
        --stateful-internal-ip=address=192.168.0.10,interface-name=nic0

To update a per-instance configuration to remove a stateful external IP
that's defined in network interface nic0, on instance my-instance, run:

    $ gcloud compute instance-groups managed instance-configs update \
        my-group --region=europe-west4 --instance=my-instance \
        --remove-stateful-internal-ips=nic0
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/instance-configs/update)

---

## `gcloud compute instance-groups managed resize-requests` — list, create, delete, cancel, and describe ResizeRequests
### `gcloud compute instance-groups managed resize-requests cancel`

Cancel a Compute Engine managed instance group resize request

gcloud compute instance-groups managed resize-requests cancel cancels one
or more Compute Engine managed instance group resize requests.

You can only cancel a resize request when it is in the ACCEPTED state.

**Synopsis:**
```
gcloud compute instance-groups managed resize-requests cancel
    INSTANCE_GROUP_MANAGER --resize-requests=RESIZE_REQUEST_NAMES,[...]
    [--zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_GROUP_MANAGER
   Name of the managed instance group to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--resize-requests` | RESIZE_REQUEST_NAMES,[...] |  | A list of comma-separated names of resize requests to cancel. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the managed instance group to operate on. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To cancel a resize request for a managed instance group, run the following
command:

    $ gcloud compute instance-groups managed resize-requests cancel \
        my-mig --resize-requests=resize-request-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/resize-requests/cancel)

---
### `gcloud compute instance-groups managed resize-requests create`

Create a Compute Engine managed instance group resize request

Create a Compute Engine managed instance group resize request.

**Synopsis:**
```
gcloud compute instance-groups managed resize-requests create
    INSTANCE_GROUP_MANAGER --resize-by=RESIZE_BY
    --resize-request=RESIZE_REQUEST_NAME
    [--requested-run-duration=REQUESTED_RUN_DURATION] [--zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_GROUP_MANAGER
   Name of the managed instance group to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--resize-by` | RESIZE_BY |  | The number of VMs to resize managed instance group by. |
| `--resize-request` | RESIZE_REQUEST_NAME |  | The name of the resize request to create. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--requested-run-duration` | REQUESTED_RUN_DURATION |  | The time you need the requested VMs to run before being automatically deleted. The value must be formatted as the number of days, hours, minutes, or seconds followed by d, h, m, and s respectively. For example, specify 30m for a duration of 30 minutes or 1d2h3m4s for 1 day, 2 hours, 3 minutes, and 4 seconds. The value must be between 10m (10 minutes) and 7d (7 days). If you want the managed instance group to consume a reservation or use FLEX_START provisioning model, then this flag is optional. Otherwise, it's required. |
| `--zone` | ZONE |  | Zone of the managed instance group to operate on. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To create a resize request for a managed instance group, run the following
command:

    $ gcloud compute instance-groups managed resize-requests create \
        my-mig --resize-request=resize-request-1 --resize-by=1 \
        --requested-run-duration=3d1h30s
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/resize-requests/create)

---
### `gcloud compute instance-groups managed resize-requests delete`

Delete a Compute Engine managed instance group resize request

gcloud compute instance-groups managed resize-requests delete deletes one
or more Compute Engine managed instance group resize requests.

You can only delete a request when it is in a state SUCCEEDED, FAILED, or
CANCELLED.

**Synopsis:**
```
gcloud compute instance-groups managed resize-requests delete
    INSTANCE_GROUP_MANAGER --resize-requests=RESIZE_REQUEST_NAMES,[...]
    [--zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_GROUP_MANAGER
   Name of the managed instance group to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--resize-requests` | RESIZE_REQUEST_NAMES,[...] |  | A list of comma-separated names of resize requests to delete. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the managed instance group to operate on. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To delete a resize request for a managed instance group, run the following
command:

    $ gcloud compute instance-groups managed resize-requests delete \
        my-mig --resize-requests=resize-request-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/resize-requests/delete)

---
### `gcloud compute instance-groups managed resize-requests describe`

Describe a Compute Engine managed instance group resize request resource

gcloud compute instance-groups managed resize-requests describe describes a
Compute Engine managed instance group resize request resource.

**Synopsis:**
```
gcloud compute instance-groups managed resize-requests describe
    INSTANCE_GROUP_MANAGER --resize-request=RESIZE_REQUEST_NAME
    [--zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_GROUP_MANAGER
   Name of the managed instance group to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--resize-request` | RESIZE_REQUEST_NAME |  | The name of the resize request to describe. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the managed instance group to operate on. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To describe a resize request for a managed instance group, run the
following command:

    $ gcloud compute instance-groups managed resize-requests describe \
        my-mig --resize-request=resize-request-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/resize-requests/describe)

---
### `gcloud compute instance-groups managed resize-requests list`

List Compute Engine managed instance group resize requests

gcloud compute instance-groups managed resize-requests list displays all
Compute Engine resize requests in a managed instance group.

**Synopsis:**
```
gcloud compute instance-groups managed resize-requests list
    INSTANCE_GROUP_MANAGER [--zone=ZONE] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_GROUP_MANAGER
   Name of the managed instance group to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the managed instance group to operate on. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To list all resize requests in a managed instance group in table form, run:

    $ gcloud compute instance-groups managed resize-requests list \
        example-managed-instance-group --zone=us-central1-a

To list the URIs of all resize requests in a managed instance group, run:

    $ gcloud compute instance-groups managed resize-requests list \
        example-managed-instance-group --zone=us-central1-a --uri
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/resize-requests/list)

---

## `gcloud compute instance-groups managed rolling-action` — manipulate rolling actions on Compute Engine managed instance groups
### `gcloud compute instance-groups managed rolling-action replace`

Replaces instances in a managed instance group

Deletes the existing instance and creates a new instance from the target
template. The Updater creates a brand new instance with all new instance
properties, such as new internal and external IP addresses.

**Synopsis:**
```
gcloud compute instance-groups managed rolling-action replace NAME
    [--max-surge=MAX_SURGE] [--max-unavailable=MAX_UNAVAILABLE]
    [--replacement-method=REPLACEMENT_METHOD]
    [--region=REGION | --zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the managed instance group to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--max-surge` | MAX_SURGE |  | Maximum additional number of instances that can be created during the update process. This can be a fixed number (e.g. 5) or a percentage of size to the managed instance group (e.g. 10%). Defaults to 0 if the managed instance group has stateful configuration, or to the number of zones in which it operates otherwise. |
| `--max-unavailable` | MAX_UNAVAILABLE |  | Maximum number of instances that can be unavailable during the update process. This can be a fixed number (e.g. 5) or a percentage of size to the managed instance group (e.g. 10%). Defaults to the number of zones in which the managed instance group operates. |
| `--replacement-method` | one of: recreate Recreate instances and preserve the instance names |  | Type of replacement method. Specifies what action will be taken to update instances. Defaults to ``recreate`` if the managed instance group has stateful configuration, or to ``substitute`` otherwise. REPLACEMENT_METHOD must be one of: recreate Recreate instances and preserve the instance names. The instance IDs and creation timestamps might change. substitute Delete old instances and create instances with new names. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/rolling-action/replace)

---
### `gcloud compute instance-groups managed rolling-action restart`

Restarts instances in a managed instance group

gcloud compute instance-groups managed rolling-action restart restarts
instances in a managed instance group, effectively performing a stop and
start request. Note, if your request requires that the instance be replaced
to pick up changes, a forced replace will be performed instead.

**Synopsis:**
```
gcloud compute instance-groups managed rolling-action restart NAME
    [--max-unavailable=MAX_UNAVAILABLE] [--region=REGION | --zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the managed instance group to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--max-unavailable` | MAX_UNAVAILABLE |  | Maximum number of instances that can be unavailable during the update process. This can be a fixed number (e.g. 5) or a percentage of size to the managed instance group (e.g. 10%). Defaults to the number of zones in which the managed instance group operates. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/rolling-action/restart)

---
### `gcloud compute instance-groups managed rolling-action start-update`

Updates instances in a managed instance group

gcloud compute instance-groups managed rolling-action start-update updates
instances in a managed instance group, according to the given versions and
the given update policy.

An instance template version can be either a global or regional resource.

**Synopsis:**
```
gcloud compute instance-groups managed rolling-action start-update NAME
    --version=[template=TEMPLATE,[name=NAME],...]
    [--canary-version=[template=TEMPLATE,
      target-size=FIXED_OR_PERCENT,[name=NAME],...]]
    [--type=TYPE; default="proactive"] [--force] [--max-surge=MAX_SURGE]
    [--max-unavailable=MAX_UNAVAILABLE] [--minimal-action=MINIMAL_ACTION]
    [--most-disruptive-allowed-action=MOST_DISRUPTIVE_ALLOWED_ACTION]
    [--replacement-method=REPLACEMENT_METHOD]
    [--region=REGION | --zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the managed instance group to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--version` | [template=TEMPLATE,[name=NAME],...] |  | Original instance template resource to be used. Each version has the following format: template=TEMPLATE,[name=NAME] |


**Examples:**
```bash
Running:

    gcloud compute instance-groups managed rolling-action start-update example-managed-instance-group \
    --version='template=example-global-instance-template'

Sets the group's instance template version to a global instance template
resource 'example-global-instance-template'.

To use a regional instance template, specify the full or partial URL of the
template.

Running:

    gcloud compute instance-groups managed rolling-action start-update example-managed-instance-group \
    --version='template=projects/example-project/regions/us-central1/instanceTemplates/example-regional-instance-template'

Sets the group's instance template version to a regional instance template
resource 'example-regional-instance-template'.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/rolling-action/start-update)

---
### `gcloud compute instance-groups managed rolling-action stop-proactive-update`

Stop the proactive update process of managed instance group

This command changes the update type of the managed instance group to
opportunistic.

**Synopsis:**
```
gcloud compute instance-groups managed rolling-action stop-proactive-update
    NAME [--region=REGION | --zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the managed instance group to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the managed instance group to operate on. If not specified, you might be prompted to select a region (interactive mode only). A list of regions can be fetched by running: $ gcloud compute regions list Overrides the default compute/region property value for this command invocation. |
| `--zone` | ZONE |  | _[At most one of these can be specified:]_ Zone of the managed instance group to operate on. If not specified, you might be prompted to select a zone (interactive mode only). A list of zones can be fetched by running: $ gcloud compute zones list Overrides the default compute/zone property value for this command invocation. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/managed/rolling-action/stop-proactive-update)

---

## `gcloud compute instance-groups unmanaged` — read and manipulate Compute Engine unmanaged instance group
### `gcloud compute instance-groups unmanaged add-instances`

Adds instances to an unmanaged instance group by name

gcloud compute instance-groups unmanaged add-instances adds existing
instances to an unmanaged instance group by name. For example:

    $ gcloud compute instance-groups unmanaged add-instances my-group \
        --instances my-instance-1,my-instance-2 --zone us-central1-a

**Synopsis:**
```
gcloud compute instance-groups unmanaged add-instances NAME
    --instances=INSTANCE,[INSTANCE,...] [--zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the instance group to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instances` | INSTANCE,[INSTANCE,...] |  | A list of names of instances to add to the instance group. These must exist beforehand and must live in the same zone as the instance group. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the instance group to operate on. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/unmanaged/add-instances)

---
### `gcloud compute instance-groups unmanaged create`

Create a Compute Engine unmanaged instance group

gcloud compute instance-groups unmanaged create creates a new Compute
Engine unmanaged instance group. For example:

    $ gcloud compute instance-groups unmanaged create \
        example-instance-group --zone us-central1-a

The above example creates one unmanaged instance group called
'example-instance-group' in the us-central1-a zone.

**Synopsis:**
```
gcloud compute instance-groups unmanaged create NAME
    [--description=DESCRIPTION] [--zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the instance group to create.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Specifies a textual description for the unmanaged instance group. |
| `--zone` | ZONE |  | Zone of the instance group to create. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/unmanaged/create)

---
### `gcloud compute instance-groups unmanaged delete`

Delete Compute Engine unmanaged instance groups

gcloud compute instance-groups unmanaged delete deletes one or more Compute
Engine unmanaged instance groups. This command just deletes the instance
group and does not delete the individual virtual machine instances in the
instance group. For example:

    $ gcloud compute instance-groups unmanaged delete \
        example-instance-group-1 example-instance-group-2 \
        --zone us-central1-a

The above example deletes two instance groups, example-instance-group-1 and
example-instance-group-2, in the us-central1-a zone.

**Synopsis:**
```
gcloud compute instance-groups unmanaged delete NAME [NAME ...]
    [--zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME [NAME ...]
   Names of the instance groups to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the instance groups to delete. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/unmanaged/delete)

---
### `gcloud compute instance-groups unmanaged describe`

Describe an instance group

gcloud compute instance-groups unmanaged describe displays detailed
information about a Google Compute Engine instance group.

**Synopsis:**
```
gcloud compute instance-groups unmanaged describe NAME [--zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the instance group to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the instance group to describe. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/unmanaged/describe)

---
### `gcloud compute instance-groups unmanaged get-named-ports`

Lists the named ports for an instance group resource

Named ports are key:value pairs metadata representing the service name and
the port that it's running on. Named ports can be assigned to an instance
group, which indicates that the service is available on all instances in
the group. This information is used by Application Load Balancers and proxy
Network Load Balancers.

gcloud compute instance-groups unmanaged get-named-ports lists the named
ports (name and port tuples) for an instance group.

**Synopsis:**
```
gcloud compute instance-groups unmanaged get-named-ports NAME [--zone=ZONE]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the instance group to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the instance group to operate on. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
For example, to list named ports for an instance group:

    $ gcloud compute instance-groups unmanaged get-named-ports \
        example-instance-group --zone=us-central1-a

The above example lists named ports assigned to an instance group named
'example-instance-group' in the us-central1-a zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/unmanaged/get-named-ports)

---
### `gcloud compute instance-groups unmanaged list`

List Google Compute Engine unmanaged instance groups

gcloud compute instance-groups unmanaged list displays all Google Compute
Engine unmanaged instance groups in a project.

By default, unmanaged instance groups from all zones are listed. The
results can be narrowed down using a filter: --filter="zone:( ZONE ... )".

**Synopsis:**
```
gcloud compute instance-groups unmanaged list [NAME ...]
    [--regexp=REGEXP, -r REGEXP] [--zones=ZONE,[ZONE,...]]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
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
| `--zones` | ZONE,[ZONE,...] |  | If provided, only resources from the given zones are queried. |


**Examples:**
```bash
To list all unmanaged instance groups in a project in table form, run:

    $ gcloud compute instance-groups unmanaged list

To list the URIs of all unmanaged instance groups in a project, run:

    $ gcloud compute instance-groups unmanaged list --uri

To list all unmanaged instance groups in the us-central1-b and
europe-west1-d zones, run:

    $ gcloud compute instance-groups unmanaged list \
        --filter="zone:( us-central1-b europe-west1-d )"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/unmanaged/list)

---
### `gcloud compute instance-groups unmanaged list-instances`

List instances present in the instance group

gcloud compute instance-groups unmanaged list-instances list instances in
an instance group.

**Synopsis:**
```
gcloud compute instance-groups unmanaged list-instances NAME
    [--regexp=REGEXP, -r REGEXP] [--zone=ZONE] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the instance group to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--regexp` | REGEXP, -r REGEXP |  | A regular expression to filter the names of the results on. Any names that do not match the entire regular expression will be filtered out. |
| `--zone` | ZONE |  | Zone of the instance group to operate on. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/unmanaged/list-instances)

---
### `gcloud compute instance-groups unmanaged remove-instances`

Removes resources from an unmanaged instance group by instance name

gcloud compute instance-groups unmanaged remove-instances removes instances
from an unmanaged instance group using the instance name.

This does not delete the actual instance resources but removes it from the
instance group.

**Synopsis:**
```
gcloud compute instance-groups unmanaged remove-instances NAME
    --instances=INSTANCE,[INSTANCE,...] [--zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the instance group to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instances` | INSTANCE,[INSTANCE,...] |  | The names of the instances to remove from the instance group. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the instance group to operate on. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/unmanaged/remove-instances)

---
### `gcloud compute instance-groups unmanaged set-named-ports`

Sets the list of named ports for an instance group

Named ports are key:value pairs metadata representing the service name and
the port that it's running on. Named ports can be assigned to an instance
group, which indicates that the service is available on all instances in
the group. This information is used by Application Load Balancers and proxy
Network Load Balancers.

gcloud compute instance-groups unmanaged set-named-ports sets the list of
named ports for all instances in an instance group.

Note: Running this command will clear all existing named ports.

**Synopsis:**
```
gcloud compute instance-groups unmanaged set-named-ports NAME
    --named-ports=[NAME:PORT,...] [--zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the instance group to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--named-ports` | [NAME:PORT,...] |  | The comma-separated list of key:value pairs representing the service name and the port that it is running on. To clear the list of named ports pass empty list as flag value. For example: $ gcloud compute instance-groups unmanaged set-named-ports \ example-instance-group --named-ports "" |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the instance group to operate on. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
For example, to apply the named ports to an entire instance group:

    $ gcloud compute instance-groups unmanaged set-named-ports \
        example-instance-group --named-ports=example-service:1111 \
        --zone=us-central1-a

The above example will assign a name 'example-service' for port 1111 to the
instance group called 'example-instance-group' in the us-central1-a zone.
The command removes any named ports that are already set for this instance
group.

To clear named ports from instance group provide empty named ports list as
parameter:

    $ gcloud compute instance-groups unmanaged set-named-ports \
        example-instance-group --named-ports="" --zone=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instance-groups/unmanaged/set-named-ports)

---
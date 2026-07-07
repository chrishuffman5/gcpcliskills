# gcloud workstations configs

manage Cloud Workstations configuration resources

### `gcloud workstations configs create`

Create a workstation configuration

Create a workstation configuration.

**Synopsis:**
```
gcloud workstations configs create
    (CONFIG : --cluster=CLUSTER --region=REGION)
    [--allowed-ports=[ALLOWED_PORTS,...]] [--async]
    [--boot-disk-size=BOOT_DISK_SIZE; default=50]
    [--container-args=[CONTAINER_ARGS,...]]
    [--container-command=[CONTAINER_COMMAND,...]]
    [--container-env=[CONTAINER_ENV,...]]
    [--container-run-as-user=CONTAINER_RUN_AS_USER]
    [--container-working-dir=CONTAINER_WORKING_DIR]
    [--disable-public-ip-addresses] [--disable-ssh-to-vm]
    [--disable-tcp-connections] [--enable-audit-agent]
    [--enable-confidential-compute] [--enable-nested-virtualization]
    [--enable-ssh-to-vm] [--ephemeral-directory=[PROPERTY=VALUE,...]]
    [--grant-workstation-admin-role-on-create]
    [--idle-timeout=IDLE_TIMEOUT; default=7200]
    [--instance-metadata=[INSTANCE_METADATA,...]] [--labels=[LABELS,...]]
    [--machine-type=MACHINE_TYPE; default="e2-standard-4"]
    [--max-usable-workstations-count=MAX_USABLE_WORKSTATIONS_COUNT]
    [--network-tags=[NETWORK_TAGS,...]] [--pool-size=POOL_SIZE]
    [--replica-zones=[REPLICA_ZONES,...]]
    [--running-timeout=RUNNING_TIMEOUT; default=7200]
    [--service-account=SERVICE_ACCOUNT]
    [--service-account-scopes=[SERVICE_ACCOUNT_SCOPES,...]]
    [--shielded-integrity-monitoring] [--shielded-secure-boot]
    [--shielded-vtpm] [--startup-script-uri=STARTUP_SCRIPT_URI]
    [--vm-tags=[VM_TAGS,...]]
    [--accelerator-count=ACCELERATOR_COUNT
      : --accelerator-type=ACCELERATOR_TYPE]
    [--container-custom-image=CONTAINER_CUSTOM_IMAGE
      | --container-predefined-image=CONTAINER_PREDEFINED_IMAGE;
      default="codeoss"]
    [--kms-key=KMS_KEY : --kms-key-service-account=KMS_KEY_SERVICE_ACCOUNT]
    [--no-persistent-storage | --disk-reclaim-policy=DISK_RECLAIM_POLICY;
      default="delete" --disk-type=DISK_TYPE --disk-size=DISK_SIZE
      | --disk-source-snapshot=DISK_SOURCE_SNAPSHOT
      | --pd-disk-type=PD_DISK_TYPE; default="pd-standard"
      --pd-reclaim-policy=PD_RECLAIM_POLICY;
      default="delete" --pd-disk-size=PD_DISK_SIZE; default=200
      | --pd-source-snapshot=PD_SOURCE_SNAPSHOT] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Config resource - The group of arguments defining a config The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument config on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONFIG
     ID of the config or fully qualified identifier for the config.

     To set the config attribute:
     + provide the argument config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     The cluster for the config.

     To set the cluster attribute:
     + provide the argument config on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line;
     + set the property workstations/cluster.

  --region=REGION
     The region for the config.

     To set the region attribute:
     + provide the argument config on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property workstations/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allowed-ports` | [ALLOWED_PORTS,...] |  | A Single or Range of ports externally accessible in the workstation. If not specified defaults to ports 22, 80 and ports 1024-65535. To specify a single port, both first and last should be same. Example: $ gcloud workstations configs create \ --allowed-ports=first=9000,last=9090 $ gcloud workstations configs create --allowed-ports=first=80,last=80 Sets allowed_ports value. first Required, sets first value. last Required, sets last value. Shorthand Example: --allowed-ports=first=int,last=int JSON Example: --allowed-ports='{"first": int, "last": int}' File Example: --allowed-ports=path_to_file.(yaml\|json) |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--boot-disk-size` | BOOT_DISK_SIZE | 50 | Size of the boot disk in GB. |
| `--container-args` | [CONTAINER_ARGS,...] |  | Arguments passed to the entrypoint. Example: $ gcloud workstations configs create --container-args=arg_1,arg_2 |
| `--container-command` | [CONTAINER_COMMAND,...] |  | If set, overrides the default ENTRYPOINT specified by the image. Example: $ gcloud workstations configs create \ --container-command=executable,parameter_1,parameter_2 |
| `--container-env` | [CONTAINER_ENV,...] |  | Environment variables passed to the container. Example: $ gcloud workstations configs create \ --container-env=key1=value1,key2=value2 |
| `--container-run-as-user` | CONTAINER_RUN_AS_USER |  | If set, overrides the USER specified in the image with the given uid. |
| `--container-working-dir` | CONTAINER_WORKING_DIR |  | If set, overrides the default DIR specified by the image. |
| `--disable-public-ip-addresses` |  |  | Default value is false. If set, instances will have no public IP address. |
| `--disable-ssh-to-vm` |  |  | (DEPRECATED) Default value is False. If set, workstations disable SSH connections to the root VM. The --disable-ssh-to-vm option is deprecated; use --enable-ssh-to-vm instead. |
| `--disable-tcp-connections` |  |  | Default value is false. If set, workstations don't allow plain TCP connections. |
| `--enable-audit-agent` |  |  | Whether to enable Linux auditd logging on the workstation. When enabled, a service account must also be specified that has logging.buckets.write permission on the project. |
| `--enable-confidential-compute` |  |  | Default value is false. If set, instances will have confidential compute enabled. |
| `--enable-nested-virtualization` |  |  | Default value is false. If set, instances will have nested virtualization enabled. |
| `--enable-ssh-to-vm` |  |  | Default value is False. If set, workstations enable SSH connections to the root VM. |
| `--ephemeral-directory` | [PROPERTY=VALUE,...] |  | Ephemeral directory which won't persist across workstation sessions. An ephemeral directory is backed by a Compute Engine persistent disk whose mount-path, source-snapshot, source-image, and read-only are configurable. mount-path Location of this directory in the running workstation. source-snapshot Name of the snapshot to use as the source for the disk. Must be empty if [source_image][] is set. Must be empty if [read_only][] is false. Updating [source_snapshot][] will update content in the ephemeral directory after the workstation is restarted. source-image Name of the disk image to use as the source for the disk. Must be empty if [source_snapshot][] is set. Updating [source_image][] will update content in the ephemeral directory after the workstation is restarted. read-only Whether the disk is read only. If true, the disk may be shared by multiple VMs and [source_snapshot][] must be set. Set to false when not specified and true when specified. Example: $ gcloud workstations configs create \ --ephemeral-directory="mount-path=/home2,disk-type=pd-balanced,s\ ource-snapshot=projects/my-project/global/snapshots/snapshot,read-on\ ly=true" |
| `--grant-workstation-admin-role-on-create` |  |  | Default value is false. If set, creator of a workstation will get roles/workstations.policyAdmin role along with roles/workstations.user role on the workstation created by them. |
| `--idle-timeout` | IDLE_TIMEOUT | 7200 | How long (in seconds) to wait before automatically stopping an instance that hasn't received any user traffic. A value of 0 indicates that this instance should never time out due to idleness. |
| `--instance-metadata` | [INSTANCE_METADATA,...] |  | Custom metadata to apply to Compute Engine instances. Example: $ gcloud workstations configs create \ --instance-metadata=key1=value1,key2=value2 |
| `--labels` | [LABELS,...] |  | Labels that are applied to the configuration and propagated to the underlying Compute Engine resources. Example: $ gcloud workstations configs create \ --labels=label1=value1,label2=value2 |
| `--machine-type` | MACHINE_TYPE | e2-standard-4 | Machine type determines the specifications of the Compute Engine machines that the workstations created under this configuration will run on. |
| `--max-usable-workstations-count` | MAX_USABLE_WORKSTATIONS_COUNT |  | Maximum number of workstations under this configuration a user can have workstations.workstation.use permission on. If not specified, defaults to 0, which indicates a user can have unlimited number of workstations under this configuration. |
| `--network-tags` | [NETWORK_TAGS,...] |  | Network tags to add to the Google Compute Engine machines backing the Workstations. Example: $ gcloud workstations configs create --network-tags=tag_1,tag_2 |
| `--pool-size` | POOL_SIZE |  | Number of instances to pool for faster Workstation startup. |
| `--replica-zones` | [REPLICA_ZONES,...] |  | Specifies the zones the VM and disk resources will be replicated within the region. If set, exactly two zones within the workstation cluster's region must be specified. Example: $ gcloud workstations configs create \ --replica-zones=us-central1-a,us-central1-f |
| `--running-timeout` | RUNNING_TIMEOUT | 7200 | How long (in seconds) to wait before automatically stopping a workstation after it started. A value of 0 indicates that workstations using this config should never time out. |
| `--service-account` | SERVICE_ACCOUNT |  | Email address of the service account that will be used on VM instances used to support this config. This service account must have permission to pull the specified container image. If not set, VMs will run without a service account, in which case the image must be publicly accessible. |
| `--service-account-scopes` | [SERVICE_ACCOUNT_SCOPES,...] |  | Scopes to grant to the service_account. Various scopes are automatically added based on feature usage. When specified, users of workstations under this configuration must have iam.serviceAccounts.actAs on the service account. |
| `--shielded-integrity-monitoring` |  |  | Default value is false. If set, instances will have integrity monitoring enabled. |
| `--shielded-secure-boot` |  |  | Default value is false. If set, instances will have Secure Boot enabled. |
| `--shielded-vtpm` |  |  | Default value is false. If set, instances will have vTPM enabled. |
| `--startup-script-uri` | STARTUP_SCRIPT_URI |  | Link to the startup script stored in Cloud Storage. The script is executed on the workstation VM after it is booted. Example: $ gcloud workstations configs create \ --startup-script-uri=gs://{bucket-name}/{object-name} |
| `--vm-tags` | [VM_TAGS,...] |  | Resource manager tags to be bound to the instance. Tag keys and values have the same definition as https://cloud.google.com/resource-manager/docs/tags/tags-overview Example: $ gcloud workstations configs create \ --vm-tags=tagKeys/key1=tagValues/value1,tagKeys/key2=tagValues/\ value2 |


**Examples:**
```bash
To create a configuration with the 'e2-standard-8' machine type and a
IntelliJ image, run:

    $ gcloud workstations configs create CONFIG \
        --machine-type=e2-standard-8 \
        --container-predefined-image=intellij

To create a configuration with a Shielded VM instance that enables Secure
Boot, virtual trusted platform module (vTPM) and integrity monitoring, run:

    $ gcloud workstations configs create CONFIG \
        --machine-type=e2-standard-4 --shielded-secure-boot \
        --shielded-vtpm --shielded-integrity-monitoring

To create a configuration with a non-default persistent disk containing
10GB of PD SSD storage, run:        $ gcloud workstations configs create CONFIG \
        --machine-type=e2-standard-4 --pd-disk-type=pd-ssd \
        --pd-disk-size=10
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workstations/configs/create)

---
### `gcloud workstations configs delete`

Delete a workstation configuration

Delete a workstation configuration.

**Synopsis:**
```
gcloud workstations configs delete
    (CONFIG : --cluster=CLUSTER --region=REGION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Config resource - The name of the configuration to delete. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument config on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONFIG
     ID of the config or fully qualified identifier for the config.

     To set the config attribute:
     + provide the argument config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     The name of the cluster containing the config.

     To set the cluster attribute:
     + provide the argument config on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line;
     + set the property workstations/cluster.

  --region=REGION
     The name of the region of the config.

     To set the region attribute:
     + provide the argument config on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property workstations/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a configuration, run:

    $ gcloud workstations configs delete WORKSTATION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workstations/configs/delete)

---
### `gcloud workstations configs describe`

Describe a config

Describe a config.

**Synopsis:**
```
gcloud workstations configs describe
    (CONFIG : --cluster=CLUSTER --region=REGION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Config resource - The name of the config to display. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument config on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONFIG
     ID of the config or fully qualified identifier for the config.

     To set the config attribute:
     + provide the argument config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     The name of the cluster containing the config.

     To set the cluster attribute:
     + provide the argument config on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line;
     + set the property workstations/cluster.

  --region=REGION
     The name of the region of the config.

     To set the region attribute:
     + provide the argument config on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property workstations/region.
```

**Examples:**
```bash
To describe a config, run:

    $ gcloud workstations configs describe CONFIG
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workstations/configs/describe)

---
### `gcloud workstations configs get-iam-policy`

Get the IAM policy for a configuration

gcloud workstations configs get-iam-policy displays the IAM policy
associated with a given configuration. If formatted as JSON, the output can
be edited and used as a policy file for set-iam-policy. The output includes
an "etag" field identifying the version emitted and allowing detection of
concurrent policy updates; see $ {parent} set-iam-policy for additional
details.

**Synopsis:**
```
gcloud workstations configs get-iam-policy
    (CONFIG : --cluster=CLUSTER --region=REGION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Config resource - The configuration for which to display the IAM policy.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument config on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONFIG
     ID of the config or fully qualified identifier for the config.

     To set the config attribute:
     + provide the argument config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     The name of the cluster containing the config.

     To set the cluster attribute:
     + provide the argument config on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line;
     + set the property workstations/cluster.

  --region=REGION
     The name of the region of the config.

     To set the region attribute:
     + provide the argument config on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property workstations/region.
```

**Examples:**
```bash
To get the IAM policy for a given configuration, run:

    $ gcloud workstations configs get-iam-policy CONFIG
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workstations/configs/get-iam-policy)

---
### `gcloud workstations configs list`

List workstation configurations

List all workstation configurations under the specified cluster.

**Synopsis:**
```
gcloud workstations configs list [--cluster=CLUSTER --region=REGION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cluster` | CLUSTER |  | _[* set the property core/project.]_ ID of the cluster or fully qualified identifier for the cluster. To set the cluster attribute: + provide the argument --cluster on the command line; + set the property workstations/cluster; + default is all clusters . |
| `--region` | REGION |  | _[* set the property core/project.]_ The name of the region of the cluster. To set the region attribute: + provide the argument --cluster on the command line with a fully specified name; + set the property workstations/cluster with a fully specified name; + default is all clusters with a fully specified name; + provide the argument --region on the command line; + set the property workstations/region; + default is all regions . |


**Examples:**
```bash
To list workstation configurations, run:

    $ gcloud workstations configs list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workstations/configs/list)

---
### `gcloud workstations configs set-iam-policy`

Set the IAM policy for a configuration

Sets the IAM policy for the given configuration as defined in a JSON or
YAML file.

**Synopsis:**
```
gcloud workstations configs set-iam-policy
    (CONFIG : --cluster=CLUSTER --region=REGION) POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Config resource - The configuration for which to display the IAM policy.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument config on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONFIG
     ID of the config or fully qualified identifier for the config.

     To set the config attribute:
     + provide the argument config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     The name of the cluster containing the config.

     To set the cluster attribute:
     + provide the argument config on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line;
     + set the property workstations/cluster.

  --region=REGION
     The name of the region of the config.

     To set the region attribute:
     + provide the argument config on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property workstations/region.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command will read an IAM policy defined in a JSON file
'policy.json' and set it for the given configuration:

    $ gcloud workstations configs set-iam-policy CONFIG policy.json

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workstations/configs/set-iam-policy)

---
### `gcloud workstations configs update`

Updates a workstation configuration

Updates a workstation configuration.

**Synopsis:**
```
gcloud workstations configs update
    (CONFIG : --cluster=CLUSTER --region=REGION)
    [--allowed-ports=[ALLOWED_PORTS,...]] [--async]
    [--boot-disk-size=BOOT_DISK_SIZE]
    [--container-args=[CONTAINER_ARGS,...]]
    [--container-command=[CONTAINER_COMMAND,...]]
    [--container-env=[CONTAINER_ENV,...]]
    [--container-run-as-user=CONTAINER_RUN_AS_USER]
    [--container-working-dir=CONTAINER_WORKING_DIR]
    [--disable-public-ip-addresses] [--enable-audit-agent]
    [--enable-confidential-compute] [--enable-nested-virtualization]
    [--grant-workstation-admin-role-on-create]
    [--idle-timeout=IDLE_TIMEOUT]
    [--instance-metadata=[INSTANCE_METADATA,...]] [--labels=[LABELS,...]]
    [--machine-type=MACHINE_TYPE]
    [--max-usable-workstations-count=MAX_USABLE_WORKSTATIONS_COUNT]
    [--network-tags=[NETWORK_TAGS,...]] [--pool-size=POOL_SIZE]
    [--running-timeout=RUNNING_TIMEOUT] [--service-account=SERVICE_ACCOUNT]
    [--service-account-scopes=[SERVICE_ACCOUNT_SCOPES,...]]
    [--shielded-integrity-monitoring] [--shielded-secure-boot]
    [--shielded-vtpm] [--startup-script-uri=STARTUP_SCRIPT_URI]
    [--vm-tags=[VM_TAGS,...]]
    [--accelerator-count=ACCELERATOR_COUNT
      : --accelerator-type=ACCELERATOR_TYPE]
    [--container-custom-image=CONTAINER_CUSTOM_IMAGE
      | --container-predefined-image=CONTAINER_PREDEFINED_IMAGE]
    [--disable-ssh-to-vm | --enable-ssh-to-vm]
    [--disable-tcp-connections | --enable-tcp-connections]
    [--disk-source-snapshot=DISK_SOURCE_SNAPSHOT
      | --pd-source-snapshot=PD_SOURCE_SNAPSHOT
      | --disk-size=DISK_SIZE --disk-type=DISK_TYPE
      | --pd-disk-size=PD_DISK_SIZE
      --pd-disk-type=PD_DISK_TYPE; default="pd-standard"]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Config resource - The group of arguments defining a config The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument config on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONFIG
     ID of the config or fully qualified identifier for the config.

     To set the config attribute:
     + provide the argument config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     The cluster for the config.

     To set the cluster attribute:
     + provide the argument config on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line;
     + set the property workstations/cluster.

  --region=REGION
     The region for the config.

     To set the region attribute:
     + provide the argument config on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property workstations/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allowed-ports` | [ALLOWED_PORTS,...] |  | A Single or Range of ports externally accessible in the workstation. If not specified defaults to ports 22, 80 and ports 1024-65535. To specify a single port, both first and last should be same. Example: $ gcloud workstations configs update \ --allowed-ports=first=9000,last=9090 $ gcloud workstations configs update --allowed-ports=first=80,last=80 Sets allowed_ports value. first Required, sets first value. last Required, sets last value. Shorthand Example: --allowed-ports=first=int,last=int JSON Example: --allowed-ports='{"first": int, "last": int}' File Example: --allowed-ports=path_to_file.(yaml\|json) |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--boot-disk-size` | BOOT_DISK_SIZE |  | Size of the boot disk in GB. |
| `--container-args` | [CONTAINER_ARGS,...] |  | Arguments passed to the entrypoint. Example: $ gcloud workstations configs update --container-args=arg_1,arg_2 |
| `--container-command` | [CONTAINER_COMMAND,...] |  | If set, overrides the default ENTRYPOINT specified by the image. Example: $ gcloud workstations configs update \ --container-command=executable,parameter_1,parameter_2 |
| `--container-env` | [CONTAINER_ENV,...] |  | Environment variables passed to the container. Example: $ gcloud workstations configs update \ --container-env=key1=value1,key2=value2 |
| `--container-run-as-user` | CONTAINER_RUN_AS_USER |  | If set, overrides the USER specified in the image with the given uid. |
| `--container-working-dir` | CONTAINER_WORKING_DIR |  | If set, overrides the default DIR specified by the image. |
| `--disable-public-ip-addresses` |  |  | Default value is false. If set, instances will have no public IP address. |
| `--enable-audit-agent` |  |  | Whether to enable Linux auditd logging on the workstation. When enabled, a service account must also be specified that has logging.buckets.write permission on the project. |
| `--enable-confidential-compute` |  |  | Default value is false. If set, instances will have confidential compute enabled. |
| `--enable-nested-virtualization` |  |  | Default value is false. If set, instances will have nested virtualization enabled. |
| `--grant-workstation-admin-role-on-create` |  |  | Default value is false. If set, creator of a workstation will get roles/workstations.policyAdmin role along with roles/workstations.user role on the workstation created by them. |
| `--idle-timeout` | IDLE_TIMEOUT |  | How long (in seconds) to wait before automatically stopping an instance that hasn't received any user traffic. A value of 0 indicates that this instance should never time out due to idleness. |
| `--instance-metadata` | [INSTANCE_METADATA,...] |  | Custom metadata to apply to Compute Engine instances. Example: $ gcloud workstations configs update \ --instance-metadata=key1=value1,key2=value2 |
| `--labels` | [LABELS,...] |  | Labels that are applied to the configuration and propagated to the underlying Compute Engine resources. Example: $ gcloud workstations configs update \ --labels=label1=value1,label2=value2 |
| `--machine-type` | MACHINE_TYPE |  | Machine type determines the specifications of the Compute Engine machines that the workstations created under this configuration will run on. |
| `--max-usable-workstations-count` | MAX_USABLE_WORKSTATIONS_COUNT |  | Maximum number of workstations under this configuration a user can have workstations.workstation.use permission on. If not specified, defaults to 0, which indicates a user can have unlimited number of workstations under this configuration. |
| `--network-tags` | [NETWORK_TAGS,...] |  | Network tags to add to the Google Compute Engine machines backing the Workstations. Example: $ gcloud workstations configs update --network-tags=tag_1,tag_2 |
| `--pool-size` | POOL_SIZE |  | Number of instances to pool for faster Workstation startup. |
| `--running-timeout` | RUNNING_TIMEOUT |  | How long (in seconds) to wait before automatically stopping a workstation after it started. A value of 0 indicates that workstations using this config should never time out. |
| `--service-account` | SERVICE_ACCOUNT |  | Email address of the service account that will be used on VM instances used to support this config. This service account must have permission to pull the specified container image. If not set, VMs will run without a service account, in which case the image must be publicly accessible. |
| `--service-account-scopes` | [SERVICE_ACCOUNT_SCOPES,...] |  | Scopes to grant to the service_account. Various scopes are automatically added based on feature usage. When specified, users of workstations under this configuration must have iam.serviceAccounts.actAs on the service account. |
| `--shielded-integrity-monitoring` |  |  | Default value is false. If set, instances will have integrity monitoring enabled. |
| `--shielded-secure-boot` |  |  | Default value is false. If set, instances will have Secure Boot enabled. |
| `--shielded-vtpm` |  |  | Default value is false. If set, instances will have vTPM enabled. |
| `--startup-script-uri` | STARTUP_SCRIPT_URI |  | Link to the startup script stored in Cloud Storage. The script is executed on the workstation VM after it is booted. Example: $ gcloud workstations configs update \ --startup-script-uri=gs://{bucket-name}/{object-name} |
| `--vm-tags` | [VM_TAGS,...] |  | Resource manager tags to be bound to the instance. Tag keys and values have the same definition as https://cloud.google.com/resource-manager/docs/tags/tags-overview Example: $ gcloud workstations configs update \ --vm-tags=tagKeys/key1=tagValues/value1,tagKeys/key2=tagValues/\ value2 |


**Examples:**
```bash
To update a configuration with the 'e2-standard-8' machine type and a
IntelliJ image, run:

    $ gcloud workstations configs update CONFIG \
        --machine-type=e2-standard-8 \
        --container-predefined-image=intellij

To update a configuration to disable Secure Boot, virtual trusted platform
module (vTPM) and integrity monitoring, run:

    $ gcloud workstations configs update CONFIG \
        --no-shielded-secure-boot --no-shielded-vtpm \
        --no-shielded-integrity-monitoring
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workstations/configs/update)

---
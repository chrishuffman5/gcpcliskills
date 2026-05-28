# gcloud network-management vpc-flow-logs-configs

manage the VPC Flow Logs configurations

### `gcloud network-management vpc-flow-logs-configs create`

Creates a new VPC Flow Logs configuration

Creates a new VPC Flow Logs configuration.

Project-level configuration: Specify a target resource, either: --subnet,
--network, --interconnect-attachment, or --vpn-tunnel

Organization-level configuration: Specify the --organization flag without a
target resource to apply the configuration across an entire organization.

The --location=global flag is always required.

**Synopsis:**
```
gcloud network-management vpc-flow-logs-configs create
    (VPC_FLOW_LOGS_CONFIG
      : --location=LOCATION --organization=ORGANIZATION)
    [--aggregation-interval=AGGREGATION_INTERVAL] [--async]
    [--cross-project-metadata=CROSS_PROJECT_METADATA]
    [--description=DESCRIPTION] [--filter-expr=FILTER_EXPR]
    [--flow-sampling=FLOW_SAMPLING] [--labels=[LABELS,...]]
    [--metadata=METADATA] [--metadata-fields=[METADATA_FIELDS,...]]
    [--state=STATE]
    [--interconnect-attachment=INTERCONNECT_ATTACHMENT | --network=NETWORK
      | --subnet=SUBNET | --vpn-tunnel=VPN_TUNNEL] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VpcFlowLogsConfig resource - Identifier. Unique name of the configuration.
The name can have one of the following forms:

 * For project-level configurations:
   projects/{project_id}/locations/global/vpcFlowLogsConfigs/{vpc_flow_logs_config_id}

 * For organization-level configurations:
   organizations/{organization_id}/locations/global/vpcFlowLogsConfigs/{vpc_flow_logs_config_id}
   The arguments in this group can be used to specify the attributes of
   this resource. (NOTE) Some attributes are not given arguments in this
   group but can be set in other ways.

To set the project attribute:
 * provide the argument vpc_flow_logs_config on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project. This resource can be one of the
   following types:
   [networkmanagement.organizations.locations.vpcFlowLogsConfigs,
   networkmanagement.projects.locations.vpcFlowLogsConfigs].

This must be specified.

  VPC_FLOW_LOGS_CONFIG
     ID of the vpcFlowLogsConfig or fully qualified identifier for the
     vpcFlowLogsConfig.

     To set the vpc_flow_logs_config attribute:
     + provide the argument vpc_flow_logs_config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the vpcFlowLogsConfig resource.

     To set the location attribute:
     + provide the argument vpc_flow_logs_config on the command line
       with a fully specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The organization id of the vpcFlowLogsConfig resource.

     To set the organization attribute:
     + provide the argument vpc_flow_logs_config on the command line
       with a fully specified name;
     + provide the argument --organization on the command line. Must be
       specified for resource of type
       [networkmanagement.organizations.locations.vpcFlowLogsConfigs].
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--aggregation-interval` | one of: interval-1-min Aggregate logs in 1m intervals |  | _[Arguments for the aggregation interval.]_ The aggregation interval for the logs. Default value is INTERVAL_5_SEC. AGGREGATION_INTERVAL must be one of: interval-1-min Aggregate logs in 1m intervals. interval-10-min Aggregate logs in 10m intervals. interval-15-min Aggregate logs in 15m intervals. interval-30-sec Aggregate logs in 30s intervals. interval-5-min Aggregate logs in 5m intervals. interval-5-sec Aggregate logs in 5s intervals. |
| `--async` |  |  | _[Arguments for the aggregation interval.]_ Return immediately, without waiting for the operation in progress to complete. |
| `--cross-project-metadata` | one of: cross-project-metadata-disabled When CROSS_PROJECT_METADATA_DISABLED, metadata from other projects will not be included in the logs |  | _[Arguments for the cross project metadata.]_ Determines whether to include cross project annotations in the logs. This field is available only for organization configurations. If not specified in org configs will be set to CROSS_PROJECT_METADATA_ENABLED. CROSS_PROJECT_METADATA must be one of: cross-project-metadata-disabled When CROSS_PROJECT_METADATA_DISABLED, metadata from other projects will not be included in the logs. cross-project-metadata-enabled When CROSS_PROJECT_METADATA_ENABLED, metadata from other projects will be included in the logs. |
| `--description` | DESCRIPTION |  | _[Arguments for the description.]_ The user-supplied description of the VPC Flow Logs configuration. Maximum of 512 characters. |
| `--filter-expr` | FILTER_EXPR |  | _[Arguments for the filter expr.]_ Export filter used to define which VPC Flow Logs should be logged. |
| `--flow-sampling` | FLOW_SAMPLING |  | _[Arguments for the flow sampling.]_ The value of the field must be in (0, 1]. The sampling rate of VPC Flow Logs where 1.0 means all collected logs are reported. Setting the sampling rate to 0.0 is not allowed. If you want to disable VPC Flow Logs, use the state field instead. Default value is 1.0. |
| `--labels` | [LABELS,...] |  | _[Arguments for the flow sampling.]_ Resource labels to represent user-provided metadata. KEY Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. VALUE Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Shorthand Example: --labels=string=string JSON Example: --labels='{"string": "string"}' File Example: --labels=path_to_file.(yaml\|json) |
| `--metadata` | one of: custom-metadata Include only custom fields (specified in metadata_fields) |  | _[Arguments for the metadata.]_ Configures whether all, none or a subset of metadata fields should be added to the reported VPC flow logs. Default value is INCLUDE_ALL_METADATA. METADATA must be one of: custom-metadata Include only custom fields (specified in metadata_fields). exclude-all-metadata Exclude all metadata fields. include-all-metadata Include all metadata fields. |
| `--metadata-fields` | [METADATA_FIELDS,...] |  | _[Arguments for the metadata.]_ Custom metadata fields to include in the reported VPC flow logs. Can only be specified if "metadata" was set to CUSTOM_METADATA. |
| `--state` | one of: disabled When DISABLED, this configuration will not generate logs |  | _[Arguments for the state.]_ The state of the VPC Flow Log configuration. Default value is ENABLED. When creating a new configuration, it must be enabled. Setting state=DISABLED will pause the log generation for this config. STATE must be one of: disabled When DISABLED, this configuration will not generate logs. enabled When ENABLED, this configuration will generate logs. |
| `--interconnect-attachment` | INTERCONNECT_ATTACHMENT |  | _[At most one of these can be specified:]_ Traffic will be logged from the Interconnect Attachment. Format: projects/{project_id}/regions/{region}/interconnectAttachments/{name} |
| `--network` | NETWORK |  | _[At most one of these can be specified:]_ Traffic will be logged from VMs, VPN tunnels and Interconnect Attachments within the network. Format: projects/{project_id}/global/networks/{name} |
| `--subnet` | SUBNET |  | _[At most one of these can be specified:]_ Traffic will be logged from VMs within the subnetwork. Format: projects/{project_id}/regions/{region}/subnetworks/{name} |
| `--vpn-tunnel` | VPN_TUNNEL |  | _[At most one of these can be specified:]_ Traffic will be logged from the VPN Tunnel. Format: projects/{project_id}/regions/{region}/vpnTunnels/{name} |


**Examples:**
```bash
To create a new VPC Flow Logs configuration my-config in organization
my-org-number, run:

    $ gcloud network-management vpc-flow-logs-configs create my-config \
        --location=global --organization=<my-org-number>

To create a new VPC Flow Logs configuration my-config in project my-project
for a VLAN attachment for Cloud Interconnect, run:

    $ gcloud network-management vpc-flow-logs-configs create my-config \
        --location=global \
        --interconnect-attachment="projects/{project_id}/regions/{region\
    }/interconnectAttachments/{interconnect_attachment_id}"

To create a new VPC Flow Logs configuration my-config in project my-project
for a Cloud VPN tunnel, run:

    $ gcloud network-management vpc-flow-logs-configs create my-config \
        --location=global \
        --subnet="projects/{project_id}/regions/{region}/vpnTunnels/{vpn\
    _tunnel_id}"

To create a new VPC Flow Logs configuration my-config in project my-project
for a subnet, run:

    $ gcloud network-management vpc-flow-logs-configs create my-config \
        --location=global \
        --subnet="projects/{project_id}/regions/{region}/subnets/{subnet\
    _id}"

To create a new VPC Flow Logs configuration my-config in project my-project
for a VPC network, run:

    $ gcloud network-management vpc-flow-logs-configs create my-config \
        --location=global \
        --network="projects/{project_id}/global/networks/{network_id}"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-management/vpc-flow-logs-configs/create)

---
### `gcloud network-management vpc-flow-logs-configs delete`

Deletes the specified VPC Flow Logs configuration

Deletes the specified VPC Flow Logs configuration.

**Synopsis:**
```
gcloud network-management vpc-flow-logs-configs delete
    (VPC_FLOW_LOGS_CONFIG
      : --location=LOCATION --organization=ORGANIZATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VpcFlowLogsConfig resource - The resource name of the VpcFlowLogsConfig,
in one of the following formats:

 * For a project-level resource:
   projects/{project_id}/locations/global/vpcFlowLogsConfigs/{vpc_flow_logs_config_id}

 * For an organization-level resource:
   organizations/{organization_id}/locations/global/vpcFlowLogsConfigs/{vpc_flow_logs_config_id}
   The arguments in this group can be used to specify the attributes of
   this resource. (NOTE) Some attributes are not given arguments in this
   group but can be set in other ways.

To set the project attribute:
 * provide the argument vpc_flow_logs_config on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project. This resource can be one of the
   following types:
   [networkmanagement.organizations.locations.vpcFlowLogsConfigs,
   networkmanagement.projects.locations.vpcFlowLogsConfigs].

This must be specified.

  VPC_FLOW_LOGS_CONFIG
     ID of the vpcFlowLogsConfig or fully qualified identifier for the
     vpcFlowLogsConfig.

     To set the vpc_flow_logs_config attribute:
     + provide the argument vpc_flow_logs_config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the vpcFlowLogsConfig resource.

     To set the location attribute:
     + provide the argument vpc_flow_logs_config on the command line
       with a fully specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The organization id of the vpcFlowLogsConfig resource.

     To set the organization attribute:
     + provide the argument vpc_flow_logs_config on the command line
       with a fully specified name;
     + provide the argument --organization on the command line. Must be
       specified for resource of type
       [networkmanagement.organizations.locations.vpcFlowLogsConfigs].
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a VPC Flow Logs configuration my-config within the organization
my-org-number, run:

    $ gcloud network-management vpc-flow-logs-configs delete my-config \
        --location=global --organization=<my-org-number>

To delete a VPC Flow Logs configuration my-config, run:

    $ gcloud network-management vpc-flow-logs-configs delete my-config \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-management/vpc-flow-logs-configs/delete)

---
### `gcloud network-management vpc-flow-logs-configs describe`

Describe the details of a specific VPC Flow Logs configuration

Describes the details of a specific VPC Flow Logs configuration.

**Synopsis:**
```
gcloud network-management vpc-flow-logs-configs describe
    (VPC_FLOW_LOGS_CONFIG
      : --location=LOCATION --organization=ORGANIZATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VpcFlowLogsConfig resource - The resource name of the VpcFlowLogsConfig,
in one of the following formats:

 * For project-level resources:
   projects/{project_id}/locations/global/vpcFlowLogsConfigs/{vpc_flow_logs_config_id}

 * For organization-level resources:
   organizations/{organization_id}/locations/global/vpcFlowLogsConfigs/{vpc_flow_logs_config_id}
   The arguments in this group can be used to specify the attributes of
   this resource. (NOTE) Some attributes are not given arguments in this
   group but can be set in other ways.

To set the project attribute:
 * provide the argument vpc_flow_logs_config on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project. This resource can be one of the
   following types:
   [networkmanagement.organizations.locations.vpcFlowLogsConfigs,
   networkmanagement.projects.locations.vpcFlowLogsConfigs].

This must be specified.

  VPC_FLOW_LOGS_CONFIG
     ID of the vpcFlowLogsConfig or fully qualified identifier for the
     vpcFlowLogsConfig.

     To set the vpc_flow_logs_config attribute:
     + provide the argument vpc_flow_logs_config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the vpcFlowLogsConfig resource.

     To set the location attribute:
     + provide the argument vpc_flow_logs_config on the command line
       with a fully specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The organization id of the vpcFlowLogsConfig resource.

     To set the organization attribute:
     + provide the argument vpc_flow_logs_config on the command line
       with a fully specified name;
     + provide the argument --organization on the command line. Must be
       specified for resource of type
       [networkmanagement.organizations.locations.vpcFlowLogsConfigs].
```

**Examples:**
```bash
To get the details of a VPC Flow Logs configuration my-config, within the
organization my-org-number, run:

    $ gcloud network-management vpc-flow-logs-configs describe \
        my-config --location=global --organization=<my-org-number>

To get the details of a VPC Flow Logs configuration my-config, run:

    $ gcloud network-management vpc-flow-logs-configs describe \
        my-config --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-management/vpc-flow-logs-configs/describe)

---
### `gcloud network-management vpc-flow-logs-configs list`

List all VPC Flow Logs configurations

By default, lists all project-level VPC Flow Logs configurations. Use the
--organization flag to list all organization-level configurations.

**Synopsis:**
```
gcloud network-management vpc-flow-logs-configs list
    (--location=LOCATION : --organization=ORGANIZATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--organization` | ORGANIZATION |  | _[This must be specified.]_ The organization id of the location resource. To set the organization attribute: + provide the argument --location on the command line with a fully specified name; + provide the argument --organization on the command line. Must be specified for resource of type [networkmanagement.organizations.locations]. |


**Examples:**
```bash
To list all the VPC Flow Logs configurations within the project, run:

    $ gcloud network-management vpc-flow-logs-configs list \
        --location=global

To list all the VPC Flow Logs configurations within the project with state
'ENABLED', run:

    $ gcloud network-management vpc-flow-logs-configs list \
        --location=global --filter="state:ENABLED"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-management/vpc-flow-logs-configs/list)

---
### `gcloud network-management vpc-flow-logs-configs query-org-vpc-flow-logs-configs`

Fetch all organization-level VPC Flow Logs configurations associated with the project

Fetch all organization-level VPC Flow Logs configurations that the project
is associated with. This method allows you to retrieve which
organization-level configurations are applied to the current project.

**Synopsis:**
```
gcloud network-management vpc-flow-logs-configs
    query-org-vpc-flow-logs-configs --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To fetch all the organization-level VPC Flow Logs configurations associated
with the project, run:

    $ gcloud network-management vpc-flow-logs-configs \
        query-org-vpc-flow-logs-configs --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-management/vpc-flow-logs-configs/query-org-vpc-flow-logs-configs)

---
### `gcloud network-management vpc-flow-logs-configs show-effective-flow-logs-configs`

Show all effective VPC Flow Logs configurations for a resource

Shows all effective VPC Flow Logs configurations for a resource. The
effective configurations include all configurations that apply to the
resource, including inherited ones from parent resources.

**Synopsis:**
```
gcloud network-management vpc-flow-logs-configs
    show-effective-flow-logs-configs --location=LOCATION
    --resource=RESOURCE [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |
| `--resource` | RESOURCE |  | _[This must be specified.]_ The resource to get the effective VPC Flow Logs configuration for. The resource must belong to the same project as the parent. The resource must be a network, subnetwork, interconnect attachment, VPN tunnel, or a project. |


**Examples:**
```bash
To show all effective VPC Flow Logs configurations for a network my-network
in project my-project, run:

    $ gcloud network-management vpc-flow-logs-configs \
        show-effective-flow-logs-configs --location=global \
        --resource="projects/my-project/global/networks/my-network"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-management/vpc-flow-logs-configs/show-effective-flow-logs-configs)

---
### `gcloud network-management vpc-flow-logs-configs update`

Updates one or more fields in an existing VPC Flow Logs configuration

Updates one or more fields in an existing VPC Flow Logs configuration.

**Synopsis:**
```
gcloud network-management vpc-flow-logs-configs update
    (VPC_FLOW_LOGS_CONFIG
      : --location=LOCATION --organization=ORGANIZATION)
    [--aggregation-interval=AGGREGATION_INTERVAL] [--async]
    [--cross-project-metadata=CROSS_PROJECT_METADATA]
    [--description=DESCRIPTION] [--filter-expr=FILTER_EXPR]
    [--flow-sampling=FLOW_SAMPLING] [--metadata=METADATA] [--state=STATE]
    [--interconnect-attachment=INTERCONNECT_ATTACHMENT | --network=NETWORK
      | --subnet=SUBNET | --vpn-tunnel=VPN_TUNNEL]
    [--labels=[LABELS,...]
      | --update-labels=[UPDATE_LABELS,...] --clear-labels
      | --remove-labels=REMOVE_LABELS]
    [--metadata-fields=[METADATA_FIELDS,...]
      | --add-metadata-fields=[ADD_METADATA_FIELDS,...]
      --clear-metadata-fields
      | --remove-metadata-fields=[REMOVE_METADATA_FIELDS,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VpcFlowLogsConfig resource - Identifier. Unique name of the configuration.
The name can have one of the following forms:

 * For project-level configurations:
   projects/{project_id}/locations/global/vpcFlowLogsConfigs/{vpc_flow_logs_config_id}

 * For organization-level configurations:
   organizations/{organization_id}/locations/global/vpcFlowLogsConfigs/{vpc_flow_logs_config_id}
   The arguments in this group can be used to specify the attributes of
   this resource. (NOTE) Some attributes are not given arguments in this
   group but can be set in other ways.

To set the project attribute:
 * provide the argument vpc_flow_logs_config on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project. This resource can be one of the
   following types:
   [networkmanagement.organizations.locations.vpcFlowLogsConfigs,
   networkmanagement.projects.locations.vpcFlowLogsConfigs].

This must be specified.

  VPC_FLOW_LOGS_CONFIG
     ID of the vpcFlowLogsConfig or fully qualified identifier for the
     vpcFlowLogsConfig.

     To set the vpc_flow_logs_config attribute:
     + provide the argument vpc_flow_logs_config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the vpcFlowLogsConfig resource.

     To set the location attribute:
     + provide the argument vpc_flow_logs_config on the command line
       with a fully specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The organization id of the vpcFlowLogsConfig resource.

     To set the organization attribute:
     + provide the argument vpc_flow_logs_config on the command line
       with a fully specified name;
     + provide the argument --organization on the command line. Must be
       specified for resource of type
       [networkmanagement.organizations.locations.vpcFlowLogsConfigs].
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--aggregation-interval` | one of: interval-1-min Aggregate logs in 1m intervals |  | _[Arguments for the aggregation interval.]_ The aggregation interval for the logs. Default value is INTERVAL_5_SEC. AGGREGATION_INTERVAL must be one of: interval-1-min Aggregate logs in 1m intervals. interval-10-min Aggregate logs in 10m intervals. interval-15-min Aggregate logs in 15m intervals. interval-30-sec Aggregate logs in 30s intervals. interval-5-min Aggregate logs in 5m intervals. interval-5-sec Aggregate logs in 5s intervals. |
| `--async` |  |  | _[Arguments for the aggregation interval.]_ Return immediately, without waiting for the operation in progress to complete. |
| `--cross-project-metadata` | one of: cross-project-metadata-disabled When CROSS_PROJECT_METADATA_DISABLED, metadata from other projects will not be included in the logs |  | _[Arguments for the cross project metadata.]_ Determines whether to include cross project annotations in the logs. This field is available only for organization configurations. If not specified in org configs will be set to CROSS_PROJECT_METADATA_ENABLED. CROSS_PROJECT_METADATA must be one of: cross-project-metadata-disabled When CROSS_PROJECT_METADATA_DISABLED, metadata from other projects will not be included in the logs. cross-project-metadata-enabled When CROSS_PROJECT_METADATA_ENABLED, metadata from other projects will be included in the logs. |
| `--description` | DESCRIPTION |  | _[Arguments for the description.]_ The user-supplied description of the VPC Flow Logs configuration. Maximum of 512 characters. |
| `--filter-expr` | FILTER_EXPR |  | _[Arguments for the filter expr.]_ Export filter used to define which VPC Flow Logs should be logged. |
| `--flow-sampling` | FLOW_SAMPLING |  | _[Arguments for the flow sampling.]_ The value of the field must be in (0, 1]. The sampling rate of VPC Flow Logs where 1.0 means all collected logs are reported. Setting the sampling rate to 0.0 is not allowed. If you want to disable VPC Flow Logs, use the state field instead. Default value is 1.0. |
| `--metadata` | one of: custom-metadata Include only custom fields (specified in metadata_fields) |  | _[Arguments for the metadata.]_ Configures whether all, none or a subset of metadata fields should be added to the reported VPC flow logs. Default value is INCLUDE_ALL_METADATA. METADATA must be one of: custom-metadata Include only custom fields (specified in metadata_fields). exclude-all-metadata Exclude all metadata fields. include-all-metadata Include all metadata fields. |
| `--state` | one of: disabled When DISABLED, this configuration will not generate logs |  | _[Arguments for the state.]_ The state of the VPC Flow Log configuration. Default value is ENABLED. When creating a new configuration, it must be enabled. Setting state=DISABLED will pause the log generation for this config. STATE must be one of: disabled When DISABLED, this configuration will not generate logs. enabled When ENABLED, this configuration will generate logs. |
| `--interconnect-attachment` | INTERCONNECT_ATTACHMENT |  | _[At most one of these can be specified:]_ Traffic will be logged from the Interconnect Attachment. Format: projects/{project_id}/regions/{region}/interconnectAttachments/{name} |
| `--network` | NETWORK |  | _[At most one of these can be specified:]_ Traffic will be logged from VMs, VPN tunnels and Interconnect Attachments within the network. Format: projects/{project_id}/global/networks/{name} |
| `--subnet` | SUBNET |  | _[At most one of these can be specified:]_ Traffic will be logged from VMs within the subnetwork. Format: projects/{project_id}/regions/{region}/subnetworks/{name} |
| `--vpn-tunnel` | VPN_TUNNEL |  | _[At most one of these can be specified:]_ Traffic will be logged from the VPN Tunnel. Format: projects/{project_id}/regions/{region}/vpnTunnels/{name} |
| `--labels` | [LABELS,...] |  | _[At most one of these can be specified:]_ Set labels to new value. Resource labels to represent user-provided metadata. KEY Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. VALUE Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Shorthand Example: --labels=string=string JSON Example: --labels='{"string": "string"}' File Example: --labels=path_to_file.(yaml\|json) |
| `--update-labels` | [UPDATE_LABELS,...] |  | _[At most one of these can be specified:]_ Update labels value or add key value pair. Resource labels to represent user-provided metadata. KEY Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. VALUE Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Shorthand Example: --update-labels=string=string JSON Example: --update-labels='{"string": "string"}' File Example: --update-labels=path_to_file.(yaml\|json) |
| `--metadata-fields` | [METADATA_FIELDS,...] |  | _[At most one of these can be specified:]_ Set metadata_fields to new value. |
| `--add-metadata-fields` | [ADD_METADATA_FIELDS,...] |  | _[At most one of these can be specified:]_ Add new value to metadata_fields list. |


**Examples:**
```bash
To update the state field to be 'DISABLED' in the VPC Flow Logs
configuration my-config, run:

    $ gcloud network-management vpc-flow-logs-configs update my-config \
        --location=global --organization=<my-org-number> \
        --state=DISABLED

To update the state field to be 'DISABLED' in the VPC Flow Logs
configuration my-config, run:

    $ gcloud network-management vpc-flow-logs-configs update my-config \
        --location=global --state=DISABLED
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-management/vpc-flow-logs-configs/update)

---
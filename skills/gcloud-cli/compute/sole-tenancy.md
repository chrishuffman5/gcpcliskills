# gcloud compute sole-tenancy

read and manage Compute Engine sole-tenancy resources


## `gcloud compute sole-tenancy node-groups` — read Compute Engine sole-tenancy node groups
### `gcloud compute sole-tenancy node-groups add-iam-policy-binding`

Add IAM policy binding to a Compute Engine node group

Add an IAM policy binding to a Compute Engine node group.

**Synopsis:**
```
gcloud compute sole-tenancy node-groups add-iam-policy-binding
    (NODE_GROUP : --zone=ZONE) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Node group resource - The node group for which to add IAM policy binding
to. The arguments in this group can be used to specify the attributes of
this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument node_group on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NODE_GROUP
     ID of the node_group or fully qualified identifier for the
     node_group.

     To set the node_group attribute:
     + provide the argument node_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     The name of the Google Compute Engine zone.

     To set the zone attribute:
     + provide the argument node_group on the command line with a fully
       specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Examples:**
```bash
To add an IAM policy binding for the role of 'roles/compute.admin' for the
user 'test-user@gmail.com' with node group 'my-node-group' and zone 'ZONE',
run:

    $ gcloud compute sole-tenancy node-groups add-iam-policy-binding \
        my-node-group --zone=ZONE --member='user:test-user@gmail.com' \
        --role='roles/compute.admin'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/sole-tenancy/node-groups/add-iam-policy-binding)

---
### `gcloud compute sole-tenancy node-groups create`

Create a Compute Engine node group

Create a Compute Engine node group.

**Synopsis:**
```
gcloud compute sole-tenancy node-groups create NAME
    --node-template=NODE_TEMPLATE --target-size=TARGET_SIZE
    [--description=DESCRIPTION]
    [--maintenance-interval=MAINTENANCE_INTERVAL]
    [--maintenance-policy=MAINTENANCE_POLICY]
    [--maintenance-window-start-time=START_TIME] [--zone=ZONE]
    [--autoscaler-mode=AUTOSCALER_MODE
      : --max-nodes=MAX_NODES --min-nodes=MIN_NODES]
    [--share-setting=SHARE_SETTING : --share-with=PROJECT,[PROJECT,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the node group to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--node-template` | NODE_TEMPLATE |  | The name of the node template resource to be set for this node group. |
| `--target-size` | TARGET_SIZE |  | The target initial number of nodes in the node group. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional description of this resource. |
| `--maintenance-interval` | one of: as-needed hosts are eligible to receive infrastructure and hypervisor updates as they become available |  | Specifies the frequency of planned maintenance events. MAINTENANCE_INTERVAL must be one of: as-needed hosts are eligible to receive infrastructure and hypervisor updates as they become available. recurrent hosts receive planned infrastructure and hypervisor updates on a periodic basis, but not more frequently than every 28 days. This minimizes the number of planned maintenance operations on individual hosts and reduces the frequency of disruptions, both live migrations and terminations, on individual VMs. |
| `--maintenance-policy` | one of: default VM instances on the host are live migrated to a new physical server |  | Determines the maintenance behavior during host maintenance events. For more information, see https://cloud.google.com/compute/docs/nodes#maintenance_policies. MAINTENANCE_POLICY must be one of: default VM instances on the host are live migrated to a new physical server. This is the default setting. migrate-within-node-group VM instances on the host are live migrated to another node within the same node group. restart-in-place VM instances on the host are terminated and then restarted on the same physical server after the maintenance event has completed. |
| `--maintenance-window-start-time` | START_TIME |  | The time (in GMT) when planned maintenance operations window begins. The possible values are 00:00, 04:00, 08:00, 12:00, 16:00, 20:00. |
| `--zone` | ZONE |  | Zone of the node group to operate on. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To create a node group, run:

    $ gcloud compute sole-tenancy node-groups create my-node-group \
        --node-template=example-template --target-size=4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/sole-tenancy/node-groups/create)

---
### `gcloud compute sole-tenancy node-groups delete`

Delete a Compute Engine node group

Delete a Compute Engine node group.

**Synopsis:**
```
gcloud compute sole-tenancy node-groups delete NAME [--zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the node group to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the node group to operate on. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To delete a node group, run:

    $ gcloud compute sole-tenancy node-groups delete my-node-group
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/sole-tenancy/node-groups/delete)

---
### `gcloud compute sole-tenancy node-groups describe`

Describe a Compute Engine node group

Describe a Compute Engine node group.

**Synopsis:**
```
gcloud compute sole-tenancy node-groups describe NAME [--zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the node group to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the node group to operate on. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To describe a node group, run:

    $ gcloud compute sole-tenancy node-groups describe my-node-group
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/sole-tenancy/node-groups/describe)

---
### `gcloud compute sole-tenancy node-groups get-iam-policy`

Get the IAM policy for a Compute Engine node group

gcloud compute sole-tenancy node-groups get-iam-policy displays the IAM
policy associated with a Compute Engine node group in a zone. If formatted
as JSON, the output can be edited and used as a policy file for
set-iam-policy. The output includes an "etag" field identifying the version
emitted and allowing detection of concurrent policy updates; see $ {parent}
set-iam-policy for additional details.

**Synopsis:**
```
gcloud compute sole-tenancy node-groups get-iam-policy
    (NODE_GROUP : --zone=ZONE) [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Node group resource - The node group for which to display the IAM policy.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument node_group on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NODE_GROUP
     ID of the node_group or fully qualified identifier for the
     node_group.

     To set the node_group attribute:
     + provide the argument node_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     The name of the Google Compute Engine zone.

     To set the zone attribute:
     + provide the argument node_group on the command line with a fully
       specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Examples:**
```bash
To print the IAM policy for a given node group, run:

    $ gcloud compute sole-tenancy node-groups get-iam-policy \
        my-node-group --zone=ZONE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/sole-tenancy/node-groups/get-iam-policy)

---
### `gcloud compute sole-tenancy node-groups list`

List Google Compute Engine node groups

gcloud compute sole-tenancy node-groups list displays all Google Compute
Engine node groups in a project.

By default, node groups from all regions are listed. The results can be
narrowed down using a filter: --filter="region:( REGION ... )".

**Synopsis:**
```
gcloud compute sole-tenancy node-groups list [--share-settings]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--share-settings` |  |  | If provided, shows details for the share setting |


**Examples:**
```bash
To list all node groups in a project in table form, run:

    $ gcloud compute sole-tenancy node-groups list

To list the URIs of all node groups in a project, run:

    $ gcloud compute sole-tenancy node-groups list --uri

To list all node groups in the us-central1 and europe-west1 regions, run:

    $ gcloud compute sole-tenancy node-groups list \
        --filter="region:( us-central1 europe-west1 )"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/sole-tenancy/node-groups/list)

---
### `gcloud compute sole-tenancy node-groups list-nodes`

List Compute Engine sole-tenant nodes present in a nodegroup

List Compute Engine sole-tenant nodes present in a node group.

**Synopsis:**
```
gcloud compute sole-tenancy node-groups list-nodes NAME [--zone=ZONE]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the node group to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the node group to operate on. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To list sole-tenant nodes present in a node group, run:

    $ gcloud compute sole-tenancy node-groups list-nodes my-node-group
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/sole-tenancy/node-groups/list-nodes)

---
### `gcloud compute sole-tenancy node-groups perform-maintenance`

Perform maintenance on nodes in a Compute Engine node group

Perform maintenance on nodes in a Compute Engine node group.

**Synopsis:**
```
gcloud compute sole-tenancy node-groups perform-maintenance NAME
    --nodes=NODE,[NODE,...] [--start-time=START_TIME] [--zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the node group to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--nodes` | NODE,[NODE,...] |  | The names of the nodes to perform maintenance on. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--start-time` | START_TIME |  | The requested time for the maintenance window to start. The timestamp must be an RFC3339 valid string. |
| `--zone` | ZONE |  | Zone of the node group to operate on. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To perform maintenance on nodes in a node group, run:

    $ gcloud compute sole-tenancy node-groups perform-maintenance \
        my-node-group --nodes=node-1,node-2 \
        --start-time=2023-05-01T00:00:00.000-08:00
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/sole-tenancy/node-groups/perform-maintenance)

---
### `gcloud compute sole-tenancy node-groups remove-iam-policy-binding`

Remove IAM policy binding from a Compute Engine node group

Remove an IAM policy binding from a Compute Engine node group.

**Synopsis:**
```
gcloud compute sole-tenancy node-groups remove-iam-policy-binding
    (NODE_GROUP : --zone=ZONE) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Node group resource - The node group for which to remove IAM policy
binding from. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument node_group on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NODE_GROUP
     ID of the node_group or fully qualified identifier for the
     node_group.

     To set the node_group attribute:
     + provide the argument node_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     The name of the Google Compute Engine zone.

     To set the zone attribute:
     + provide the argument node_group on the command line with a fully
       specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Examples:**
```bash
To remove an IAM policy binding for the role of 'roles/compute.admin' for
the user 'test-user@gmail.com' with node group 'my-node-group' and zone
'ZONE', run:

    $ gcloud compute sole-tenancy node-groups \
        remove-iam-policy-binding my-node-group --zone=ZONE \
        --member='user:test-user@gmail.com' --role='roles/compute.admin'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/sole-tenancy/node-groups/remove-iam-policy-binding)

---
### `gcloud compute sole-tenancy node-groups set-iam-policy`

Set the IAM policy for a Compute Engine node group

Sets the IAM policy for the given node group as defined in a JSON or YAML
file.

**Synopsis:**
```
gcloud compute sole-tenancy node-groups set-iam-policy
    (NODE_GROUP : --zone=ZONE) POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Node group resource - The node group to set the IAM policy for. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument node_group on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NODE_GROUP
     ID of the node_group or fully qualified identifier for the
     node_group.

     To set the node_group attribute:
     + provide the argument node_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     The name of the Google Compute Engine zone.

     To set the zone attribute:
     + provide the argument node_group on the command line with a fully
       specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command will read am IAM policy defined in a JSON file
'policy.json' and set it for the node group my-node-group:

    $ gcloud compute sole-tenancy node-groups set-iam-policy \
        my-node-group --zone=ZONE policy.json

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/sole-tenancy/node-groups/set-iam-policy)

---
### `gcloud compute sole-tenancy node-groups simulate-maintenance-event`

Simulate maintenance of a Compute Engine node group

Simulate maintenance of a Compute Engine node group.

**Synopsis:**
```
gcloud compute sole-tenancy node-groups simulate-maintenance-event NAME
    [--async] [--nodes=[NODE,...]] [--zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the node group to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--nodes` | [NODE,...] |  | The names of the nodes to simulate maintenance event. |
| `--zone` | ZONE |  | Zone of the node group to operate on. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To simulate maintenance of a node group, run:

    $ gcloud compute sole-tenancy node-groups \
        simulate-maintenance-event my-node-group --nodes=example-nodes
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/sole-tenancy/node-groups/simulate-maintenance-event)

---
### `gcloud compute sole-tenancy node-groups update`

Update a Compute Engine node group

Update a Compute Engine node group.

**Synopsis:**
```
gcloud compute sole-tenancy node-groups update NAME
    [--node-template=NODE_TEMPLATE] [--zone=ZONE]
    [--add-nodes=ADD_NODES | --delete-nodes=[NODE,...]]
    [--autoscaler-mode=AUTOSCALER_MODE
      --max-nodes=MAX_NODES --min-nodes=MIN_NODES]
    [--share-setting=SHARE_SETTING : --share-with=PROJECT,[PROJECT,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the node group to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--node-template` | NODE_TEMPLATE |  | The name of the node template resource to be set for this node group. |
| `--zone` | ZONE |  | Zone of the node group to operate on. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To update a node group to have two more nodes, run:

    $ gcloud compute sole-tenancy node-groups update my-node-group \
        --add-nodes=2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/sole-tenancy/node-groups/update)

---

## `gcloud compute sole-tenancy node-templates` — read and manage Compute Engine sole-tenancy node templates
### `gcloud compute sole-tenancy node-templates add-iam-policy-binding`

Add IAM policy binding to a Compute Engine node template

Add an IAM policy binding to a Compute Engine node template.

**Synopsis:**
```
gcloud compute sole-tenancy node-templates add-iam-policy-binding
    (NODE_TEMPLATE : --region=REGION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Node template resource - The node template for which to add IAM policy
binding to. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument node_template on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NODE_TEMPLATE
     ID of the node_template or fully qualified identifier for the
     node_template.

     To set the node_template attribute:
     + provide the argument node_template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the Google Compute Engine region.

     To set the region attribute:
     + provide the argument node_template on the command line with a
       fully specified name;
     + provide the argument --region on the command line;
     + set the property compute/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Examples:**
```bash
To add an IAM policy binding for the role of 'roles/compute.admin' for the
user 'test-user@gmail.com' with node template 'my-node-template' and region
'REGION', run:

    $ gcloud compute sole-tenancy node-templates \
        add-iam-policy-binding my-node-template --region=REGION \
        --member='user:test-user@gmail.com' --role='roles/compute.admin'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/sole-tenancy/node-templates/add-iam-policy-binding)

---
### `gcloud compute sole-tenancy node-templates create`

Create a Compute Engine node template

Create a Compute Engine node template.

**Synopsis:**
```
gcloud compute sole-tenancy node-templates create NAME
    (--node-requirements=[localSSD=LOCALSSD],[memory=MEMORY],[vCPU=VCPU]
      | --node-type=NODE_TYPE) [--accelerator=[count=COUNT],[type=TYPE]]
    [--cpu-overcommit-type=CPU_OVERCOMMIT_TYPE] [--description=DESCRIPTION]
    [--disk=[count=COUNT],[size=SIZE],[type=TYPE]]
    [--node-affinity-labels=[KEY=VALUE,...]] [--region=REGION]
    [--server-binding=SERVER_BINDING; default="restart-node-on-any-server"]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the node templates to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--node-requirements` | [localSSD=LOCALSSD],[memory=MEMORY],[vCPU=VCPU] |  | _[Exactly one of these must be specified:]_ The requirements for nodes. Google Compute Engine will automatically choose a node type that fits the requirements on Node Group creation. If multiple node types match your defined criteria, the NodeType with the least amount of each resource will be selected. You can specify 'any' to indicate any non-zero value for a certain resource. The following keys are allowed: vCPU The number of committed cores available to the node. memory The amount of memory available to the node. This value should include unit (eg. 3072MB or 9GB). If no units are specified, MB is assumed. localSSD Optional. The amount of SSD space available on the node. This value should include unit (eg. 3072MB or 9GB). If no units are specified, GB is assumed. If this key is not specified, local SSD is unconstrained. |
| `--node-type` | NODE_TYPE |  | _[Exactly one of these must be specified:]_ The node type to use for nodes in node groups using this template. The type of a node determines what resources are available to instances running on the node. See the following for more information: $ gcloud compute sole-tenancy node-types list |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--accelerator` | [count=COUNT],[type=TYPE] |  | Attaches accelerators (e.g. GPUs) to the node template. type The specific type (e.g. nvidia-tesla-k80 for nVidia Tesla K80) of accelerator to attach to the node template. Use 'gcloud compute accelerator-types list' to learn about all available accelerator types. count Number of accelerators to attach to each node template. The default value is 1. |
| `--cpu-overcommit-type` | one of: enabled, none |  | CPU overcommit type for nodes created based on this template. To overcommit CPUs on a VM, set --cpu-overcommit-type equal to either standard or none, and then when creating a VM, specify a value for the --min-node-cpu flag. Lower values for --min-node-cpu specify a higher overcommit ratio, that is, proportionally more vCPUs in relation to physical CPUs. You can only overcommit CPUs on VMs that are scheduled on nodes that support it. CPU_OVERCOMMIT_TYPE must be one of: enabled, none. |
| `--description` | DESCRIPTION |  | An optional description of this resource. |
| `--disk` | [count=COUNT],[size=SIZE],[type=TYPE] |  | Option to specify disk properties. It is mutually exclusive with '--node-requirements=[localSSD=LOCALSSD]' but '--node-requirements=[memory=MEMORY],[vCPU=VCPU],any' are still available. type Specifies the desired disk type on the node. This disk type must be a local storage type. This should be the name of the disk type. Currently only local-ssd is allowed. size The size of the disk in GiB. Currently you can specify only 375 GiB or no value at all. count Specifies the number of such disks. Set to 16 or 24. |
| `--node-affinity-labels` | [KEY=VALUE,...] |  | Labels to use for node affinity, which will be used in instance scheduling. This corresponds to the --node-affinity flag on compute instances create and compute instance-templates create. |
| `--region` | REGION |  | Region of the node templates to operate on. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--server-binding` | one of: restart-node-on-any-server Nodes using this template will restart on any physical server following a maintenance event | restart-node-on-any-server | The server binding policy for nodes using this template, which determines where the nodes should restart following a maintenance event. SERVER_BINDING must be one of: restart-node-on-any-server Nodes using this template will restart on any physical server following a maintenance event. restart-node-on-minimal-servers Nodes using this template will restart on the same physical server following a maintenance event, instead of being live migrated to or restarted on a new physical server. This means that VMs on such nodes will experience outages while maintenance is applied. This option may be useful if you are using software licenses tied to the underlying server characteristics such as physical sockets or cores, to avoid the need for additional licenses when maintenance occurs. Note that in some cases, Google Compute Engine may need to move your VMs to a new underlying server. During these situations your VMs will be restarted on a new physical server and assigned a new sole tenant physical server ID. |


**Examples:**
```bash
To create a node template of type n1-node-96-624, run:

    $ gcloud compute sole-tenancy node-templates create \
        my-node-template --node-type=n1-node-96-624
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/sole-tenancy/node-templates/create)

---
### `gcloud compute sole-tenancy node-templates delete`

Delete a Compute Engine node template

Delete a Compute Engine node template.

**Synopsis:**
```
gcloud compute sole-tenancy node-templates delete NAME [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the node templates to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the node templates to operate on. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To delete a node template, run:

    $ gcloud compute sole-tenancy node-templates delete my-node-template
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/sole-tenancy/node-templates/delete)

---
### `gcloud compute sole-tenancy node-templates describe`

Describe a Compute Engine node template

Describe a Compute Engine node template.

**Synopsis:**
```
gcloud compute sole-tenancy node-templates describe NAME [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the node templates to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the node templates to operate on. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To describe a node template, run:

    $ gcloud compute sole-tenancy node-templates describe \
        my-node-template
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/sole-tenancy/node-templates/describe)

---
### `gcloud compute sole-tenancy node-templates get-iam-policy`

Get the IAM Policy for a Compute Engine node template

gcloud compute sole-tenancy node-templates get-iam-policy displays the IAM
policy associated with a Compute Engine node template. If formatted as
JSON, the output can be edited and used as a policy file for
set-iam-policy. The output includes an "etag" field identifying the version
emitted and allowing detection of concurrent policy updates; see $ {parent}
set-iam-policy for additional details.

**Synopsis:**
```
gcloud compute sole-tenancy node-templates get-iam-policy
    (NODE_TEMPLATE : --region=REGION) [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Node template resource - The node template for which to display the IAM
policy. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument node_template on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NODE_TEMPLATE
     ID of the node_template or fully qualified identifier for the
     node_template.

     To set the node_template attribute:
     + provide the argument node_template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the Google Compute Engine region.

     To set the region attribute:
     + provide the argument node_template on the command line with a
       fully specified name;
     + provide the argument --region on the command line;
     + set the property compute/region.
```

**Examples:**
```bash
To print the IAM policy for a given node template, run:

    $ gcloud compute sole-tenancy node-templates get-iam-policy \
        my-node-template --region=REGION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/sole-tenancy/node-templates/get-iam-policy)

---
### `gcloud compute sole-tenancy node-templates list`

List Google Compute Engine node templates

gcloud compute sole-tenancy node-templates list displays all Google Compute
Engine node templates in a project.

By default, node templates from all regions are listed. The results can be
narrowed down using a filter: --filter="region:( REGION ... )".

**Synopsis:**
```
gcloud compute sole-tenancy node-templates list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all node templates in a project in table form, run:

    $ gcloud compute sole-tenancy node-templates list

To list the URIs of all node templates in a project, run:

    $ gcloud compute sole-tenancy node-templates list --uri

To list all node templates in the us-central1 and europe-west1 regions,
run:

    $ gcloud compute sole-tenancy node-templates list \
        --filter="region:( us-central1 europe-west1 )"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/sole-tenancy/node-templates/list)

---
### `gcloud compute sole-tenancy node-templates remove-iam-policy-binding`

Remove IAM policy binding from a Compute Engine node template

Remove an IAM policy binding from a Compute Engine node template.

**Synopsis:**
```
gcloud compute sole-tenancy node-templates remove-iam-policy-binding
    (NODE_TEMPLATE : --region=REGION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Node template resource - The node template for which to remove IAM policy
binding from. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument node_template on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NODE_TEMPLATE
     ID of the node_template or fully qualified identifier for the
     node_template.

     To set the node_template attribute:
     + provide the argument node_template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the Google Compute Engine region.

     To set the region attribute:
     + provide the argument node_template on the command line with a
       fully specified name;
     + provide the argument --region on the command line;
     + set the property compute/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Examples:**
```bash
To remove an IAM policy binding for the role of 'roles/compute.admin' for
the user 'test-user@gmail.com' with node template 'my-node-template' and
region 'REGION', run:

    $ gcloud compute sole-tenancy node-templates \
        remove-iam-policy-binding my-node-template --region=REGION \
        --member='user:test-user@gmail.com' --role='roles/compute.admin'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/sole-tenancy/node-templates/remove-iam-policy-binding)

---
### `gcloud compute sole-tenancy node-templates set-iam-policy`

Set the IAM policy for a Compute Engine node template

Sets the IAM policy for the given node template as defined in a JSON or
YAML file.

**Synopsis:**
```
gcloud compute sole-tenancy node-templates set-iam-policy
    (NODE_TEMPLATE : --region=REGION) POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Node template resource - The node template to set the IAM policy for. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument node_template on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NODE_TEMPLATE
     ID of the node_template or fully qualified identifier for the
     node_template.

     To set the node_template attribute:
     + provide the argument node_template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the Google Compute Engine region.

     To set the region attribute:
     + provide the argument node_template on the command line with a
       fully specified name;
     + provide the argument --region on the command line;
     + set the property compute/region.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command will read am IAM policy defined in a JSON file
'policy.json' and set it for the node template my-node-template:

    $ gcloud compute sole-tenancy node-templates set-iam-policy \
        my-node-template --region=REGION policy.json

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/sole-tenancy/node-templates/set-iam-policy)

---

## `gcloud compute sole-tenancy node-types` — read Compute Engine sole-tenancy node types
### `gcloud compute sole-tenancy node-types describe`

Describe a Compute Engine node type

Describe a Compute Engine node type.

**Synopsis:**
```
gcloud compute sole-tenancy node-types describe NAME [--zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the node types to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the node types to operate on. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To describe a node type, run:

    $ gcloud compute sole-tenancy node-types describe example-node-type
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/sole-tenancy/node-types/describe)

---
### `gcloud compute sole-tenancy node-types list`

List Google Compute Engine node types

gcloud compute sole-tenancy node-types list displays all Google Compute
Engine node types in a project.

By default, node types from all zones are listed. The results can be
narrowed down using a filter: --filter="zone:( ZONE ... )".

**Synopsis:**
```
gcloud compute sole-tenancy node-types list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all node types in a project in table form, run:

    $ gcloud compute sole-tenancy node-types list

To list the URIs of all node types in a project, run:

    $ gcloud compute sole-tenancy node-types list --uri

To list all node types in the us-central1-b and europe-west1-d zones, run:

    $ gcloud compute sole-tenancy node-types list \
        --filter="zone:( us-central1-b europe-west1-d )"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/sole-tenancy/node-types/list)

---
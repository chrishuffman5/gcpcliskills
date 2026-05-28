# gcloud compute network-firewall-policies

manage Compute Engine network firewall policies

### `gcloud compute network-firewall-policies clone-rules`

Replace the rules of a Compute Engine network firewall policy with rules from another policy

gcloud compute network-firewall-policies clone-rules is used to replace the
rules of network firewall policies. A network firewall policy is a set of
rules that controls access to various resources.

**Synopsis:**
```
gcloud compute network-firewall-policies clone-rules FIREWALL_POLICY
    --source-firewall-policy=SOURCE_FIREWALL_POLICY
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FIREWALL_POLICY
   name of the network firewall policy to clone the rules to.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source-firewall-policy` | SOURCE_FIREWALL_POLICY |  | Name of the source network firewall policy to copy the rules from. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the firewall policy is global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the firewall policy to clone-rules. Overrides the default compute/region property value for this command invocation. |


**Examples:**
```bash
To clone the rules of a global network firewall policy with NAME my-policy,
from another network firewall policy with NAME source-policy, run:

    $ gcloud compute network-firewall-policies clone-rules my-policy \
        --source-firewall-policy=source-policy --global

To clone the rules of a region network firewall policy with NAME
my-region-policy, in region region-a, from another network firewall policy
with NAME source-policy, run:

    $ gcloud compute network-firewall-policies clone-rules \
        my-region-policy --source-firewall-policy=source-policy \
        --region=region-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/network-firewall-policies/clone-rules)

---
### `gcloud compute network-firewall-policies create`

Create a Compute Engine Network firewall policy

gcloud compute network-firewall-policies create is used to create network
firewall policies. A network firewall policy is a set of rules that
controls access to various resources.

**Synopsis:**
```
gcloud compute network-firewall-policies create FIREWALL_POLICY
    [--description=DESCRIPTION] [--policy-type=POLICY_TYPE]
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FIREWALL_POLICY
   name of the network firewall policy to create.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional, textual description for the network firewall policy. |
| `--policy-type` | one of: VPC_POLICY, RDMA_ROCE_POLICY |  | Network firewall policy type. POLICY_TYPE must be one of: VPC_POLICY, RDMA_ROCE_POLICY. |


**Examples:**
```bash
To create a global network firewall policy named my-policy under project
with ID test-project, run:

    $ gcloud compute network-firewall-policies create my-policy \
        --project=test-project --global

To create a regional network firewall policy named my-region-policy under
project with ID test-project, in region my-region, run:

    $ gcloud compute network-firewall-policies create my-region-policy \
        --project=test-project --region=my-region
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/network-firewall-policies/create)

---
### `gcloud compute network-firewall-policies delete`

Delete a Compute Engine network firewall policy

gcloud compute network-firewall-policies delete is used to delete network
firewall policies. A network firewall policy is a set of rules that
controls access to various resources.

**Synopsis:**
```
gcloud compute network-firewall-policies delete FIREWALL_POLICY
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FIREWALL_POLICY
   name of the network firewall policy to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the firewall policy is global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the firewall policy to delete. Overrides the default compute/region property value for this command invocation. |


**Examples:**
```bash
To delete a global network firewall policy with name my-policy, run:

    $ gcloud compute network-firewall-policies delete my-policy --global

To delete a regional network firewall policy with name my-policy, in region
my-region, run:

    $ gcloud compute network-firewall-policies delete my-policy \
        --region=my-region
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/network-firewall-policies/delete)

---
### `gcloud compute network-firewall-policies describe`

Describe a Compute Engine network firewall policy

gcloud compute network-firewall-policies describe is used to describe
network firewall policies. A network firewall policy is a set of rules that
controls access to various resources.

**Synopsis:**
```
gcloud compute network-firewall-policies describe FIREWALL_POLICY
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FIREWALL_POLICY
   name of the network firewall policy to get.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the firewall policy is global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the firewall policy to get. Overrides the default compute/region property value for this command invocation. |


**Examples:**
```bash
To describe a global network firewall policy with name my-policy, run:

    $ gcloud compute network-firewall-policies describe my-policy \
        --global

To describe a regional network firewall policy with name my-policy, in
region my-region, run:

    $ gcloud compute network-firewall-policies describe my-policy \
        --region=my-region
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/network-firewall-policies/describe)

---
### `gcloud compute network-firewall-policies export-rules`

Export Compute Engine network firewall policy rules

Exports Firewall Policy rules configuration to a file.

**Synopsis:**
```
gcloud compute network-firewall-policies export-rules FIREWALL_POLICY
    [--destination=DESTINATION] [--global | --region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FIREWALL_POLICY
   name of the network firewall policy to export rules from.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | Path to a YAML file where the configuration will be exported. Alternatively, you may omit this flag to write to standard output. For a schema describing the export/import format, see: $CLOUDSDKROOT\lib\googlecloudsdk\schemas\compute\v1\FirewallPolicy.yaml. |


**Examples:**
```bash
Firewall Policy rules can be exported by running:

    $ gcloud compute network-firewall-policies export-rules \
        FIREWALL_POLICY --destination=<path-to-file> --global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/network-firewall-policies/export-rules)

---
### `gcloud compute network-firewall-policies get-effective-firewalls`

Get the effective firewalls for a network

gcloud compute network-firewall-policies get-effective-firewalls is used to
get the effective firewalls applied to the network, including regional
firewalls in a specified region.

**Synopsis:**
```
gcloud compute network-firewall-policies get-effective-firewalls
    --network=NETWORK [--region=REGION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--network` | NETWORK |  | The network to get the effective firewalls for. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | The region to get the effective regional firewalls. |


**Examples:**
```bash
To get the effective firewalls of network with name example-network,
including effective regional firewalls for that network, in region
region-a, run:

    $ gcloud compute network-firewall-policies get-effective-firewalls \
        --network=example-network --region=region-a

To show all fields of the firewall rules, please show in JSON format with
option --format=json

To list more the fields of the rules of network example-network in table
format, run:

    $ gcloud compute network-firewall-policies get-effective-firewalls \
        --network=example-network --region=region-a --format="table(
      type,
      firewall_policy_name,
      rule_type,
      priority,
      action,
      direction,
      ip_ranges.list():label=IP_RANGES,
      target_svc_acct,
      enableLogging,
      description,
      name,
      disabled,
      target_tags,
      src_svc_acct,
      src_tags,
      ruleTupleCount,
      targetResources:label=TARGET_RESOURCES)"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/network-firewall-policies/get-effective-firewalls)

---
### `gcloud compute network-firewall-policies import-rules`

Import a Compute Engine network firewall policy rules

Imports Firewall Policy rules configuration from a file.

**Synopsis:**
```
gcloud compute network-firewall-policies import-rules FIREWALL_POLICY
    [--source=SOURCE] [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FIREWALL_POLICY
   name of the network firewall policy to import rules to.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source` | SOURCE |  | Path to a YAML file containing configuration export data. Alternatively, you may omit this flag to read from standard input. For a schema describing the export/import format, see: $CLOUDSDKROOT\lib\googlecloudsdk\schemas\compute\v1\FirewallPolicy.yaml. Note: $CLOUDSDKROOT represents the Google Cloud CLI's installation directory. |


**Examples:**
```bash
Firewall Policy rules can be imported by running:

    $ gcloud compute network-firewall-policies import-rules \
        FIREWALL_POLICY --source=<path-to-file> --global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/network-firewall-policies/import-rules)

---
### `gcloud compute network-firewall-policies list`

List Compute Engine network firewall policies

gcloud compute network-firewall-policies list is used to list network
firewall policies. A network firewall policy is a set of rules that
controls access to various resources.

**Synopsis:**
```
gcloud compute network-firewall-policies list [NAME ...]
    [--regexp=REGEXP, -r REGEXP] [--global | --regions=[REGION,...]]
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


**Examples:**
```bash
To list global network firewall policies under project my-project, run:

    $ gcloud compute network-firewall-policies list \
        --project=my-project --global

To list regional network firewall policies under project my-project,
specify a list of regions with --regions:

    $ gcloud compute network-firewall-policies list \
        --project=my-project --regions="region-a, region-b"

To list all global and regional network firewall policies under project
my-project, omit --global and --regions:

    $ gcloud compute network-firewall-policies list --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/network-firewall-policies/list)

---
### `gcloud compute network-firewall-policies update`

Update a Compute Engine network firewall policy

gcloud compute network-firewall-policies update is used to update network
firewall policies. A network firewall policy is a set of rules that
controls access to various resources.

**Synopsis:**
```
gcloud compute network-firewall-policies update FIREWALL_POLICY
    [--description=DESCRIPTION] [--global | --region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FIREWALL_POLICY
   name of the network firewall policy to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional, textual description for the network firewall policy. |


**Examples:**
```bash
To update a global network firewall policy with name my-policy, to change
the description to New description, run:

    $ gcloud compute network-firewall-policies update my-policy \
        --description='New description' --global

To update a regional network firewall policy with name my-policy, in region
my-region, to change the description to New description, run:

    $ gcloud compute network-firewall-policies update my-policy \
        --description='New description' --region=my-region
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/network-firewall-policies/update)

---

## `gcloud compute network-firewall-policies associations` — read and manipulate Compute Engine network firewall policy associations
### `gcloud compute network-firewall-policies associations create`

Create a new association between a firewall policy and a network

gcloud compute network-firewall-policies associations create is used to
create network firewall policy associations. A network firewall policy is a
set of rules that controls access to various resources.

**Synopsis:**
```
gcloud compute network-firewall-policies associations create
    --firewall-policy=FIREWALL_POLICY --network=NETWORK [--name=NAME]
    [--replace-association-on-target]
    [--firewall-policy-region=FIREWALL_POLICY_REGION
      | --global-firewall-policy] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--firewall-policy` | FIREWALL_POLICY |  | Firewall policy ID with which to create association. |
| `--network` | NETWORK |  | Name of the network with which the association is created. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--name` | NAME |  | Name of the association. |
| `--replace-association-on-target` |  |  | By default, if you attempt to insert an association to a network that is already associated with a firewall policy the method will fail. If this is set, the existing association will be deleted at the same time that the new association is created. |


**Examples:**
```bash
To associate a global network firewall policy with name my-policy to
network my-network with an association named my-association, run:

    $ gcloud compute network-firewall-policies associations create \
        --firewall-policy=my-policy --network=my-network \
        --name=my-association --global-firewall-policy

To associate a network firewall policy with name my-region-policy in region
region-a to network my-network with an association named my-association,
run:

    $ gcloud compute network-firewall-policies associations create \
        --firewall-policy=my-policy --network=my-network \
        --name=my-association --firewall-policy-region=region-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/network-firewall-policies/associations/create)

---
### `gcloud compute network-firewall-policies associations delete`

Delete a new association between a firewall policy and an network or folder resource

gcloud compute network-firewall-policies associations delete is used to
delete network firewall policy associations. An network firewall policy is
a set of rules that controls access to various resources.

**Synopsis:**
```
gcloud compute network-firewall-policies associations delete
    --firewall-policy=FIREWALL_POLICY --name=NAME
    [--firewall-policy-region=FIREWALL_POLICY_REGION
      | --global-firewall-policy] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--firewall-policy` | FIREWALL_POLICY |  | Firewall policy ID with which to delete association. |
| `--name` | NAME |  | Name of the association to delete. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--firewall-policy-region` | FIREWALL_POLICY_REGION |  | _[At most one of these can be specified:]_ Region of the firewall policy to delete. Overrides the default compute/region property value for this command invocation. |
| `--global-firewall-policy` |  |  | _[At most one of these can be specified:]_ If set, the firewall policy is global. |


**Examples:**
```bash
To delete an association from a global network firewall policy with NAME
my-policy and association name my-association, run:

    $ gcloud compute network-firewall-policies associations delete \
        --firewall-policy=my-policy --name=my-association \
        --global-firewall-policy

To delete an association from a regional network firewall policy with NAME
my-policy in region region-a and association name my-association, run:

    $ gcloud compute network-firewall-policies associations delete \
        --firewall-policy=my-policy --name=my-association \
        --firewall-policy-region=region-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/network-firewall-policies/associations/delete)

---

## `gcloud compute network-firewall-policies mirroring-rules` — read and manipulate Compute Engine packet mirroring rules in network firewall policy
### `gcloud compute network-firewall-policies mirroring-rules create`

Creates a Compute Engine network firewall policy packet mirroring rule

gcloud compute network-firewall-policies mirroring-rules create is used to
create network firewall policy packet mirroring rules.

**Synopsis:**
```
gcloud compute network-firewall-policies mirroring-rules create PRIORITY
    --action=ACTION --firewall-policy=FIREWALL_POLICY
    --global-firewall-policy --layer4-configs=[LAYER4_CONFIG,...]
    [--description=DESCRIPTION] [--dest-ip-ranges=[DEST_IP_RANGE,...]]
    [--direction=DIRECTION] [--[no-]disabled]
    [--security-profile-group=SECURITY_PROFILE_GROUP]
    [--src-ip-ranges=[SRC_IP_RANGE,...]]
    [--target-secure-tags=[TARGET_SECURE_TAGS,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PRIORITY
   Priority of the rule to be inserted. Valid in [0, 2147483547].
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--action` | one of: mirror, do_not_mirror, goto_next |  | Action to take if the request matches the match condition. ACTION must be one of: mirror, do_not_mirror, goto_next. |
| `--firewall-policy` | FIREWALL_POLICY |  | Firewall policy ID with which to create rule. |
| `--global-firewall-policy` |  |  | Use this flag to indicate that firewall policy is global. |
| `--layer4-configs` | [LAYER4_CONFIG,...] |  | A list of destination protocols and ports to which the firewall rule will apply. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional, textual description for the rule. |
| `--dest-ip-ranges` | [DEST_IP_RANGE,...] |  | Destination IP ranges to match for this rule. |
| `--direction` | one of: INGRESS, EGRESS |  | Direction of the traffic the rule is applied. The default is to apply on incoming traffic. DIRECTION must be one of: INGRESS, EGRESS. |
| `--[no-]disabled` |  |  | Use this flag to disable the rule. Disabled rules will not affect traffic. Use --disabled to enable and --no-disabled to disable. |
| `--security-profile-group` | SECURITY_PROFILE_GROUP |  | A security profile group to be used with mirror action. |
| `--src-ip-ranges` | [SRC_IP_RANGE,...] |  | A list of IP address blocks that are allowed to make inbound connections that match the firewall rule to the instances on the network. The IP address blocks must be specified in CIDR format: http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing.Either --src-ip-ranges or --src-secure-tags must be specified for INGRESS traffic. If both --src-ip-ranges and --src-secure-tags are specified, the rule matches if either the range of the source matches --src-ip-ranges or the secure tag of the source matches --src-secure-tags.Multiple IP address blocks can be specified if they are separated by commas. |
| `--target-secure-tags` | [TARGET_SECURE_TAGS,...] |  | An optional, list of target secure tags with a name of the format tagValues/ or full namespaced name |


**Examples:**
```bash
To create a rule with priority 10 in a global network firewall policy with
name my-policy and description example rule, run:

    $ gcloud compute network-firewall-policies mirroring-rules create \
      10 --firewall-policy=my-policy --action=do_not_mirror \
      --description="example rule" --global-firewall-policy
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/network-firewall-policies/mirroring-rules/create)

---
### `gcloud compute network-firewall-policies mirroring-rules delete`

Deletes a Compute Engine network firewall policy packet mirroirng rule

gcloud compute network-firewall-policies mirroring-rules delete is used to
delete network firewall policy packet mirroring rules.

**Synopsis:**
```
gcloud compute network-firewall-policies mirroring-rules delete PRIORITY
    --firewall-policy=FIREWALL_POLICY --global-firewall-policy
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PRIORITY
   Priority of the rule to be deleted. Valid in [0, 2147483547].
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--firewall-policy` | FIREWALL_POLICY |  | Firewall policy ID with which to delete rule. |
| `--global-firewall-policy` |  |  | Use this flag to indicate that firewall policy is global. |


**Examples:**
```bash
To delete a rule with priority 10 in a global network firewall policy with
name my-policy, run:

    $ gcloud compute network-firewall-policies mirroring-rules delete \
        10 --firewall-policy=my-policy --global-firewall-policy
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/network-firewall-policies/mirroring-rules/delete)

---
### `gcloud compute network-firewall-policies mirroring-rules describe`

Describes a Compute Engine network firewall policy pakcet mirroring rule

gcloud compute network-firewall-policies mirroring-rules describe is used
to describe network firewall policy packet mirroring rules.

**Synopsis:**
```
gcloud compute network-firewall-policies mirroring-rules describe PRIORITY
    --firewall-policy=FIREWALL_POLICY --global-firewall-policy
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PRIORITY
   Priority of the rule to be described. Valid in [0, 2147483547].
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--firewall-policy` | FIREWALL_POLICY |  | Firewall policy ID with which to describe rule. |
| `--global-firewall-policy` |  |  | Use this flag to indicate that firewall policy is global. |


**Examples:**
```bash
To describe a rule with priority 10 in a global network firewall policy
with name my-policy, run:

    $ gcloud compute network-firewall-policies mirroring-rules \
        describe 10 --firewall-policy=my-policy --global-firewall-policy
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/network-firewall-policies/mirroring-rules/describe)

---
### `gcloud compute network-firewall-policies mirroring-rules update`

Updates a Compute Engine network firewall policy packet mirroring rule

gcloud compute network-firewall-policies mirroring-rules update is used to
update network firewall policy packet mirroring rules.

**Synopsis:**
```
gcloud compute network-firewall-policies mirroring-rules update PRIORITY
    --firewall-policy=FIREWALL_POLICY --global-firewall-policy
    [--action=ACTION] [--description=DESCRIPTION]
    [--dest-ip-ranges=[DEST_IP_RANGE,...]] [--direction=DIRECTION]
    [--[no-]disabled] [--layer4-configs=[LAYER4_CONFIG,...]]
    [--new-priority=NEW_PRIORITY]
    [--security-profile-group=SECURITY_PROFILE_GROUP]
    [--src-ip-ranges=[SRC_IP_RANGE,...]]
    [--target-secure-tags=[TARGET_SECURE_TAGS,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PRIORITY
   Priority of the rule to be updated. Valid in [0, 2147483547].
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--firewall-policy` | FIREWALL_POLICY |  | Firewall policy ID with which to update rule. |
| `--global-firewall-policy` |  |  | Use this flag to indicate that firewall policy is global. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--action` | one of: mirror, do_not_mirror, goto_next |  | Action to take if the request matches the match condition. ACTION must be one of: mirror, do_not_mirror, goto_next. |
| `--description` | DESCRIPTION |  | An optional, textual description for the rule. |
| `--dest-ip-ranges` | [DEST_IP_RANGE,...] |  | Destination IP ranges to match for this rule. |
| `--direction` | one of: INGRESS, EGRESS |  | Direction of the traffic the rule is applied. The default is to apply on incoming traffic. DIRECTION must be one of: INGRESS, EGRESS. |
| `--[no-]disabled` |  |  | Use this flag to disable the rule. Disabled rules will not affect traffic. Use --disabled to enable and --no-disabled to disable. |
| `--layer4-configs` | [LAYER4_CONFIG,...] |  | A list of destination protocols and ports to which the firewall rule will apply. |
| `--new-priority` | NEW_PRIORITY |  | New priority for the rule to update. Valid in [0, 65535]. |
| `--security-profile-group` | SECURITY_PROFILE_GROUP |  | A security profile group to be used with mirror action. |
| `--src-ip-ranges` | [SRC_IP_RANGE,...] |  | A list of IP address blocks that are allowed to make inbound connections that match the firewall rule to the instances on the network. The IP address blocks must be specified in CIDR format: http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing.Either --src-ip-ranges or --src-secure-tags must be specified for INGRESS traffic. If both --src-ip-ranges and --src-secure-tags are specified, the rule matches if either the range of the source matches --src-ip-ranges or the secure tag of the source matches --src-secure-tags.Multiple IP address blocks can be specified if they are separated by commas. |
| `--target-secure-tags` | [TARGET_SECURE_TAGS,...] |  | An optional, list of target secure tags with a name of the format tagValues/ or full namespaced name |


**Examples:**
```bash
To update a rule with priority 10 in a global network firewall policy with
name my-policy to change the action to mirror and description to new
example rule, run:

    $ gcloud compute network-firewall-policies mirroring-rules update \
        10 --firewall-policy=my-policy --action=mirror \
        --description="new example rule"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/network-firewall-policies/mirroring-rules/update)

---

## `gcloud compute network-firewall-policies rules` — read and manipulate Compute Engine network firewall policy rules
### `gcloud compute network-firewall-policies rules create`

Creates a Compute Engine network firewall policy rule

gcloud compute network-firewall-policies rules create is used to create
network firewall policy rules.

**Synopsis:**
```
gcloud compute network-firewall-policies rules create PRIORITY
    --action=ACTION --firewall-policy=FIREWALL_POLICY
    --layer4-configs=[LAYER4_CONFIG,...] [--description=DESCRIPTION]
    [--dest-address-groups=[DEST_ADDRESS_GROUPS,...]]
    [--dest-fqdns=[DEST_FQDNS,...]] [--dest-ip-ranges=[DEST_IP_RANGE,...]]
    [--dest-region-codes=[DEST_REGION_CODES,...]]
    [--dest-threat-intelligence=[DEST_THREAT_INTELLIGENCE_LISTS,...]]
    [--direction=DIRECTION] [--[no-]disabled] [--[no-]enable-logging]
    [--security-profile-group=SECURITY_PROFILE_GROUP]
    [--src-address-groups=[SOURCE_ADDRESS_GROUPS,...]]
    [--src-fqdns=[SOURCE_FQDNS,...]] [--src-ip-ranges=[SRC_IP_RANGE,...]]
    [--src-region-codes=[SOURCE_REGION_CODES,...]]
    [--src-secure-tags=[SOURCE_SECURE_TAGS,...]]
    [--src-threat-intelligence=[SOURCE_THREAT_INTELLIGENCE_LISTS,...]]
    [--target-secure-tags=[TARGET_SECURE_TAGS,...]]
    [--target-service-accounts=[TARGET_SERVICE_ACCOUNTS,...]]
    [--[no-]tls-inspect]
    [--firewall-policy-region=FIREWALL_POLICY_REGION
      | --global-firewall-policy] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PRIORITY
   Priority of the rule to be inserted. Valid in [0, 2147483547].
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--action` | one of: allow, deny, goto_next, apply_security_profile_group |  | Action to take if the request matches the match condition. ACTION must be one of: allow, deny, goto_next, apply_security_profile_group. |
| `--firewall-policy` | FIREWALL_POLICY |  | Firewall policy ID with which to create rule. |
| `--layer4-configs` | [LAYER4_CONFIG,...] |  | A list of destination protocols and ports to which the firewall rule will apply. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional, textual description for the rule. |
| `--dest-address-groups` | [DEST_ADDRESS_GROUPS,...] |  | Destination address groups to match for this rule. Can only be specified if DIRECTION is engress. |
| `--dest-fqdns` | [DEST_FQDNS,...] |  | Destination FQDNs to match for this rule. Can only be specified if DIRECTION is egress. |
| `--dest-ip-ranges` | [DEST_IP_RANGE,...] |  | Destination IP ranges to match for this rule. |
| `--dest-region-codes` | [DEST_REGION_CODES,...] |  | Destination Region Code to match for this rule. Can only be specified if DIRECTION is egress. |
| `--dest-threat-intelligence` | [DEST_THREAT_INTELLIGENCE_LISTS,...] |  | Destination Threat Intelligence lists to match for this rule. Can only be specified if DIRECTION is egress. The available lists can be found here: https://cloud.google.com/vpc/docs/firewall-policies-rule-details#threat-intelligence-fw-policy. |
| `--direction` | one of: INGRESS, EGRESS |  | Direction of the traffic the rule is applied. The default is to apply on incoming traffic. DIRECTION must be one of: INGRESS, EGRESS. |
| `--[no-]disabled` |  |  | Use this flag to disable the rule. Disabled rules will not affect traffic. Use --disabled to enable and --no-disabled to disable. |
| `--[no-]enable-logging` |  |  | Use this flag to enable logging of connections that allowed or denied by this rule. Use --enable-logging to enable and --no-enable-logging to disable. |
| `--security-profile-group` | SECURITY_PROFILE_GROUP |  | A security profile group to be used with apply_security_profile_group action. |
| `--src-address-groups` | [SOURCE_ADDRESS_GROUPS,...] |  | Source address groups to match for this rule. Can only be specified if DIRECTION is ingress. |
| `--src-fqdns` | [SOURCE_FQDNS,...] |  | Source FQDNs to match for this rule. Can only be specified if DIRECTION is ingress. |
| `--src-ip-ranges` | [SRC_IP_RANGE,...] |  | A list of IP address blocks that are allowed to make inbound connections that match the firewall rule to the instances on the network. The IP address blocks must be specified in CIDR format: http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing.Either --src-ip-ranges or --src-secure-tags must be specified for INGRESS traffic. If both --src-ip-ranges and --src-secure-tags are specified, the rule matches if either the range of the source matches --src-ip-ranges or the secure tag of the source matches --src-secure-tags.Multiple IP address blocks can be specified if they are separated by commas. |
| `--src-region-codes` | [SOURCE_REGION_CODES,...] |  | Source Region Code to match for this rule. Can only be specified if DIRECTION is ingress. |
| `--src-secure-tags` | [SOURCE_SECURE_TAGS,...] |  | A list of instance secure tags indicating the set of instances on the network to which the rule applies if all other fields match. Either --src-ip-ranges or --src-secure-tags must be specified for ingress traffic. If both --src-ip-ranges and --src-secure-tags are specified, an inbound connection is allowed if either the range of the source matches --src-ip-ranges or the tag of the source matches --src-secure-tags. Secure Tags can be assigned to instances during instance creation. |
| `--src-threat-intelligence` | [SOURCE_THREAT_INTELLIGENCE_LISTS,...] |  | Source Threat Intelligence lists to match for this rule. Can only be specified if DIRECTION is ingress. The available lists can be found here: https://cloud.google.com/vpc/docs/firewall-policies-rule-details#threat-intelligence-fw-policy. |
| `--target-secure-tags` | [TARGET_SECURE_TAGS,...] |  | An optional, list of target secure tags with a name of the format tagValues/ or full namespaced name |
| `--target-service-accounts` | [TARGET_SERVICE_ACCOUNTS,...] |  | List of target service accounts for the rule. |
| `--[no-]tls-inspect` |  |  | Use this flag to indicate whether TLS traffic should be inspected using the TLS inspection policy when the security profile group is applied. Default: no TLS inspection. Use --tls-inspect to enable and --no-tls-inspect to disable. |


**Examples:**
```bash
To create a rule with priority 10 in a global network firewall policy with
name my-policy and description example rule, run:

    $ gcloud compute network-firewall-policies rules create 10 \
      --firewall-policy=my-policy --action=allow \
      --description="example rule" --global-firewall-policy

To create a rule with priority 10 in a regional network firewall policy
with name my-region-policy and description example rule, in region
region-a, run:

    $ gcloud compute network-firewall-policies rules create 10 \
      --firewall-policy=my-policy --action=allow \
      --description="example rule"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/network-firewall-policies/rules/create)

---
### `gcloud compute network-firewall-policies rules delete`

Deletes a Compute Engine network firewall policy rule

gcloud compute network-firewall-policies rules delete is used to delete
network firewall policy rules.

**Synopsis:**
```
gcloud compute network-firewall-policies rules delete PRIORITY
    --firewall-policy=FIREWALL_POLICY
    [--firewall-policy-region=FIREWALL_POLICY_REGION
      | --global-firewall-policy] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PRIORITY
   Priority of the rule to be deleted. Valid in [0, 2147483547].
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--firewall-policy` | FIREWALL_POLICY |  | Firewall policy ID with which to delete rule. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--firewall-policy-region` | FIREWALL_POLICY_REGION |  | _[At most one of these can be specified:]_ Region of the firewall policy to delete. Overrides the default compute/region property value for this command invocation. |
| `--global-firewall-policy` |  |  | _[At most one of these can be specified:]_ If set, the firewall policy is global. |


**Examples:**
```bash
To delete a rule with priority 10 in a global network firewall policy with
name my-policy, run:

    $ gcloud compute network-firewall-policies rules delete 10 \
        --firewall-policy=my-policy --global-firewall-policy

To delete a rule with priority 10 in a regional network firewall policy
with name my-policy, in region region-a, run:

    $ gcloud compute network-firewall-policies rules delete 10 \
        --firewall-policy=my-policy --firewall-policy-region=region-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/network-firewall-policies/rules/delete)

---
### `gcloud compute network-firewall-policies rules describe`

Describes a Compute Engine network firewall policy rule

gcloud compute network-firewall-policies rules describe is used to describe
network firewall policy rules.

**Synopsis:**
```
gcloud compute network-firewall-policies rules describe PRIORITY
    --firewall-policy=FIREWALL_POLICY
    [--firewall-policy-region=FIREWALL_POLICY_REGION
      | --global-firewall-policy] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PRIORITY
   Priority of the rule to be described. Valid in [0, 2147483547].
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--firewall-policy` | FIREWALL_POLICY |  | Firewall policy ID with which to describe rule. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--firewall-policy-region` | FIREWALL_POLICY_REGION |  | _[At most one of these can be specified:]_ Region of the firewall policy to operate on. Overrides the default compute/region property value for this command invocation. |
| `--global-firewall-policy` |  |  | _[At most one of these can be specified:]_ If set, the firewall policy is global. |


**Examples:**
```bash
To describe a rule with priority 10 in a global network firewall policy
with name my-policy, run:

    $ gcloud compute network-firewall-policies rules describe 10 \
        --firewall-policy=my-policy --global-firewall-policy

To describe a rule with priority 10 in a regional network firewall policy
with name my-policy, in region region-a, run:

    $ gcloud compute network-firewall-policies rules describe 10 \
        --firewall-policy=my-policy --firewall-policy-region=region-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/network-firewall-policies/rules/describe)

---
### `gcloud compute network-firewall-policies rules update`

Updates a Compute Engine network firewall policy rule

gcloud compute network-firewall-policies rules update is used to update
network firewall policy rules.

**Synopsis:**
```
gcloud compute network-firewall-policies rules update PRIORITY
    --firewall-policy=FIREWALL_POLICY [--action=ACTION]
    [--description=DESCRIPTION]
    [--dest-address-groups=[DEST_ADDRESS_GROUPS,...]]
    [--dest-fqdns=[DEST_FQDNS,...]] [--dest-ip-ranges=[DEST_IP_RANGE,...]]
    [--dest-region-codes=[DEST_REGION_CODES,...]]
    [--dest-threat-intelligence=[DEST_THREAT_INTELLIGENCE_LISTS,...]]
    [--direction=DIRECTION] [--[no-]disabled] [--[no-]enable-logging]
    [--layer4-configs=[LAYER4_CONFIG,...]] [--new-priority=NEW_PRIORITY]
    [--security-profile-group=SECURITY_PROFILE_GROUP]
    [--src-address-groups=[SOURCE_ADDRESS_GROUPS,...]]
    [--src-fqdns=[SOURCE_FQDNS,...]] [--src-ip-ranges=[SRC_IP_RANGE,...]]
    [--src-region-codes=[SOURCE_REGION_CODES,...]]
    [--src-secure-tags=[SOURCE_SECURE_TAGS,...]]
    [--src-threat-intelligence=[SOURCE_THREAT_INTELLIGENCE_LISTS,...]]
    [--target-secure-tags=[TARGET_SECURE_TAGS,...]]
    [--target-service-accounts=[TARGET_SERVICE_ACCOUNTS,...]]
    [--[no-]tls-inspect]
    [--firewall-policy-region=FIREWALL_POLICY_REGION
      | --global-firewall-policy] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PRIORITY
   Priority of the rule to be updated. Valid in [0, 2147483547].
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--firewall-policy` | FIREWALL_POLICY |  | Firewall policy ID with which to update rule. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--action` | one of: allow, deny, goto_next, apply_security_profile_group |  | Action to take if the request matches the match condition. ACTION must be one of: allow, deny, goto_next, apply_security_profile_group. |
| `--description` | DESCRIPTION |  | An optional, textual description for the rule. |
| `--dest-address-groups` | [DEST_ADDRESS_GROUPS,...] |  | Destination address groups to match for this rule. Can only be specified if DIRECTION is engress. |
| `--dest-fqdns` | [DEST_FQDNS,...] |  | Destination FQDNs to match for this rule. Can only be specified if DIRECTION is egress. |
| `--dest-ip-ranges` | [DEST_IP_RANGE,...] |  | Destination IP ranges to match for this rule. |
| `--dest-region-codes` | [DEST_REGION_CODES,...] |  | Destination Region Code to match for this rule. Can only be specified if DIRECTION is egress. |
| `--dest-threat-intelligence` | [DEST_THREAT_INTELLIGENCE_LISTS,...] |  | Destination Threat Intelligence lists to match for this rule. Can only be specified if DIRECTION is egress. The available lists can be found here: https://cloud.google.com/vpc/docs/firewall-policies-rule-details#threat-intelligence-fw-policy. |
| `--direction` | one of: INGRESS, EGRESS |  | Direction of the traffic the rule is applied. The default is to apply on incoming traffic. DIRECTION must be one of: INGRESS, EGRESS. |
| `--[no-]disabled` |  |  | Use this flag to disable the rule. Disabled rules will not affect traffic. Use --disabled to enable and --no-disabled to disable. |
| `--[no-]enable-logging` |  |  | Use this flag to enable logging of connections that allowed or denied by this rule. Use --enable-logging to enable and --no-enable-logging to disable. |
| `--layer4-configs` | [LAYER4_CONFIG,...] |  | A list of destination protocols and ports to which the firewall rule will apply. |
| `--new-priority` | NEW_PRIORITY |  | New priority for the rule to update. Valid in [0, 65535]. |
| `--security-profile-group` | SECURITY_PROFILE_GROUP |  | A security profile group to be used with apply_security_profile_group action. |
| `--src-address-groups` | [SOURCE_ADDRESS_GROUPS,...] |  | Source address groups to match for this rule. Can only be specified if DIRECTION is ingress. |
| `--src-fqdns` | [SOURCE_FQDNS,...] |  | Source FQDNs to match for this rule. Can only be specified if DIRECTION is ingress. |
| `--src-ip-ranges` | [SRC_IP_RANGE,...] |  | A list of IP address blocks that are allowed to make inbound connections that match the firewall rule to the instances on the network. The IP address blocks must be specified in CIDR format: http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing.Either --src-ip-ranges or --src-secure-tags must be specified for INGRESS traffic. If both --src-ip-ranges and --src-secure-tags are specified, the rule matches if either the range of the source matches --src-ip-ranges or the secure tag of the source matches --src-secure-tags.Multiple IP address blocks can be specified if they are separated by commas. |
| `--src-region-codes` | [SOURCE_REGION_CODES,...] |  | Source Region Code to match for this rule. Can only be specified if DIRECTION is ingress. |
| `--src-secure-tags` | [SOURCE_SECURE_TAGS,...] |  | A list of instance secure tags indicating the set of instances on the network to which the rule applies if all other fields match. Either --src-ip-ranges or --src-secure-tags must be specified for ingress traffic. If both --src-ip-ranges and --src-secure-tags are specified, an inbound connection is allowed if either the range of the source matches --src-ip-ranges or the tag of the source matches --src-secure-tags. Secure Tags can be assigned to instances during instance creation. |
| `--src-threat-intelligence` | [SOURCE_THREAT_INTELLIGENCE_LISTS,...] |  | Source Threat Intelligence lists to match for this rule. Can only be specified if DIRECTION is ingress. The available lists can be found here: https://cloud.google.com/vpc/docs/firewall-policies-rule-details#threat-intelligence-fw-policy. |
| `--target-secure-tags` | [TARGET_SECURE_TAGS,...] |  | An optional, list of target secure tags with a name of the format tagValues/ or full namespaced name |
| `--target-service-accounts` | [TARGET_SERVICE_ACCOUNTS,...] |  | List of target service accounts for the rule. |
| `--[no-]tls-inspect` |  |  | Use this flag to indicate whether TLS traffic should be inspected using the TLS inspection policy when the security profile group is applied. Default: no TLS inspection. Use --tls-inspect to enable and --no-tls-inspect to disable. |


**Examples:**
```bash
To update a rule with priority 10 in a global network firewall policy with
name my-policy to change the action to allow and description to new example
rule, run:

    $ gcloud compute network-firewall-policies rules update 10 \
        --firewall-policy=my-policy --action=allow \
        --description="new example rule"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/network-firewall-policies/rules/update)

---
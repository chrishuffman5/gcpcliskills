# gcloud compute firewall-policies

manage Compute Engine organization firewall policies

### `gcloud compute firewall-policies clone-rules`

Replace the rules of a Compute Engine organization firewall policy with rules from another policy

gcloud compute firewall-policies clone-rules is used to replace the rules
of organization firewall policies. An organization firewall policy is a set
of rules that controls access to various resources.

**Synopsis:**
```
gcloud compute firewall-policies clone-rules FIREWALL_POLICY
    --source-firewall-policy=SOURCE_FIREWALL_POLICY
    [--organization=ORGANIZATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FIREWALL_POLICY
   Short name or ID of the firewall policy to clone the rules to.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source-firewall-policy` | SOURCE_FIREWALL_POLICY |  | The URL of the source firewall policy to copy the rules from. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION |  | Organization in which the organization firewall policy to copy the rules to. Must be set if firewall-policy is short name. |


**Examples:**
```bash
To clone the rules of an organization firewall policy with ID ``123456789",
from another organization firewall policy with ID ``987654321", run:

    $ gcloud compute firewall-policies clone-rules 123456789 \
        --source-firewall-policy=987654321
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/firewall-policies/clone-rules)

---
### `gcloud compute firewall-policies create`

Create a Compute Engine organization firewall policy

gcloud compute firewall-policies create is used to create organization
firewall policies. An organization firewall policy is a set of rules that
controls access to various resources.

**Synopsis:**
```
gcloud compute firewall-policies create --short-name=SHORT_NAME
    (--folder=FOLDER | --organization=ORGANIZATION)
    [--description=DESCRIPTION] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--short-name` | SHORT_NAME |  | A textual name of the firewall policy. The name must be 1-63 characters long, and comply with RFC 1035. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional, textual description for the organization security policy. |


**Examples:**
```bash
To create an organization firewall policy under folder with ID
``123456789", run:

    $ gcloud compute firewall-policies create --short-name=my-policy \
        --folder=123456789
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/firewall-policies/create)

---
### `gcloud compute firewall-policies delete`

Delete a Compute Engine organization firewall policy

gcloud compute firewall-policies delete is used to delete organization
firewall policies. An organization firewall policy is a set of rules that
controls access to various resources.

**Synopsis:**
```
gcloud compute firewall-policies delete FIREWALL_POLICY
    [--organization=ORGANIZATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FIREWALL_POLICY
   Short name or ID of the firewall policy to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION |  | Organization in which the organization firewall policy is to be deleted. Must be set if FIREWALL_POLICY is the short name. |


**Examples:**
```bash
To delete an organization firewall policy with ID ``123456789", run:

    $ gcloud compute firewall-policies delete 123456789
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/firewall-policies/delete)

---
### `gcloud compute firewall-policies describe`

Describe a Compute Engine organization firewall policy

gcloud compute firewall-policies describe is used to describe organization
firewall policies. An organization firewall policy is a set of rules that
controls access to various resources.

**Synopsis:**
```
gcloud compute firewall-policies describe FIREWALL_POLICY
    [--organization=ORGANIZATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FIREWALL_POLICY
   Short name or ID of the firewall policy to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION |  | Organization in which the organization firewall policy is to be described. Must be set if FIREWALL_POLICY is short name. |


**Examples:**
```bash
To describe an organization firewall policy with ID ``123456789", run:

    $ gcloud compute firewall-policies describe 123456789
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/firewall-policies/describe)

---
### `gcloud compute firewall-policies export-rules`

Export Compute Engine organization firewall policy rules

Exports Firewall Policy rules configuration to a file.

**Synopsis:**
```
gcloud compute firewall-policies export-rules FIREWALL_POLICY
    [--destination=DESTINATION] [--organization=ORGANIZATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FIREWALL_POLICY
   Short name or ID of the firewall policy to export rules from.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | Path to a YAML file where the configuration will be exported. Alternatively, you may omit this flag to write to standard output. For a schema describing the export/import format, see: $CLOUDSDKROOT\lib\googlecloudsdk\schemas\compute\v1\FirewallPolicy.yaml. |
| `--organization` | ORGANIZATION |  | Organization in which the organization firewall policy rules export from. Must be set if FIREWALL_POLICY is short name. |


**Examples:**
```bash
Firewall Policy rules can be exported by running:

    $ gcloud compute firewall-policies export-rules FIREWALL_POLICY \
        --destination=<path-to-file> --organization=<organization>
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/firewall-policies/export-rules)

---
### `gcloud compute firewall-policies import-rules`

Import Compute Engine organization firewall policy rules

Imports Firewall Policy rules configuration from a file.

**Synopsis:**
```
gcloud compute firewall-policies import-rules FIREWALL_POLICY
    [--organization=ORGANIZATION] [--source=SOURCE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FIREWALL_POLICY
   Short name or ID of the firewall policy to imports rules to.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION |  | Organization in which the organization firewall policy rules import to. Must be set if FIREWALL_POLICY is short name. |
| `--source` | SOURCE |  | Path to a YAML file containing configuration export data. Alternatively, you may omit this flag to read from standard input. For a schema describing the export/import format, see: $CLOUDSDKROOT\lib\googlecloudsdk\schemas\compute\v1\FirewallPolicy.yaml. Note: $CLOUDSDKROOT represents the Google Cloud CLI's installation directory. |


**Examples:**
```bash
Firewall Policy rules can be imported by running:

    $ gcloud compute firewall-policies import-rules FIREWALL_POLICY \
        --source=<path-to-file> --organization=<organization>
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/firewall-policies/import-rules)

---
### `gcloud compute firewall-policies list`

List Compute Engine organization firewall policies

gcloud compute firewall-policies list is used to list organization firewall
policies. An organization firewall policy is a set of rules that controls
access to various resources.

**Synopsis:**
```
gcloud compute firewall-policies list [NAME ...]
    (--folder=FOLDER | --organization=ORGANIZATION)
    [--regexp=REGEXP, -r REGEXP] [--filter=EXPRESSION] [--limit=LIMIT]
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

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER |  | _[Exactly one of these must be specified:]_ Folder in which firewall policies are listed |
| `--organization` | ORGANIZATION |  | _[Exactly one of these must be specified:]_ Organization in which firewall policies are listed |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--regexp` | REGEXP, -r REGEXP |  | (DEPRECATED) Regular expression to filter the names of the results on. Any names that do not match the entire regular expression will be filtered out. Flag --regexp is deprecated. Use --filter="name~'REGEXP'" instead. |


**Examples:**
```bash
To list organization firewall policies under folder with ID ``123456789",
run:

    $ gcloud compute firewall-policies list --folder=123456789
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/firewall-policies/list)

---
### `gcloud compute firewall-policies list-rules`

List the rules of a Compute Engine organization firewall policy

gcloud compute firewall-policies list-rules is used to list the rules of an
organization firewall policy.

**Synopsis:**
```
gcloud compute firewall-policies list-rules FIREWALL_POLICY [NAME ...]
    [--organization=ORGANIZATION] [--regexp=REGEXP, -r REGEXP]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FIREWALL_POLICY
   Short name or ID of the firewall policy to list rules for.

[NAME ...]
   (DEPRECATED) If provided, show details for the specified names and/or
   URIs of resources.

   Argument NAME is deprecated. Use --filter="name=( 'NAME' ... )"
   instead.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION |  | Organization which the organization firewall policy belongs to. Must be set if FIREWALL_POLICY is short name. |
| `--regexp` | REGEXP, -r REGEXP |  | (DEPRECATED) Regular expression to filter the names of the results on. Any names that do not match the entire regular expression will be filtered out. Flag --regexp is deprecated. Use --filter="name~'REGEXP'" instead. |


**Examples:**
```bash
To list the rules of an organization firewall policy with ID ``123456789",
run:

    $ gcloud compute firewall-policies list-rules 123456789

To list all the fields of the rules of an organization firewall policy with
ID ``123456789", run:

    $ gcloud compute firewall-policies list-rules 123456789 \
        --format="table(
      priority,
      action,
      direction,
      match.srcIpRanges.list():label=SRC_RANGES,
      match.destIpRanges.list():label=DEST_RANGES,
      match.layer4Configs.map().org_firewall_rule().list():label=PORT_RANGES,
      targetServiceAccounts.list():label=TARGET_SVC_ACCT,
      targetResources:label=TARGET_RESOURCES,
      ruleTupleCount,
      enableLogging,
      description)"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/firewall-policies/list-rules)

---
### `gcloud compute firewall-policies move`

Move a Compute Engine organization firewall policy

gcloud compute firewall-policies move is used to move is used to move
organization firewall policies to new parent nodes.

**Synopsis:**
```
gcloud compute firewall-policies move FIREWALL_POLICY [--folder=FOLDER]
    [--organization=ORGANIZATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FIREWALL_POLICY
   Short name or ID of the firewall policy to move.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER |  | Folder to which the organization firewall policy is to be moved. |
| `--organization` | ORGANIZATION |  | Organization in which the organization firewall policy is to be moved. Must be set if FIREWALL_POLICY is short name. |


**Examples:**
```bash
To move an organization firewall policy under folder with ID ``123456789"
to folder ``987654321", run:

    $ gcloud compute firewall-policies move 123456789 --folder=987654321
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/firewall-policies/move)

---
### `gcloud compute firewall-policies update`

Update a Compute Engine organization firewall policy

gcloud compute firewall-policies update is used to update organization
firewall policies. An organization firewall policy is a set of rules that
controls access to various resources.

**Synopsis:**
```
gcloud compute firewall-policies update FIREWALL_POLICY
    [--description=DESCRIPTION] [--organization=ORGANIZATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FIREWALL_POLICY
   Short name or ID of the firewall policy to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional, textual description for the organization security policy. |
| `--organization` | ORGANIZATION |  | Organization in which the organization firewall policy is to be updated. Must be set if FIREWALL_POLICY is short name. |


**Examples:**
```bash
To update an organization firewall policy with ID ``123456789" to change
the description to ``New description", run:

    $ gcloud compute firewall-policies update 123456789 \
        --description='New description'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/firewall-policies/update)

---

## `gcloud compute firewall-policies associations` — read and manipulate Compute Engine organization firewall policy associations
### `gcloud compute firewall-policies associations create`

Create a new association between a firewall policy and an organization or folder resource

gcloud compute firewall-policies associations create is used to create
organization firewall policy associations. An organization firewall policy
is a set of rules that controls access to various resources.

**Synopsis:**
```
gcloud compute firewall-policies associations create
    --firewall-policy=FIREWALL_POLICY [--folder=FOLDER] [--name=NAME]
    [--organization=ORGANIZATION] [--replace-association-on-target]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--firewall-policy` | FIREWALL_POLICY |  | Security policy ID of the association. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER |  | ID of the folder with which the association is created. |
| `--name` | NAME |  | Name to identify this association. If unspecified, the name will be set to "organization-{ORGANIZATION_ID}" or "folder-{FOLDER_ID}". |
| `--organization` | ORGANIZATION |  | ID of the organization in which the firewall policy is to be associated. Must be set if FIREWALL_POLICY is short name. |
| `--replace-association-on-target` |  |  | By default, if you attempt to insert an association to an organization or folder resource that is already associated with a firewall policy the method will fail. If this is set, the existing association will be deleted at the same time that the new association is created. |


**Examples:**
```bash
To associate an organization firewall policy under folder with ID
``123456789" to folder ``987654321", run:

    $ gcloud compute firewall-policies associations create \
        --firewall-policy=123456789 --folder=987654321
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/firewall-policies/associations/create)

---
### `gcloud compute firewall-policies associations delete`

Delete a Compute Engine organization firewall policy association

gcloud compute firewall-policies associations delete is used to delete
organization firewall policy association.

**Synopsis:**
```
gcloud compute firewall-policies associations delete NAME
    --firewall-policy=FIREWALL_POLICY [--organization=ORGANIZATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the association to delete.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--firewall-policy` | FIREWALL_POLICY |  | Short name or ID of the firewall policy ID of the association. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION |  | ID of the organization in which the firewall policy is to be detached. Must be set if FIREWALL_POLICY is short name. |


**Examples:**
```bash
To delete an association with name ``example-association" of an
organization firewall policy with ID ``123456789", run:

    $ gcloud compute firewall-policies associations delete \
        example-association --firewall-policy=123456789
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/firewall-policies/associations/delete)

---
### `gcloud compute firewall-policies associations list`

List the associations of an organization or folder resource

gcloud compute firewall-policies associations list is used to list the
associations of an organization or folder resource.

**Synopsis:**
```
gcloud compute firewall-policies associations list
    (--folder=FOLDER | --organization=ORGANIZATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER |  | _[Exactly one of these must be specified:]_ ID of the folder with which the association is listed. |
| `--organization` | ORGANIZATION |  | _[Exactly one of these must be specified:]_ ID of the organization with which the association is listed. |


**Examples:**
```bash
To list the associations of the folder with ID ``987654321", run:

    $ gcloud compute firewall-policies associations list \
        --folder=987654321
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/firewall-policies/associations/list)

---

## `gcloud compute firewall-policies rules` — read and manipulate Compute Engine organization firewall policy rules
### `gcloud compute firewall-policies rules create`

Creates a Compute Engine firewall policy rule

gcloud compute firewall-policies rules create is used to create
organization firewall policy rules.

**Synopsis:**
```
gcloud compute firewall-policies rules create PRIORITY --action=ACTION
    --firewall-policy=FIREWALL_POLICY --layer4-configs=[LAYER4_CONFIG,...]
    [--description=DESCRIPTION]
    [--dest-address-groups=[DEST_ADDRESS_GROUPS,...]]
    [--dest-fqdns=[DEST_FQDNS,...]] [--dest-ip-ranges=[DEST_IP_RANGE,...]]
    [--dest-region-codes=[DEST_REGION_CODES,...]]
    [--dest-threat-intelligence=[DEST_THREAT_INTELLIGENCE_LISTS,...]]
    [--direction=DIRECTION] [--[no-]disabled] [--[no-]enable-logging]
    [--organization=ORGANIZATION]
    [--security-profile-group=SECURITY_PROFILE_GROUP]
    [--src-address-groups=[SOURCE_ADDRESS_GROUPS,...]]
    [--src-fqdns=[SOURCE_FQDNS,...]] [--src-ip-ranges=[SRC_IP_RANGE,...]]
    [--src-region-codes=[SOURCE_REGION_CODES,...]]
    [--src-secure-tags=[SOURCE_SECURE_TAGS,...]]
    [--src-threat-intelligence=[SOURCE_THREAT_INTELLIGENCE_LISTS,...]]
    [--target-resources=[TARGET_RESOURCES,...]]
    [--target-secure-tags=[TARGET_SECURE_TAGS,...]]
    [--target-service-accounts=[TARGET_SERVICE_ACCOUNTS,...]]
    [--[no-]tls-inspect] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PRIORITY
   Priority of the firewall policy rule to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--action` | one of: allow, deny, goto_next, apply_security_profile_group |  | Action to take if the request matches the match condition. ACTION must be one of: allow, deny, goto_next, apply_security_profile_group. |
| `--firewall-policy` | FIREWALL_POLICY |  | Short name of the firewall policy into which the rule should be inserted. |
| `--layer4-configs` | [LAYER4_CONFIG,...] |  | A list of destination protocols and ports to which the firewall rule will apply. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional, textual description for the rule. |
| `--dest-address-groups` | [DEST_ADDRESS_GROUPS,...] |  | Destination address groups to match for this rule. Can only be specified if DIRECTION is egress. |
| `--dest-fqdns` | [DEST_FQDNS,...] |  | Destination FQDNs to match for this rule. Can only be specified if DIRECTION is egress. |
| `--dest-ip-ranges` | [DEST_IP_RANGE,...] |  | Destination IP ranges to match for this rule. |
| `--dest-region-codes` | [DEST_REGION_CODES,...] |  | Destination Region Code to match for this rule. Can only be specified if DIRECTION is egress. |
| `--dest-threat-intelligence` | [DEST_THREAT_INTELLIGENCE_LISTS,...] |  | Destination Threat Intelligence lists to match for this rule. Can only be specified if DIRECTION is egress. The available lists can be found here: https://cloud.google.com/vpc/docs/firewall-policies-rule-details#threat-intelligence-fw-policy. |
| `--direction` | one of: INGRESS, EGRESS |  | Direction of the traffic the rule is applied. The default is to apply on incoming traffic. DIRECTION must be one of: INGRESS, EGRESS. |
| `--[no-]disabled` |  |  | Use this flag to disable the rule. Disabled rules will not affect traffic. Use --disabled to enable and --no-disabled to disable. |
| `--[no-]enable-logging` |  |  | Use this flag to enable logging of connections that allowed or denied by this rule. Use --enable-logging to enable and --no-enable-logging to disable. |
| `--organization` | ORGANIZATION |  | Organization which the organization firewall policy belongs to. Must be set if FIREWALL_POLICY is short name. |
| `--security-profile-group` | SECURITY_PROFILE_GROUP |  | An org-based security profile group to be used with apply_security_profile_group action. Allowed formats are: a) http(s)://<namespace>/<api>/organizations/<org_id>/locations/global/securityProfileGroups/<profile> b) (//)<namespace>/organizations/<org_id>/locations/global/securityProfileGroups/<profile> c) <profile>. In case "c" gcloud CLI will create a reference matching format "a", but to make it work CLOUDSDK_API_ENDPOINT_OVERRIDES_NETWORKSECURITY property must be set. In order to set this property, please run the command gcloud config set api_endpoint_overrides/networksecurity https://<namespace>/. |
| `--src-address-groups` | [SOURCE_ADDRESS_GROUPS,...] |  | Source address groups to match for this rule. Can only be specified if DIRECTION is ingress. |
| `--src-fqdns` | [SOURCE_FQDNS,...] |  | Source FQDNs to match for this rule. Can only be specified if DIRECTION is ingress. |
| `--src-ip-ranges` | [SRC_IP_RANGE,...] |  | Source IP ranges to match for this rule. |
| `--src-region-codes` | [SOURCE_REGION_CODES,...] |  | Source Region Code to match for this rule. Can only be specified if DIRECTION is ingress. |
| `--src-secure-tags` | [SOURCE_SECURE_TAGS,...] |  | A list of instance secure tags indicating the set of instances on the network to which the rule applies if all other fields match. Either --src-ip-ranges or --src-secure-tags must be specified for ingress traffic. If both --src-ip-ranges and --src-secure-tags are specified, an inbound connection is allowed if either the range of the source matches --src-ip-ranges or the tag of the source matches --src-secure-tags. Secure Tags can be assigned to instances during instance creation. |
| `--src-threat-intelligence` | [SOURCE_THREAT_INTELLIGENCE_LISTS,...] |  | Source Threat Intelligence lists to match for this rule. Can only be specified if DIRECTION is ingress. The available lists can be found here: https://cloud.google.com/vpc/docs/firewall-policies-rule-details#threat-intelligence-fw-policy. |
| `--target-resources` | [TARGET_RESOURCES,...] |  | List of URLs of target resources to which the rule is applied. |
| `--target-secure-tags` | [TARGET_SECURE_TAGS,...] |  | An optional, list of target secure tags with a name of the format tagValues/ or full namespaced name |
| `--target-service-accounts` | [TARGET_SERVICE_ACCOUNTS,...] |  | List of target service accounts for the rule. |
| `--[no-]tls-inspect` |  |  | Use this flag to indicate whether TLS traffic should be inspected using the TLS inspection policy when the security profile group is applied. Default: no TLS inspection. Use --tls-inspect to enable and --no-tls-inspect to disable. |


**Examples:**
```bash
To create a rule with priority ``10" in an organization firewall policy
with ID ``123456789", run:

    $ gcloud compute firewall-policies rules create 10 \
        --firewall-policy=123456789 --action=allow \
        --description=example-rule
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/firewall-policies/rules/create)

---
### `gcloud compute firewall-policies rules delete`

Deletes a Compute Engine organization firewall policy rule

gcloud compute firewall-policies rules delete is used to delete
organization firewall policy rules.

**Synopsis:**
```
gcloud compute firewall-policies rules delete PRIORITY
    --firewall-policy=FIREWALL_POLICY [--organization=ORGANIZATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PRIORITY
   Priority of the firewall policy rule to delete.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--firewall-policy` | FIREWALL_POLICY |  | Short name of the firewall policy into which the rule should be deleted. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION |  | Organization which the organization firewall policy belongs to. Must be set if FIREWALL_POLICY is short name. |


**Examples:**
```bash
To delete a rule with priority ``10" in an organization firewall policy
with ID ``123456789", run:

    $ gcloud compute firewall-policies rules delete 10 \
        --firewall-policy=123456789
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/firewall-policies/rules/delete)

---
### `gcloud compute firewall-policies rules describe`

Describes a Compute Engine organization firewall policy rule

gcloud compute firewall-policies rules describe is used to describe
organization firewall policy rules.

**Synopsis:**
```
gcloud compute firewall-policies rules describe PRIORITY
    --firewall-policy=FIREWALL_POLICY [--organization=ORGANIZATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PRIORITY
   Priority of the firewall policy rule to describe.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--firewall-policy` | FIREWALL_POLICY |  | Short name of the firewall policy into which the rule should be described. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION |  | Organization which the organization firewall policy belongs to. Must be set if FIREWALL_POLICY is short name. |


**Examples:**
```bash
To describe a rule with priority ``10" in an organization firewall policy
with ID ``123456789", run:

    $ gcloud compute firewall-policies rules describe 10 \
        --firewall-policy=123456789
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/firewall-policies/rules/describe)

---
### `gcloud compute firewall-policies rules update`

Updates a Compute Engine firewall policy rule

gcloud compute firewall-policies rules update is used to update
organization firewall policy rules.

**Synopsis:**
```
gcloud compute firewall-policies rules update PRIORITY
    --firewall-policy=FIREWALL_POLICY [--action=ACTION]
    [--description=DESCRIPTION]
    [--dest-address-groups=[DEST_ADDRESS_GROUPS,...]]
    [--dest-fqdns=[DEST_FQDNS,...]] [--dest-ip-ranges=[DEST_IP_RANGE,...]]
    [--dest-region-codes=[DEST_REGION_CODES,...]]
    [--dest-threat-intelligence=[DEST_THREAT_INTELLIGENCE_LISTS,...]]
    [--direction=DIRECTION] [--[no-]disabled] [--[no-]enable-logging]
    [--layer4-configs=[LAYER4_CONFIG,...]] [--new-priority=NEW_PRIORITY]
    [--organization=ORGANIZATION]
    [--security-profile-group=SECURITY_PROFILE_GROUP]
    [--src-address-groups=[SOURCE_ADDRESS_GROUPS,...]]
    [--src-fqdns=[SOURCE_FQDNS,...]] [--src-ip-ranges=[SRC_IP_RANGE,...]]
    [--src-region-codes=[SOURCE_REGION_CODES,...]]
    [--src-secure-tags=[SOURCE_SECURE_TAGS,...]]
    [--src-threat-intelligence=[SOURCE_THREAT_INTELLIGENCE_LISTS,...]]
    [--target-resources=[TARGET_RESOURCES,...]]
    [--target-secure-tags=[TARGET_SECURE_TAGS,...]]
    [--target-service-accounts=[TARGET_SERVICE_ACCOUNTS,...]]
    [--[no-]tls-inspect] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PRIORITY
   Priority of the firewall policy rule to update.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--firewall-policy` | FIREWALL_POLICY |  | Short name of the firewall policy into which the rule should be updated. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--action` | one of: allow, deny, goto_next, apply_security_profile_group |  | Action to take if the request matches the match condition. ACTION must be one of: allow, deny, goto_next, apply_security_profile_group. |
| `--description` | DESCRIPTION |  | An optional, textual description for the rule. |
| `--dest-address-groups` | [DEST_ADDRESS_GROUPS,...] |  | Destination address groups to match for this rule. Can only be specified if DIRECTION is egress. |
| `--dest-fqdns` | [DEST_FQDNS,...] |  | Destination FQDNs to match for this rule. Can only be specified if DIRECTION is egress. |
| `--dest-ip-ranges` | [DEST_IP_RANGE,...] |  | Destination IP ranges to match for this rule. |
| `--dest-region-codes` | [DEST_REGION_CODES,...] |  | Destination Region Code to match for this rule. Can only be specified if DIRECTION is egress. |
| `--dest-threat-intelligence` | [DEST_THREAT_INTELLIGENCE_LISTS,...] |  | Destination Threat Intelligence lists to match for this rule. Can only be specified if DIRECTION is egress. The available lists can be found here: https://cloud.google.com/vpc/docs/firewall-policies-rule-details#threat-intelligence-fw-policy. |
| `--direction` | one of: INGRESS, EGRESS |  | Direction of the traffic the rule is applied. The default is to apply on incoming traffic. DIRECTION must be one of: INGRESS, EGRESS. |
| `--[no-]disabled` |  |  | Use this flag to disable the rule. Disabled rules will not affect traffic. Use --disabled to enable and --no-disabled to disable. |
| `--[no-]enable-logging` |  |  | Use this flag to enable logging of connections that allowed or denied by this rule. Use --enable-logging to enable and --no-enable-logging to disable. |
| `--layer4-configs` | [LAYER4_CONFIG,...] |  | A list of destination protocols and ports to which the firewall rule will apply. |
| `--new-priority` | NEW_PRIORITY |  | New priority for the rule to update. Valid in [0, 65535]. |
| `--organization` | ORGANIZATION |  | Organization which the organization firewall policy belongs to. Must be set if FIREWALL_POLICY is short name. |
| `--security-profile-group` | SECURITY_PROFILE_GROUP |  | An org-based security profile group to be used with apply_security_profile_group action. Allowed formats are: a) http(s)://<namespace>/<api>/organizations/<org_id>/locations/global/securityProfileGroups/<profile> b) (//)<namespace>/organizations/<org_id>/locations/global/securityProfileGroups/<profile> c) <profile>. In case "c" gcloud CLI will create a reference matching format "a", but to make it work CLOUDSDK_API_ENDPOINT_OVERRIDES_NETWORKSECURITY property must be set. In order to set this property, please run the command gcloud config set api_endpoint_overrides/networksecurity https://<namespace>/. |
| `--src-address-groups` | [SOURCE_ADDRESS_GROUPS,...] |  | Source address groups to match for this rule. Can only be specified if DIRECTION is ingress. |
| `--src-fqdns` | [SOURCE_FQDNS,...] |  | Source FQDNs to match for this rule. Can only be specified if DIRECTION is ingress. |
| `--src-ip-ranges` | [SRC_IP_RANGE,...] |  | Source IP ranges to match for this rule. |
| `--src-region-codes` | [SOURCE_REGION_CODES,...] |  | Source Region Code to match for this rule. Can only be specified if DIRECTION is ingress. |
| `--src-secure-tags` | [SOURCE_SECURE_TAGS,...] |  | A list of instance secure tags indicating the set of instances on the network to which the rule applies if all other fields match. Either --src-ip-ranges or --src-secure-tags must be specified for ingress traffic. If both --src-ip-ranges and --src-secure-tags are specified, an inbound connection is allowed if either the range of the source matches --src-ip-ranges or the tag of the source matches --src-secure-tags. Secure Tags can be assigned to instances during instance creation. |
| `--src-threat-intelligence` | [SOURCE_THREAT_INTELLIGENCE_LISTS,...] |  | Source Threat Intelligence lists to match for this rule. Can only be specified if DIRECTION is ingress. The available lists can be found here: https://cloud.google.com/vpc/docs/firewall-policies-rule-details#threat-intelligence-fw-policy. |
| `--target-resources` | [TARGET_RESOURCES,...] |  | List of URLs of target resources to which the rule is applied. |
| `--target-secure-tags` | [TARGET_SECURE_TAGS,...] |  | An optional, list of target secure tags with a name of the format tagValues/ or full namespaced name |
| `--target-service-accounts` | [TARGET_SERVICE_ACCOUNTS,...] |  | List of target service accounts for the rule. |
| `--[no-]tls-inspect` |  |  | Use this flag to indicate whether TLS traffic should be inspected using the TLS inspection policy when the security profile group is applied. Default: no TLS inspection. Use --tls-inspect to enable and --no-tls-inspect to disable. |


**Examples:**
```bash
To update a rule with priority ``10" in an organization firewall policy
with ID ``123456789" to change the action to ``allow" and description to
``new-example-rule", run:

    $ gcloud compute firewall-policies rules update 10 \
        --firewall-policy=123456789 --action=allow \
        --description=new-example-rule
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/firewall-policies/rules/update)

---
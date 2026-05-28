# gcloud compute org-security-policies

manage Compute Engine organization security policies

### `gcloud compute org-security-policies copy-rules`

Replace the rules of a Compute Engine organization security policy with rules from another policy

gcloud compute org-security-policies copy-rules is used to replace the
rules of organization security policies. An organization security policy is
a set of rules that controls access to various resources.

**Synopsis:**
```
gcloud compute org-security-policies copy-rules SECURITY_POLICY
    --source-security-policy=SOURCE_SECURITY_POLICY
    [--organization=ORGANIZATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SECURITY_POLICY
   Short name or ID of the security policy to copy the rules to.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source-security-policy` | SOURCE_SECURITY_POLICY |  | The URL of the source security policy to copy the rules from. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION |  | Organization in which the organization security policy to copy the rules to. Must be set if security-policy is the short name. |


**Examples:**
```bash
To copy the rules of an organization security policy with ID 123456789,
from another organization security policy with ID 987654321, run:

    $ gcloud compute org-security-policies copy-rules 123456789 \
        --source-security-policy=987654321
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/org-security-policies/copy-rules)

---
### `gcloud compute org-security-policies create`

Create a Compute Engine organization security policy

gcloud compute org-security-policies create is used to create organization
security policies. An organization security policy is a set of rules that
controls access to various resources.

**Synopsis:**
```
gcloud compute org-security-policies create
    (--folder=FOLDER | --organization=ORGANIZATION)
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [--file-format=FILE_FORMAT] [--short-name=SHORT_NAME]
    [--file-name=FILE_NAME | --type=SECURITY_POLICY_TYPE]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER |  | _[Exactly one of these must be specified:]_ Folder in which the organization security policy is to be created. |
| `--organization` | ORGANIZATION |  | _[Exactly one of these must be specified:]_ Organization in which the organization security policy is to be created. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional, textual description for the organization security policy. |
| `--display-name` | DISPLAY_NAME |  | A textual name of the security policy. |
| `--file-format` | one of: json, yaml |  | The format of the file to create the organization security policy config from. Specify either yaml or json. Defaults to yaml if not specified. Will be ignored if --file-name is not specified. FILE_FORMAT must be one of: json, yaml. |
| `--short-name` | SHORT_NAME |  | A textual name of the security policy. |


**Examples:**
```bash
To create an organization security policy under folder with ID 123456789,
run:

    $ gcloud compute org-security-policies create \
        --short-name=my-policy --folder=123456789

To create an organization security under organization with ID 12345 from an
input file, run:

    $ gcloud compute org-security-policies create \
        --file-name=my-file-name --organization=12345
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/org-security-policies/create)

---
### `gcloud compute org-security-policies delete`

Delete a Compute Engine organization security policy

gcloud compute org-security-policies delete is used to delete organization
security policies. An organization security policy is a set of rules that
controls access to various resources.

**Synopsis:**
```
gcloud compute org-security-policies delete SECURITY_POLICY
    [--organization=ORGANIZATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SECURITY_POLICY
   Short name or ID of the security policy to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION |  | Organization in which the organization security policy is to be deleted. Must be set if SECURITY_POLICY is short name. |


**Examples:**
```bash
To delete an organization security policy with ID 123456789, run:

    $ gcloud compute org-security-policies delete 123456789
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/org-security-policies/delete)

---
### `gcloud compute org-security-policies describe`

Describe a Compute Engine organization security policy

gcloud compute org-security-policies describe is used to describe
organization security policies. An organization security policy is a set of
rules that controls access to various resources.

**Synopsis:**
```
gcloud compute org-security-policies describe SECURITY_POLICY
    [--organization=ORGANIZATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SECURITY_POLICY
   Short name or ID of the security policy to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION |  | Organization in which the organization security policy is to be described. Must be set if SECURITY_POLICY is short name. |


**Examples:**
```bash
To describe an organization security policy with ID 123456789, run:

    $ gcloud compute org-security-policies describe 123456789
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/org-security-policies/describe)

---
### `gcloud compute org-security-policies list`

List Compute Engine organization security policies

gcloud compute org-security-policies list is used to list organization
security policies. An organization security policy is a set of rules that
controls access to various resources.

**Synopsis:**
```
gcloud compute org-security-policies list [NAME ...]
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
| `--folder` | FOLDER |  | _[Exactly one of these must be specified:]_ Folder in which security policies are listed |
| `--organization` | ORGANIZATION |  | _[Exactly one of these must be specified:]_ Organization in which security policies are listed |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--regexp` | REGEXP, -r REGEXP |  | (DEPRECATED) Regular expression to filter the names of the results on. Any names that do not match the entire regular expression will be filtered out. Flag --regexp is deprecated. Use --filter="name~'REGEXP'" instead. |


**Examples:**
```bash
To list organization security policies under folder with ID 123456789, run:

    $ gcloud compute org-security-policies list --folder=123456789
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/org-security-policies/list)

---
### `gcloud compute org-security-policies list-rules`

List the rules of a Compute Engine organization security policy

gcloud compute org-security-policies list-rules is used to list the rules
of an organization security policy.

**Synopsis:**
```
gcloud compute org-security-policies list-rules SECURITY_POLICY [NAME ...]
    [--organization=ORGANIZATION] [--regexp=REGEXP, -r REGEXP]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SECURITY_POLICY
   Short name or ID of the security policy to list rules for.

[NAME ...]
   (DEPRECATED) If provided, show details for the specified names and/or
   URIs of resources.

   Argument NAME is deprecated. Use --filter="name=( 'NAME' ... )"
   instead.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION |  | Organization which the organization security policy belongs to. Must be set if SECURITY_POLICY is display name. |
| `--regexp` | REGEXP, -r REGEXP |  | (DEPRECATED) Regular expression to filter the names of the results on. Any names that do not match the entire regular expression will be filtered out. Flag --regexp is deprecated. Use --filter="name~'REGEXP'" instead. |


**Examples:**
```bash
To list the rules of an organization security policy with ID 123456789,
run:

    $ gcloud compute org-security-policies list-rules 123456789

To list all the fields of the rules of an organization security policy with
ID 123456789, run:

    $ gcloud compute org-security-policies list-rules list-rules \
        123456789 --format="table(
      priority,
      action,
      direction,
      match.config.srcIpRanges.list():label=SRC_RANGES,
      match.config.destIpRanges.list():label=DEST_RANGES,
      match.config.layer4Configs.map().org_firewall_rule().list():label=PORT_RANGES,
      targetServiceAccounts.list():label=TARGET_SVC_ACCT,
      targetResources:label=TARGET_RESOURCES,
      ruleTupleCount,
      enableLogging,
      description)"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/org-security-policies/list-rules)

---
### `gcloud compute org-security-policies move`

Move a Compute Engine organization security policy

gcloud compute org-security-policies move is used to move is used to move
organization security policies to new parent nodes.

**Synopsis:**
```
gcloud compute org-security-policies move SECURITY_POLICY [--folder=FOLDER]
    [--organization=ORGANIZATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SECURITY_POLICY
   Short name or ID of the security policy to move.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER |  | Folder to which the organization security policy is to be moved. |
| `--organization` | ORGANIZATION |  | Organization in which the organization security policy is to be moved. Must be set if SECURITY_POLICY is the short name. |


**Examples:**
```bash
To move an organization security policy under folder with ID 123456789 to
folder 987654321, run:

    $ gcloud compute org-security-policies move 123456789 \
        --folder=987654321
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/org-security-policies/move)

---
### `gcloud compute org-security-policies update`

Update a Compute Engine organization security policy

gcloud compute org-security-policies update is used to update organization
security policies. An organization security policy is a set of rules that
controls access to various resources.

**Synopsis:**
```
gcloud compute org-security-policies update SECURITY_POLICY
    [--description=DESCRIPTION]
    [--json-custom-content-types=[CONTENT_TYPE,...]]
    [--json-parsing=JSON_PARSING] [--log-level=LOG_LEVEL]
    [--organization=ORGANIZATION]
    [--user-ip-request-headers=[USER_IP_REQUEST_HEADER,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SECURITY_POLICY
   Short name or ID of the security policy to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional, textual description for the organization security policy. |
| `--json-custom-content-types` | [CONTENT_TYPE,...] |  | A comma-separated list of custom Content-Type header values to apply JSON parsing for preconfigured WAF rules. Only applicable when JSON parsing is enabled, like --json-parsing=STANDARD. When configuring a Content-Type header value, only the type/subtype needs to be specified, and the parameters should be excluded. |
| `--json-parsing` | one of: DISABLED, STANDARD, STANDARD_WITH_GRAPHQL |  | The JSON parsing behavior for this rule. Must be one of the following values: [DISABLED, STANDARD, STANDARD_WITH_GRAPHQL]. JSON_PARSING must be one of: DISABLED, STANDARD, STANDARD_WITH_GRAPHQL. |
| `--log-level` | one of: NORMAL, VERBOSE |  | The level of detail to display for WAF logging. LOG_LEVEL must be one of: NORMAL, VERBOSE. |
| `--organization` | ORGANIZATION |  | Organization in which the organization security policy is to be updated. Must be set if SECURITY_POLICY is the short name. |
| `--user-ip-request-headers` | [USER_IP_REQUEST_HEADER,...] |  | A comma-separated list of request header names to use for resolving the caller's user IP address. |


**Examples:**
```bash
To update an organization security policy with ID 123456789 to change the
description to New description, run:

    $ gcloud compute org-security-policies update 123456789 \
        --description='New description'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/org-security-policies/update)

---

## `gcloud compute org-security-policies associations` — read and manipulate Compute Engine organization security policy associations
### `gcloud compute org-security-policies associations create`

Create a new association between a security policy and an organization or folder resource

gcloud compute org-security-policies associations create is used to create
organization security policy associations. An organization security policy
is a set of rules that controls access to various resources.

This command has billing implications. Projects in the hierarchy with
effective hierarchical security policies will be automatically enrolled
into Cloud Armor Enterprise if not already enrolled.

**Synopsis:**
```
gcloud compute org-security-policies associations create
    --security-policy=SECURITY_POLICY
    [--excluded-folders=[EXCLUDED_FOLDERS,...]]
    [--excluded-projects=[EXCLUDED_PROJECTS,...]] [--name=NAME]
    [--organization=ORGANIZATION] [--replace-association-on-target]
    [--folder=FOLDER | --project-number=PROJECT_NUMBER]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--security-policy` | SECURITY_POLICY |  | Security policy ID of the association. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--excluded-folders` | [EXCLUDED_FOLDERS,...] |  | List of folders to exclude from the application of this security policy. Folders should be specified in the form "folders/123". |
| `--excluded-projects` | [EXCLUDED_PROJECTS,...] |  | List of projects to exclude from the application of this security policy. Projects should be specified in the form "projects/123". |
| `--name` | NAME |  | Name to identify this association. If unspecified, the name will be set to "organization-{ORGANIZATION_ID}" or "folder-{FOLDER_ID}". |
| `--organization` | ORGANIZATION |  | ID of the organization to associate the security policy with. Must be set if SECURITY_POLICY is short name. |
| `--replace-association-on-target` |  |  | By default, if you attempt to insert an association to an organization or folder resource that is already associated with a security policy the method will fail. If this is set, the existing association will be deleted at the same time that the new association is created. |


**Examples:**
```bash
To associate an organization security policy under folder with ID 123456789
to folder 987654321, run:

    $ gcloud compute org-security-policies associations create \
        --security-policy=123456789 --folder=987654321
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/org-security-policies/associations/create)

---
### `gcloud compute org-security-policies associations delete`

Delete a Compute Engine organization security policy association

gcloud compute org-security-policies associations delete is used to delete
organization security policy association.

**Synopsis:**
```
gcloud compute org-security-policies associations delete NAME
    --security-policy=SECURITY_POLICY [--organization=ORGANIZATION]
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
| `--security-policy` | SECURITY_POLICY |  | short name or ID of the security policy ID of the association. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION |  | ID of the organization in which the security policy is to be detached. Must be set if SECURITY_POLICY is short name. |


**Examples:**
```bash
To delete an association with name example-association of an organization
security policy with ID 123456789, run:

    $ gcloud compute org-security-policies associations delete \
        example-association --security-policy=123456789
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/org-security-policies/associations/delete)

---
### `gcloud compute org-security-policies associations list`

List the associations of an organization or folder resource

gcloud compute org-security-policies associations list is used to list the
associations of an organization or folder resource.

**Synopsis:**
```
gcloud compute org-security-policies associations list
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
To list the associations of the folder with ID 987654321, run:

    $ gcloud compute org-security-policies associations list \
        --folder=987654321
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/org-security-policies/associations/list)

---

## `gcloud compute org-security-policies rules` — read and manipulate Compute Engine organization security policy rules
### `gcloud compute org-security-policies rules add-preconfig-waf-exclusion`

Add an exclusion configuration for preconfigured WAF evaluation into a security policy rule

gcloud compute org-security-policies rules add-preconfig-waf-exclusion is
used to add an exclusion configuration for preconfigured WAF evaluation
into a security policy rule.

Note that request field exclusions are associated with a target, which can
be a single rule set, or a rule set plus a list of rule IDs under the rule
set.

**Synopsis:**
```
gcloud compute org-security-policies rules add-preconfig-waf-exclusion
    PRIORITY --security-policy=SECURITY_POLICY
    --target-rule-set=TARGET_RULE_SET [--organization=ORGANIZATION]
    [--request-cookie-to-exclude=[op=OP],[val=VAL]]
    [--request-header-to-exclude=[op=OP],[val=VAL]]
    [--request-query-param-to-exclude=[op=OP],[val=VAL]]
    [--request-uri-to-exclude=[op=OP],[val=VAL]]
    [--target-rule-ids=[RULE_ID,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PRIORITY
   Priority of the security policy rule to add preconfig WAF exclusion.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--security-policy` | SECURITY_POLICY |  | short name of the security policy into which the rule should be updated. |
| `--target-rule-set` | TARGET_RULE_SET |  | Target WAF rule set where the request field exclusions being added would apply. This, together with the target rule IDs (if given), determines the target for associating request field exclusions. See --target-rule-ids. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION |  | Organization which the organization security policy belongs to. Must be set if SECURITY_POLICY is short name. |
| `--request-cookie-to-exclude` | [op=OP],[val=VAL] |  | Adds a request cookie to the request field exclusions associated with the rule set and rule IDs (if given). This specifies a request cookie whose value will be excluded from inspection during preconfigured WAF evaluation. You can specify an exact match or a partial match by using a field operator and a field value. Available field operators are: * EQUALS: the operator matches if the field value equals the specified value. * STARTS_WITH: the operator matches if the field value starts with the specified value. * ENDS_WITH: the operator matches if the field value ends with the specified value. * CONTAINS: the operator matches if the field value contains the specified value. * EQUALS_ANY: the operator matches if the field value is any value. A field value must be given if the field operator is not EQUALS_ANY, and cannot be given if the field operator is EQUALS_ANY. For example, --request-header-to-exclude op=EQUALS,val=abc or --request-header-to-exclude op=EQUALS_ANY. This flag can be repeated to specify multiple request headers to exclude. For example, --request-header-to-exclude op=EQUALS,val=abc --request-header-to-exclude op=STARTS_WITH,val=xyz. |
| `--request-header-to-exclude` | [op=OP],[val=VAL] |  | Adds a request header to the request field exclusions associated with the rule set and rule IDs (if given). This specifies a request header whose value will be excluded from inspection during preconfigured WAF evaluation. Refer to the syntax under --request-cookie-to-exclude. This flag can be repeated to specify multiple request headers. |
| `--request-query-param-to-exclude` | [op=OP],[val=VAL] |  | Adds a request query parameter to the request field exclusions associated with the rule set and rule IDs (if given). This specifies a request query parameter in the query string or in the POST body whose value will be excluded from inspection during preconfigured WAF evaluation. Refer to the syntax under --request-cookie-to-exclude. This flag can be repeated to specify multiple request query parameters. |
| `--request-uri-to-exclude` | [op=OP],[val=VAL] |  | Adds a request URI to the request field exclusions associated with the rule set and rule IDs (if given). This specifies a request URI from the request line to be excluded from inspection during preconfigured WAF evaluation. Refer to the syntax under --request-cookie-to-exclude. This flag can be repeated to specify multiple request URIs. |
| `--target-rule-ids` | [RULE_ID,...] |  | A comma-separated list of target rule IDs under the WAF rule set where the request field exclusions being added would apply. If omitted, the added request field exclusions will be associated with the rule set only, which would apply to all the rule IDs under the rule set. |


**Examples:**
```bash
To add specific request field exclusions that are associated with the
target of 'sqli-stable': ['owasp-crs-v030001-id942110-sqli',
'owasp-crs-v030001-id942120-sqli'], run:

    $ gcloud compute org-security-policies rules \
        add-preconfig-waf-exclusion 1000 --security-policy=1234567890 \
        --target-rule-set=sqli-stable \
        --target-rule-ids=owasp-crs-v030001-id942110-sqli,\
    owasp-crs-v030001-id942120-sqli \
        --request-header-to-exclude='op=EQUALS,val=abc' \
        --request-header-to-exclude='op=STARTS_WITH,val=xyz' \
        --request-uri-to-exclude='op=EQUALS_ANY'

To add specific request field exclusions that are associated with the
target of 'sqli-stable': [], run:

    $ gcloud compute org-security-policies rules \
        add-preconfig-waf-exclusion 1000 --security-policy=1234567890 \
        --target-rule-set=sqli-stable \
        --request-cookie-to-exclude='op=EQUALS_ANY'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/org-security-policies/rules/add-preconfig-waf-exclusion)

---
### `gcloud compute org-security-policies rules create`

Create a Compute Engine organizationsecurity policy rule

gcloud compute org-security-policies rules create is used to create
organization security policy rules.

**Synopsis:**
```
gcloud compute org-security-policies rules create PRIORITY --action=ACTION
    --security-policy=SECURITY_POLICY [--cloud-armor]
    [--description=DESCRIPTION] [--dest-ip-ranges=[DEST_IP_RANGE,...]]
    [--direction=DIRECTION] [--[no-]enable-logging]
    [--layer4-configs=[LAYER4_CONFIG,...]] [--organization=ORGANIZATION]
    [--preview] [--target-resources=[TARGET_RESOURCES,...]]
    [--target-service-accounts=[TARGET_SERVICE_ACCOUNTS,...]]
    [--expression=EXPRESSION | --src-ip-ranges=[SRC_IP_RANGE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PRIORITY
   Priority of the security policy rule to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--action` | one of: allow Allows the request from HTTP(S) Load Balancing |  | Action to take if the request matches the match condition. ACTION must be one of: allow Allows the request from HTTP(S) Load Balancing. deny (DEPRECATED) Only used for Hierarchical Firewalls. deny-403 Denies the request from HTTP(S) Load Balancing, with an HTTP response status code of 403. deny-404 Denies the request from HTTP(S) Load Balancing, with an HTTP response status code of 404. deny-502 Denies the request from HTTP(S) Load Balancing, with an HTTP response status code of 502. goto-next Defers enforcement to the next policy in the hierarchy. redirect Redirects the request from HTTP(S) Load Balancing, based on redirect options. |
| `--security-policy` | SECURITY_POLICY |  | short name of the security policy into which the rule should be inserted. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cloud-armor` |  |  | Specified for Hierarchical Cloud Armor rules. |
| `--description` | DESCRIPTION |  | An optional, textual description for the rule. |
| `--dest-ip-ranges` | [DEST_IP_RANGE,...] |  | Destination IP ranges to match for this rule. Can only be specified if DIRECTION is egress. |
| `--direction` | one of: INGRESS, EGRESS |  | Direction of the traffic the rule is applied. The default is to apply on incoming traffic. DIRECTION must be one of: INGRESS, EGRESS. |
| `--[no-]enable-logging` |  |  | Use this flag to enable logging of connections that allowed or denied by this rule. Use --enable-logging to enable and --no-enable-logging to disable. |
| `--layer4-configs` | [LAYER4_CONFIG,...] |  | A list of destination protocols and ports to which the firewall rule will apply. |
| `--organization` | ORGANIZATION |  | Organization which the organization security policy belongs to. Must be set if SECURITY_POLICY is short name. |
| `--preview` |  |  | If specified, the action will not be enforced. |
| `--target-resources` | [TARGET_RESOURCES,...] |  | List of URLs of target resources to which the rule is applied. |
| `--target-service-accounts` | [TARGET_SERVICE_ACCOUNTS,...] |  | List of target service accounts for the rule. |


**Examples:**
```bash
To create a rule with priority 10 in an organization security policy with
ID 123456789, run:

    $ gcloud compute org-security-policies rules create 10 \
        --security-policy=123456789 --action=allow \
        --description=example-rule --cloud-armor
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/org-security-policies/rules/create)

---
### `gcloud compute org-security-policies rules delete`

Delete a Compute Engine organization security policy rule

gcloud compute org-security-policies rules delete is used to delete
organization security policy rule.

**Synopsis:**
```
gcloud compute org-security-policies rules delete PRIORITY
    --security-policy=SECURITY_POLICY [--organization=ORGANIZATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PRIORITY
   Priority of the security policy rule to delete.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--security-policy` | SECURITY_POLICY |  | short name of the security policy into which the rule should be deleted. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION |  | Organization which the organization security policy belongs to. Must be set if SECURITY_POLICY is short name. |


**Examples:**
```bash
To delete a rule with priority 10 in an organization security policy with
ID 123456789, run:

    $ gcloud compute org-security-policies rules delete 10 \
        --security-policy=123456789
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/org-security-policies/rules/delete)

---
### `gcloud compute org-security-policies rules describe`

Describe a Compute Engine organization security policy rule

gcloud compute org-security-policies rules describe is used to describe
organization security policy rule.

**Synopsis:**
```
gcloud compute org-security-policies rules describe PRIORITY
    --security-policy=SECURITY_POLICY [--organization=ORGANIZATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PRIORITY
   Priority of the security policy rule to describe.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--security-policy` | SECURITY_POLICY |  | short name of the security policy into which the rule should be described. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION |  | Organization which the organization security policy belongs to. Must be set if SECURITY_POLICY is short name. |


**Examples:**
```bash
To describe a rule with priority 10 in an organization security policy with
ID 123456789, run:

    $ gcloud compute org-security-policies rules describe 10 \
        --security-policy=123456789
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/org-security-policies/rules/describe)

---
### `gcloud compute org-security-policies rules remove-preconfig-waf-exclusion`

Remove an exclusion configuration for preconfigured WAF evaluation from a security policy rule

gcloud compute org-security-policies rules remove-preconfig-waf-exclusion
is used to remove an exclusion configuration for preconfigured WAF
evaluation from a security policy rule.

Note that request field exclusions are associated with a target, which can
be a single rule set, or a rule set plus a list of rule IDs under the rule
set.

It is possible to remove request field exclusions at 3 levels:
  o Remove specific request field exclusions that are associated with a
    matching target.
  o Remove all the request field exclusions that are associated with a
    matching target.
  o Remove all the request field exclusions that are configured under the
    security policy rule, regardless of the target.

**Synopsis:**
```
gcloud compute org-security-policies rules remove-preconfig-waf-exclusion
    PRIORITY --security-policy=SECURITY_POLICY
    --target-rule-set=TARGET_RULE_SET [--organization=ORGANIZATION]
    [--request-cookie-to-exclude=[op=OP],[val=VAL]]
    [--request-header-to-exclude=[op=OP],[val=VAL]]
    [--request-query-param-to-exclude=[op=OP],[val=VAL]]
    [--request-uri-to-exclude=[op=OP],[val=VAL]]
    [--target-rule-ids=[RULE_ID,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PRIORITY
   Priority of the security policy rule to remove preconfig WAF exclusion.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--security-policy` | SECURITY_POLICY |  | short name of the security policy into which the rule should be updated. |
| `--target-rule-set` | TARGET_RULE_SET |  | Target WAF rule set from where to remove the request field exclusions. This, together with the target rule IDs (if given), determines the target for associating request field exclusions. See --target-rule-ids. Note that the removal of request field exclusions is restricted to those associated with a matching target. Set this flag to * if you want to remove request field exclusions regardless of the target. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION |  | Organization which the organization security policy belongs to. Must be set if SECURITY_POLICY is short name. |
| `--request-cookie-to-exclude` | [op=OP],[val=VAL] |  | Removes a request cookie from the existing request field exclusions associated with the rule set and rule IDs (if given). You can specify an exact match or a partial match by using a field operator and a field value. Available field operators are: * EQUALS: the operator matches if the field value equals the specified value. * STARTS_WITH: the operator matches if the field value starts with the specified value. * ENDS_WITH: the operator matches if the field value ends with the specified value. * CONTAINS: the operator matches if the field value contains the specified value. * EQUALS_ANY: the operator matches if the field value is any value. A field value must be given if the field operator is not EQUALS_ANY, and cannot be given if the field operator is EQUALS_ANY. For example, --request-header-to-exclude op=EQUALS,val=abc or --request-header-to-exclude op=EQUALS_ANY. This flag can be repeated to specify multiple request headers to exclude. For example, --request-header-to-exclude op=EQUALS,val=abc --request-header-to-exclude op=STARTS_WITH,val=xyz. |
| `--request-header-to-exclude` | [op=OP],[val=VAL] |  | Removes a request header from the existing request field exclusions associated with the rule set and rule IDs (if given). Refer to the syntax under --request-cookie-to-exclude. This flag can be repeated to specify multiple request headers. |
| `--request-query-param-to-exclude` | [op=OP],[val=VAL] |  | Removes a request query parameter from the existing request field exclusions associated with the rule set and rule IDs (if given). Refer to the syntax under --request-cookie-to-exclude. This flag can be repeated to specify multiple request query parameters. |
| `--request-uri-to-exclude` | [op=OP],[val=VAL] |  | Removes a request URI from the existing request field exclusions associated with the rule set and rule IDs (if given). Refer to the syntax under --request-cookie-to-exclude. This flag can be repeated to specify multiple request URIs. |
| `--target-rule-ids` | [RULE_ID,...] |  | A comma-separated list of target rule IDs under the WAF rule set from where to remove the request field exclusions. If omitted, the removal of request field exclusions is restricted to those associated with the rule set only, without specific rule IDs. |


**Examples:**
```bash
To remove specific request field exclusions that are associated with the
target of 'sqli-stable': ['owasp-crs-v030001-id942110-sqli',
'owasp-crs-v030001-id942120-sqli'], run:

    $ gcloud compute org-security-policies rules \
        remove-preconfig-waf-exclusion 1000 \
        --security-policy=1234567890 --target-rule-set=sqli-stable \
        --target-rule-ids='owasp-crs-v030001-id942110-sqli',\
    'owasp-crs-v030001-id942120-sqli' \
        --request-header-to-exclude='op=EQUALS,val=abc' \
        --request-header-to-exclude='op=STARTS_WITH,val=xyz' \
        --request-uri-to-exclude='op=EQUALS_ANY'

To remove all the request field exclusions that are associated with the
target of 'sqli-stable': ['owasp-crs-v030001-id942110-sqli',
'owasp-crs-v030001-id942120-sqli'], run:

    $ gcloud compute org-security-policies rules \
        remove-preconfig-waf-exclusion 1000 \
        --security-policy=1234567890 --target-rule-set=sqli-stable \
        --target-rule-ids='owasp-crs-v030001-id942110-sqli',\
    'owasp-crs-v030001-id942120-sqli'

To remove all the request field exclusions that are associated with the
target of 'sqli-stable': [], run:

    $ gcloud compute org-security-policies rules \
        remove-preconfig-waf-exclusion 1000 \
        --security-policy=1234567890 --target-rule-set=sqli-stable

To remove all the request field exclusions that are configured under the
security policy rule, regardless of the target, run:

    $ gcloud compute org-security-policies rules \
        remove-preconfig-waf-exclusion 1000 \
        --security-policy=1234567890 --target-rule-set=*
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/org-security-policies/rules/remove-preconfig-waf-exclusion)

---
### `gcloud compute org-security-policies rules update`

Update a Compute Engine security policy rule

gcloud compute org-security-policies rules update is used to update
organization security policy rules.

**Synopsis:**
```
gcloud compute org-security-policies rules update PRIORITY
    --security-policy=SECURITY_POLICY [--action=ACTION] [--cloud-armor]
    [--description=DESCRIPTION] [--dest-ip-ranges=[DEST_IP_RANGE,...]]
    [--direction=DIRECTION] [--[no-]enable-logging]
    [--layer4-configs=[LAYER4_CONFIG,...]] [--new-priority=NEW_PRIORITY]
    [--organization=ORGANIZATION] [--[no-]preview]
    [--target-resources=[TARGET_RESOURCES,...]]
    [--target-service-accounts=[TARGET_SERVICE_ACCOUNTS,...]]
    [--expression=EXPRESSION | --src-ip-ranges=[SRC_IP_RANGE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PRIORITY
   Priority of the security policy rule to update.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--security-policy` | SECURITY_POLICY |  | short name of the security policy into which the rule should be updated. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--action` | one of: allow Allows the request from HTTP(S) Load Balancing |  | Action to take if the request matches the match condition. ACTION must be one of: allow Allows the request from HTTP(S) Load Balancing. deny (DEPRECATED) Only used for Hierarchical Firewalls. deny-403 Denies the request from HTTP(S) Load Balancing, with an HTTP response status code of 403. deny-404 Denies the request from HTTP(S) Load Balancing, with an HTTP response status code of 404. deny-502 Denies the request from HTTP(S) Load Balancing, with an HTTP response status code of 502. goto-next Defers enforcement to the next policy in the hierarchy. redirect Redirects the request from HTTP(S) Load Balancing, based on redirect options. |
| `--cloud-armor` |  |  | Specified for Hierarchical Cloud Armor rules. |
| `--description` | DESCRIPTION |  | An optional, textual description for the rule. |
| `--dest-ip-ranges` | [DEST_IP_RANGE,...] |  | Destination IP ranges to match for this rule. Can only be specified if DIRECTION is egress. |
| `--direction` | one of: INGRESS, EGRESS |  | Direction of the traffic the rule is applied. The default is to apply on incoming traffic. DIRECTION must be one of: INGRESS, EGRESS. |
| `--[no-]enable-logging` |  |  | Use this flag to enable logging of connections that allowed or denied by this rule. Use --enable-logging to enable and --no-enable-logging to disable. |
| `--layer4-configs` | [LAYER4_CONFIG,...] |  | A list of destination protocols and ports to which the firewall rule will apply. |
| `--new-priority` | NEW_PRIORITY |  | New priority for the rule to update. Valid in [0, 65535]. |
| `--organization` | ORGANIZATION |  | Organization which the organization security policy belongs to. Must be set if SECURITY_POLICY is short name. |
| `--[no-]preview` |  |  | If specified, the action will not be enforced. Use --preview to enable and --no-preview to disable. |
| `--target-resources` | [TARGET_RESOURCES,...] |  | List of URLs of target resources to which the rule is applied. |
| `--target-service-accounts` | [TARGET_SERVICE_ACCOUNTS,...] |  | List of target service accounts for the rule. |


**Examples:**
```bash
To update a rule with priority 10 in an organization security policy with
ID 123456789 to change the action to allow and description to
new-example-rule, run:

    $ gcloud compute org-security-policies rules update 10 \
        --security-policy=123456789 --action=allow \
        --description=new-example-rule
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/org-security-policies/rules/update)

---
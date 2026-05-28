# gcloud compute security-policies

read and manipulate Cloud Armor security policies

### `gcloud compute security-policies add-layer7-ddos-defense-threshold-config`

Add a layer7 ddos defense threshold config to a Compute Engine security policy

gcloud compute security-policies add-layer7-ddos-defense-threshold-config
is used to add layer7 ddos defense threshold configs to security policies.

**Synopsis:**
```
gcloud compute security-policies add-layer7-ddos-defense-threshold-config
    NAME --threshold-config-name=THRESHOLD_CONFIG_NAME
    [--auto-deploy-confidence-threshold=AUTO_DEPLOY_CONFIDENCE_THRESHOLD]
    [--auto-deploy-expiration-sec=AUTO_DEPLOY_EXPIRATION_SEC]
    [--auto-deploy-impacted-baseline-threshold=AUTO_DEPLOY_IMPACTED_BASELINE_THRESHOLD]
    [--auto-deploy-load-threshold=AUTO_DEPLOY_LOAD_THRESHOLD]
    [--detection-absolute-qps=DETECTION_ABSOLUTE_QPS]
    [--detection-load-threshold=DETECTION_LOAD_THRESHOLD]
    [--detection-relative-to-baseline-qps=DETECTION_RELATIVE_TO_BASELINE_QPS]
    [--traffic-granularity-configs=[type=TYPE[,value=VALUE][,
      enableEachUniqueValue=ENABLE_EACH_UNIQUE_VALUE];...;...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the security policy to update.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--threshold-config-name` | THRESHOLD_CONFIG_NAME |  | The name for the threshold config. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--auto-deploy-confidence-threshold` | AUTO_DEPLOY_CONFIDENCE_THRESHOLD |  | The threshold of the confidence of an identified attack, over which auto-deploy takes action. |
| `--auto-deploy-expiration-sec` | AUTO_DEPLOY_EXPIRATION_SEC |  | The duration of actions, if any, taken by auto-deploy. |
| `--auto-deploy-impacted-baseline-threshold` | AUTO_DEPLOY_IMPACTED_BASELINE_THRESHOLD |  | The threshold on the estimated impact to the baseline traffic of a suggested mitigation, below which auto-deploy takes action. |
| `--auto-deploy-load-threshold` | AUTO_DEPLOY_LOAD_THRESHOLD |  | The threshold on backend's load, over which auto-deploy takes action. |
| `--detection-absolute-qps` | DETECTION_ABSOLUTE_QPS |  | The absolute QPS of the incoming traffic, over which adaptive protection detects an attack. |
| `--detection-load-threshold` | DETECTION_LOAD_THRESHOLD |  | The threshold on backend's load, over which adaptive protection detects an attack. |
| `--detection-relative-to-baseline-qps` | DETECTION_RELATIVE_TO_BASELINE_QPS |  | The QPS of the incoming traffic relative to the average baseline QPS, over which adaptive protection detects an attack. |
| `--traffic-granularity-configs` | [type=TYPE[,value=VALUE][,enableEachUniqueValue=ENABLE_EACH_UNIQUE_VALUE];...;...] |  | Specify up to 2 configs matching a specifc type/value of traffic. |


**Examples:**
```bash
To add a layer7 ddos defense threshold config run the following command:

    $ gcloud compute security-policies \
        add-layer7-ddos-defense-threshold-config NAME \
        --threshold-config-name=my-threshold-config-name \
        --auto-deploy-load-threshold=0.7 \
        --auto-deploy-confidence-threshold=0.8 \
        --auto-deploy-impacted-baseline-threshold=0.1 \
        --auto-deploy-expiration-sec=4800 \
        --detection-load-threshold=0.4 --detection-absolute-qps=1000 \
        --detection-relative-to-baseline-qps=2.0 \
        --traffic-granularity-configs=type=HTTP_HEADER_HOST,\
    value=www.my-test-host.com;type=HTTP_PATH,enableEachUniqueValue=true
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/security-policies/add-layer7-ddos-defense-threshold-config)

---
### `gcloud compute security-policies add-user-defined-field`

Add a user defined field to a Compute Engine security policy

gcloud compute security-policies add-user-defined-field is used to add user
defined fields to security policies.

**Synopsis:**
```
gcloud compute security-policies add-user-defined-field NAME --base=BASE
    --offset=OFFSET --size=SIZE
    --user-defined-field-name=USER_DEFINED_FIELD_NAME [--mask=MASK]
    [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the security policy to update.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--base` | one of: ipv4, ipv6, tcp, udp |  | The base relative to which offset is measured. BASE must be one of: ipv4, ipv6, tcp, udp. |
| `--offset` | OFFSET |  | Offset of the first byte of the field (in network byte order) relative to base. |
| `--size` | SIZE |  | Size of the field in bytes. Valid values: 1-4. |
| `--user-defined-field-name` | USER_DEFINED_FIELD_NAME |  | The name for the user defined field. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--mask` | MASK |  | If specified, apply this mask (bitwise AND) to the field to ignore bits before matching. Encoded as a hexadecimal number (starting with "0x"). |
| `--region` | REGION |  | Region of the security policy to update. Overrides the default compute/region property value for this command invocation. |


**Examples:**
```bash
To add a user defined field run this:

    $ gcloud compute security-policies add-user-defined-field \
        SECURITY_POLICY --user-defined-field-name=my-field --base=ipv6 \
        --offset=10 --size=3
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/security-policies/add-user-defined-field)

---
### `gcloud compute security-policies create`

Create a Compute Engine security policy

gcloud compute security-policies create is used to create security
policies. A security policy policy is a set of rules that controls access
to various resources.

**Synopsis:**
```
gcloud compute security-policies create NAME [--description=DESCRIPTION]
    [--file-format=FILE_FORMAT]
    [--file-name=FILE_NAME | --type=SECURITY_POLICY_TYPE]
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the security policy to create.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional, textual description for the security policy. |
| `--file-format` | one of: json, yaml |  | The format of the file to create the security policy config from. Specify either yaml or json. Defaults to yaml if not specified. Will be ignored if --file-name is not specified. FILE_FORMAT must be one of: json, yaml. |


**Examples:**
```bash
To create a security policy with a given type and description, run:

    $ gcloud compute security-policies create my-policy \
        --type=CLOUD_ARMOR_EDGE --description="policy description"

To create a security from an input file, run:

    $ gcloud compute security-policies create my-policy \
        --file-name=my-file-name
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/security-policies/create)

---
### `gcloud compute security-policies delete`

Delete security policies

gcloud compute security-policies delete deletes Compute Engine security
policies. Security policies can only be deleted when no other resources
(e.g., backend services) refer to them.

**Synopsis:**
```
gcloud compute security-policies delete NAME [NAME ...]
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME [NAME ...]
   Names of the security policies to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the security policies are global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the security policies to delete. Overrides the default compute/region property value for this command invocation. |


**Examples:**
```bash
To delete a security policy, run:

    $ gcloud compute security-policies delete my-policy
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/security-policies/delete)

---
### `gcloud compute security-policies describe`

Describe a Compute Engine security policy

gcloud compute security-policies describe displays all data associated with
Compute Engine security policy in a project.

**Synopsis:**
```
gcloud compute security-policies describe NAME [--global | --region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the security policy to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the security policy is global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the security policy to describe. Overrides the default compute/region property value for this command invocation. |


**Examples:**
```bash
To describe a security policy, run:

    $ gcloud compute security-policies describe my-policy
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/security-policies/describe)

---
### `gcloud compute security-policies export`

Export security policy configs into YAML or JSON files

gcloud compute security-policies export exports all data associated with
Compute Engine security policy into a local file.

**Synopsis:**
```
gcloud compute security-policies export NAME --file-name=FILE_NAME
    [--file-format=FILE_FORMAT] [--global | --region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the security policy to export.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--file-name` | FILE_NAME |  | The name of the file to export the security policy config to. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--file-format` | one of: json, yaml |  | The format of the file to export the security policy config to. Specify either yaml or json. Defaults to yaml if not specified. FILE_FORMAT must be one of: json, yaml. |


**Examples:**
```bash
To export a security policy in JSON format to a given file, run:

    $ gcloud compute security-policies export my-policy \
        --file-name=my-file-name --file-format=json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/security-policies/export)

---
### `gcloud compute security-policies import`

Import security policy configs into your project

gcloud compute security-policies import imports a security policy to update
an existing policy. To create a new policy from a file please use the
create command instead.

**Synopsis:**
```
gcloud compute security-policies import NAME --file-name=FILE_NAME
    [--file-format=FILE_FORMAT] [--global | --region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the security policy to import.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--file-name` | FILE_NAME |  | The name of the JSON or YAML file to import the security policy config from. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--file-format` | one of: json, yaml |  | The format of the file to import the security policy config from. Specify either yaml or json. Defaults to yaml if not specified. FILE_FORMAT must be one of: json, yaml. |


**Examples:**
```bash
To import a security policy from a YAML file run this:

    $ gcloud compute security-policies import --file-name=myFile
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/security-policies/import)

---
### `gcloud compute security-policies list`

List Google Compute Engine security policies

gcloud compute security-policies list displays all Google Compute Engine
security policies in a project.

**Synopsis:**
```
gcloud compute security-policies list [NAME ...]
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
To list all security policies in a project in table form, run:

    $ gcloud compute security-policies list

To list the URIs of all security policies in a project, run:

    $ gcloud compute security-policies list --uri
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/security-policies/list)

---
### `gcloud compute security-policies list-preconfigured-expression-sets`

List all available preconfigured expression sets

gcloud compute security-policies list-preconfigured-expression-sets lists
all available preconfigured expression sets that can be used with the Cloud
Armor rules language.

**Synopsis:**
```
gcloud compute security-policies list-preconfigured-expression-sets
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all current preconfigured expressions sets run this:

    $ gcloud compute security-policies list-preconfigured-expression-sets
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/security-policies/list-preconfigured-expression-sets)

---
### `gcloud compute security-policies remove-layer7-ddos-defense-threshold-config`

Remove a layer7 ddos defense threshold config from a Compute Engine security policy

gcloud compute security-policies
remove-layer7-ddos-defense-threshold-config is used to remove layer7 ddos
defense threshold configs from security policies.

**Synopsis:**
```
gcloud compute security-policies
    remove-layer7-ddos-defense-threshold-config NAME
    --threshold-config-name=THRESHOLD_CONFIG_NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the security policy to update.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--threshold-config-name` | THRESHOLD_CONFIG_NAME |  | The name for the threshold config. |


**Examples:**
```bash
To remove a layer7 ddos defense threshold config run the following command:

    $ gcloud compute security-policies \
        remove-layer7-ddos-defense-threshold-config NAME \
        --threshold-config-name=my-threshold-config-name
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/security-policies/remove-layer7-ddos-defense-threshold-config)

---
### `gcloud compute security-policies remove-user-defined-field`

Remove a user defined field from a Compute Engine security policy

gcloud compute security-policies remove-user-defined-field is used to
remove user defined fields from security policies.

**Synopsis:**
```
gcloud compute security-policies remove-user-defined-field NAME
    --user-defined-field-name=USER_DEFINED_FIELD_NAME [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the security policy to update.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--user-defined-field-name` | USER_DEFINED_FIELD_NAME |  | The name of the user defined field to remove. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the security policy to update. Overrides the default compute/region property value for this command invocation. |


**Examples:**
```bash
To remove a user defined field run this:

    $ gcloud compute security-policies remove-user-defined-field \
        SECURITY_POLICY --user-defined-field-name=my-field
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/security-policies/remove-user-defined-field)

---
### `gcloud compute security-policies update`

Update a Compute Engine security policy

gcloud compute security-policies update is used to update security
policies.

**Synopsis:**
```
gcloud compute security-policies update NAME [--description=DESCRIPTION]
    [--enable-layer7-ddos-defense]
    [--json-custom-content-types=[CONTENT_TYPE,...]]
    [--json-parsing=JSON_PARSING]
    [--layer7-ddos-defense-rule-visibility=VISIBILITY_TYPE]
    [--log-level=LOG_LEVEL]
    [--network-ddos-protection=NETWORK_DDOS_PROTECTION]
    [--recaptcha-redirect-site-key=RECAPTCHA_REDIRECT_SITE_KEY]
    [--user-ip-request-headers=[USER_IP_REQUEST_HEADER,...]]
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the security policy to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional, textual description for the security policy. |
| `--enable-layer7-ddos-defense` |  |  | Whether to enable Cloud Armor Layer 7 DDoS Defense Adaptive Protection. |
| `--json-custom-content-types` | [CONTENT_TYPE,...] |  | A comma-separated list of custom Content-Type header values to apply JSON parsing for preconfigured WAF rules. Only applicable when JSON parsing is enabled, like --json-parsing=STANDARD. When configuring a Content-Type header value, only the type/subtype needs to be specified, and the parameters should be excluded. |
| `--json-parsing` | one of: DISABLED, STANDARD, STANDARD_WITH_GRAPHQL |  | The JSON parsing behavior for this rule. Must be one of the following values: [DISABLED, STANDARD, STANDARD_WITH_GRAPHQL]. JSON_PARSING must be one of: DISABLED, STANDARD, STANDARD_WITH_GRAPHQL. |
| `--layer7-ddos-defense-rule-visibility` | one of: STANDARD, PREMIUM |  | The visibility type indicates whether the rules are opaque or transparent. VISIBILITY_TYPE must be one of: STANDARD, PREMIUM. |
| `--log-level` | one of: NORMAL, VERBOSE |  | The level of detail to display for WAF logging. LOG_LEVEL must be one of: NORMAL, VERBOSE. |
| `--network-ddos-protection` | one of: STANDARD, ADVANCED, ADVANCED_PREVIEW |  | The DDoS protection level for network load balancing and instances with external IPs. NETWORK_DDOS_PROTECTION must be one of: STANDARD, ADVANCED, ADVANCED_PREVIEW. |
| `--recaptcha-redirect-site-key` | RECAPTCHA_REDIRECT_SITE_KEY |  | The reCAPTCHA site key to be used for rules using the redirect action and the google-recaptcha redirect type under the security policy. |
| `--user-ip-request-headers` | [USER_IP_REQUEST_HEADER,...] |  | A comma-separated list of request header names to use for resolving the caller's user IP address. |


**Examples:**
```bash
To update the description run this:

    $ gcloud compute security-policies update SECURITY_POLICY \
        --description='new description'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/security-policies/update)

---

## `gcloud compute security-policies rules` — read and manipulate Compute Engine security policies rules
### `gcloud compute security-policies rules add-preconfig-waf-exclusion`

Add an exclusion configuration for preconfigured WAF evaluation into a security policy rule

gcloud compute security-policies rules add-preconfig-waf-exclusion is used
to add an exclusion configuration for preconfigured WAF evaluation into a
security policy rule.

Note that request field exclusions are associated with a target, which can
be a single rule set, or a rule set plus a list of rule IDs under the rule
set.

**Synopsis:**
```
gcloud compute security-policies rules add-preconfig-waf-exclusion PRIORITY
    --target-rule-set=TARGET_RULE_SET [--region=REGION]
    [--request-cookie-to-exclude=[op=OP],[val=VAL]]
    [--request-header-to-exclude=[op=OP],[val=VAL]]
    [--request-query-param-to-exclude=[op=OP],[val=VAL]]
    [--request-uri-to-exclude=[op=OP],[val=VAL]]
    [--security-policy=SECURITY_POLICY] [--target-rule-ids=[RULE_ID,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PRIORITY
   The priority of the rule to add the exclusion configuration for
   preconfigured WAF evaluation. Rules are evaluated in order from highest
   priority to lowest priority where 0 is the highest priority and
   2147483647 is the lowest priority.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--target-rule-set` | TARGET_RULE_SET |  | Target WAF rule set where the request field exclusions being added would apply. This, together with the target rule IDs (if given), determines the target for associating request field exclusions. See --target-rule-ids. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the security policy to add the exclusion configuration for preconfigured WAF evaluation. If not specified, you might be prompted to select a region (interactive mode only). A list of regions can be fetched by running: $ gcloud compute regions list Overrides the default compute/region property value for this command invocation. |
| `--request-cookie-to-exclude` | [op=OP],[val=VAL] |  | Adds a request cookie to the request field exclusions associated with the rule set and rule IDs (if given). This specifies a request cookie whose value will be excluded from inspection during preconfigured WAF evaluation. You can specify an exact match or a partial match by using a field operator and a field value. Available field operators are: * EQUALS: the operator matches if the field value equals the specified value. * STARTS_WITH: the operator matches if the field value starts with the specified value. * ENDS_WITH: the operator matches if the field value ends with the specified value. * CONTAINS: the operator matches if the field value contains the specified value. * EQUALS_ANY: the operator matches if the field value is any value. A field value must be given if the field operator is not EQUALS_ANY, and cannot be given if the field operator is EQUALS_ANY. For example, --request-header-to-exclude op=EQUALS,val=abc or --request-header-to-exclude op=EQUALS_ANY. This flag can be repeated to specify multiple request headers to exclude. For example, --request-header-to-exclude op=EQUALS,val=abc --request-header-to-exclude op=STARTS_WITH,val=xyz. |
| `--request-header-to-exclude` | [op=OP],[val=VAL] |  | Adds a request header to the request field exclusions associated with the rule set and rule IDs (if given). This specifies a request header whose value will be excluded from inspection during preconfigured WAF evaluation. Refer to the syntax under --request-cookie-to-exclude. This flag can be repeated to specify multiple request headers. |
| `--request-query-param-to-exclude` | [op=OP],[val=VAL] |  | Adds a request query parameter to the request field exclusions associated with the rule set and rule IDs (if given). This specifies a request query parameter in the query string or in the POST body whose value will be excluded from inspection during preconfigured WAF evaluation. Refer to the syntax under --request-cookie-to-exclude. This flag can be repeated to specify multiple request query parameters. |
| `--request-uri-to-exclude` | [op=OP],[val=VAL] |  | Adds a request URI to the request field exclusions associated with the rule set and rule IDs (if given). This specifies a request URI from the request line to be excluded from inspection during preconfigured WAF evaluation. Refer to the syntax under --request-cookie-to-exclude. This flag can be repeated to specify multiple request URIs. |
| `--security-policy` | SECURITY_POLICY |  | The security policy that this rule belongs to. |
| `--target-rule-ids` | [RULE_ID,...] |  | A comma-separated list of target rule IDs under the WAF rule set where the request field exclusions being added would apply. If omitted, the added request field exclusions will be associated with the rule set only, which would apply to all the rule IDs under the rule set. |


**Examples:**
```bash
To add specific request field exclusions that are associated with the
target of 'sqli-stable': ['owasp-crs-v030001-id942110-sqli',
'owasp-crs-v030001-id942120-sqli'], run:

    $ gcloud compute security-policies rules \
        add-preconfig-waf-exclusion 1000 --security-policy=my-policy \
        --target-rule-set=sqli-stable \
        --target-rule-ids=owasp-crs-v030001-id942110-sqli,\
    owasp-crs-v030001-id942120-sqli \
        --request-header-to-exclude=op=EQUALS,val=abc \
        --request-header-to-exclude=op=STARTS_WITH,val=xyz \
        --request-uri-to-exclude=op=EQUALS_ANY

To add specific request field exclusions that are associated with the
target of 'sqli-stable': [], run:

    $ gcloud compute security-policies rules \
        add-preconfig-waf-exclusion 1000 --security-policy=my-policy \
        --target-rule-set=sqli-stable \
        --request-cookie-to-exclude=op=EQUALS_ANY
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/security-policies/rules/add-preconfig-waf-exclusion)

---
### `gcloud compute security-policies rules create`

Create a Compute Engine security policy rule

gcloud compute security-policies rules create is used to create security
policy rules.

**Synopsis:**
```
gcloud compute security-policies rules create PRIORITY --action=ACTION
    (--expression=EXPRESSION --network-dest-ip-ranges=[DEST_IP_RANGE,...]
      --network-dest-ports=[DEST_PORT,...]
      --network-ip-protocols=[IP_PROTOCOL,...]
      --network-src-asns=[SRC_ASN,...]
      --network-src-ip-ranges=[SRC_IP_RANGE,...]
      --network-src-ports=[SRC_PORT,...]
      --network-src-region-codes=[SRC_REGION_CODE,...]
      --network-user-defined-fields=[NAME;VALUE:VALUE:...,...]
      --src-ip-ranges=[SRC_IP_RANGE,...])
    [--ban-duration-sec=BAN_DURATION_SEC]
    [--ban-threshold-count=BAN_THRESHOLD_COUNT]
    [--ban-threshold-interval-sec=BAN_THRESHOLD_INTERVAL_SEC]
    [--conform-action=CONFORM_ACTION] [--description=DESCRIPTION]
    [--enforce-on-key=ENFORCE_ON_KEY]
    [--enforce-on-key-configs=[[all],[ip],[xff-ip],
      [http-cookie=HTTP_COOKIE],[http-header=HTTP_HEADER],[http-path],[sni],
      [region-code],
      [tls-ja3-fingerprint],[user-ip],[tls-ja4-fingerprint]],[...]]
    [--enforce-on-key-name=ENFORCE_ON_KEY_NAME]
    [--exceed-action=EXCEED_ACTION]
    [--exceed-redirect-target=EXCEED_REDIRECT_TARGET]
    [--exceed-redirect-type=EXCEED_REDIRECT_TYPE] [--preview]
    [--rate-limit-threshold-count=RATE_LIMIT_THRESHOLD_COUNT]
    [--rate-limit-threshold-interval-sec=RATE_LIMIT_THRESHOLD_INTERVAL_SEC]
    [--recaptcha-action-site-keys=[SITE_KEY,...]]
    [--recaptcha-session-site-keys=[SITE_KEY,...]]
    [--redirect-target=REDIRECT_TARGET] [--redirect-type=REDIRECT_TYPE]
    [--region=REGION]
    [--request-headers-to-add=[REQUEST_HEADERS_TO_ADD,...]]
    [--security-policy=SECURITY_POLICY] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PRIORITY
   The priority of the rule to add. Rules are evaluated in order from
   highest priority to lowest priority where 0 is the highest priority and
   2147483647 is the lowest priority.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--action` | one of: allow Allows the request from HTTP(S) Load Balancing |  | The action to take if the request matches the match condition. ACTION must be one of: allow Allows the request from HTTP(S) Load Balancing. deny Denies the request from TCP/SSL Proxy and Network Load Balancing. deny-403 Denies the request from HTTP(S) Load Balancing, with an HTTP response status code of 403. deny-404 Denies the request from HTTP(S) Load Balancing, with an HTTP response status code of 404. deny-502 Denies the request from HTTP(S) Load Balancing, with an HTTP response status code of 502. rate-based-ban Enforces rate-based ban action from HTTP(S) Load Balancing, based on rate limit options. redirect Redirects the request from HTTP(S) Load Balancing, based on redirect options. redirect-to-recaptcha (DEPRECATED) Redirects the request from HTTP(S) Load Balancing, for reCAPTCHA Enterprise assessment. This flag choice is deprecated. Use --action=redirect and --redirect-type=google-recaptcha instead. throttle Enforces throttle action from HTTP(S) Load Balancing, based on rate limit options. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--ban-duration-sec` | BAN_DURATION_SEC |  | Can only be specified if the action for the rule is rate-based-ban. If specified, determines the time (in seconds) the traffic will continue to be banned by the rate limit after the rate falls below the threshold. |
| `--ban-threshold-count` | BAN_THRESHOLD_COUNT |  | Number of HTTP(S) requests for calculating the threshold for banning requests. Can only be specified if the action for the rule is rate-based-ban. If specified, the key will be banned for the configured BAN_DURATION_SEC when the number of requests that exceed the RATE_LIMIT_THRESHOLD_COUNT also exceed this BAN_THRESHOLD_COUNT. |
| `--ban-threshold-interval-sec` | BAN_THRESHOLD_INTERVAL_SEC |  | Interval over which the threshold for banning requests is computed. Can only be specified if the action for the rule is rate-based-ban. If specified, the key will be banned for the configured BAN_DURATION_SEC when the number of requests that exceed the RATE_LIMIT_THRESHOLD_COUNT also exceed this BAN_THRESHOLD_COUNT. |
| `--conform-action` | CONFORM_ACTION |  | Action to take when requests are under the given threshold. When requests are throttled, this is also the action for all requests which are not dropped. CONFORM_ACTION must be (only one value is supported): allow. |
| `--description` | DESCRIPTION |  | An optional, textual description for the rule. |
| `--enforce-on-key` | one of: ip, all, http-header, xff-ip, http-cookie, http-path, sni, region-code, tls-ja3-fingerprint, user-ip, tls-ja4-fingerprint |  | Different key types available to enforce the rate limit threshold limit on: * ip: each client IP address has this limit enforced separately * all: a single limit is applied to all requests matching this rule * http-header: key type takes the value of the HTTP header configured in enforce-on-key-name as the key value * xff-ip: takes the original IP address specified in the X-Forwarded-For header as the key * http-cookie: key type takes the value of the HTTP cookie configured in enforce-on-key-name as the key value * http-path: key type takes the value of the URL path in the request * sni: key type takes the value of the server name indication from the TLS session of the HTTPS request * region-code: key type takes the value of the region code from which the request originates * tls-ja3-fingerprint: key type takes the value of JA3 TLS/SSL fingerprint if the client connects using HTTPS, HTTP/2 or HTTP/3 * user-ip: key type takes the IP address of the originating client, which is resolved based on user-ip-request-headers configured with the security policy * tls-ja4-fingerprint: key type takes the value of JA4 TLS/SSL fingerprint if the client connects using HTTPS, HTTP/2 or HTTP/3 ENFORCE_ON_KEY must be one of: ip, all, http-header, xff-ip, http-cookie, http-path, sni, region-code, tls-ja3-fingerprint, user-ip, tls-ja4-fingerprint. |
| `--enforce-on-key-configs` | [[all],[ip],[xff-ip],[http-cookie=HTTP_COOKIE],[http-header=HTTP_HEADER],[http-path],[sni],[region-code],[tls-ja3-fingerprint],[user-ip],[tls-ja4-fingerprint]],[...] |  | Specify up to 3 key type/name pairs to rate limit. Valid key types are: * ip: each client IP address has this limit enforced separately * all: a single limit is applied to all requests matching this rule * http-header: key type takes the value of the HTTP header configured in enforce-on-key-name as the key value * xff-ip: takes the original IP address specified in the X-Forwarded-For header as the key * http-cookie: key type takes the value of the HTTP cookie configured in enforce-on-key-name as the key value * http-path: key type takes the value of the URL path in the request * sni: key type takes the value of the server name indication from the TLS session of the HTTPS request * region-code: key type takes the value of the region code from which the request originates * tls-ja3-fingerprint: key type takes the value of JA3 TLS/SSL fingerprint if the client connects using HTTPS, HTTP/2 or HTTP/3 * user-ip: key type takes the IP address of the originating client, which is resolved based on user-ip-request-headers configured with the security policy * tls-ja4-fingerprint: key type takes the value of JA4 TLS/SSL fingerprint if the client connects using HTTPS, HTTP/2 or HTTP/3 Key names are only applicable to the following key types: * http-header: The name of the HTTP header whose value is taken as the key value. * http-cookie: The name of the HTTP cookie whose value is taken as the key value. |
| `--enforce-on-key-name` | ENFORCE_ON_KEY_NAME |  | Determines the key name for the rate limit key. Applicable only for the following rate limit key types: * http-header: The name of the HTTP header whose value is taken as the key value. * http-cookie: The name of the HTTP cookie whose value is taken as the key value. |
| `--exceed-action` | one of: deny-403, deny-404, deny-429, deny-502, deny, redirect |  | Action to take when requests are above the given threshold. When a request is denied, return the specified HTTP response code. When a request is redirected, use the redirect options based on --exceed-redirect-type and --exceed-redirect-target below. EXCEED_ACTION must be one of: deny-403, deny-404, deny-429, deny-502, deny, redirect. |
| `--exceed-redirect-target` | EXCEED_REDIRECT_TARGET |  | URL target for the redirect action that is configured as the exceed action when the redirect type is external-302. |
| `--exceed-redirect-type` | one of: google-recaptcha, external-302 |  | Type for the redirect action that is configured as the exceed action. EXCEED_REDIRECT_TYPE must be one of: google-recaptcha, external-302. |
| `--preview` |  |  | If specified, the action will not be enforced. |
| `--rate-limit-threshold-count` | RATE_LIMIT_THRESHOLD_COUNT |  | Number of HTTP(S) requests for calculating the threshold for rate limiting requests. |
| `--rate-limit-threshold-interval-sec` | RATE_LIMIT_THRESHOLD_INTERVAL_SEC |  | Interval over which the threshold for rate limiting requests is computed. |
| `--recaptcha-action-site-keys` | [SITE_KEY,...] |  | A comma-separated list of site keys to be used during the validation of reCAPTCHA action-tokens. The provided site keys need to be created from the reCAPTCHA API under the same project where the security policy is created. |
| `--recaptcha-session-site-keys` | [SITE_KEY,...] |  | A comma-separated list of site keys to be used during the validation of reCAPTCHA session-tokens. The provided site keys need to be created from the reCAPTCHA API under the same project where the security policy is created. |
| `--redirect-target` | REDIRECT_TARGET |  | URL target for the redirect action. Must be specified if the redirect type is external-302. Cannot be specified if the redirect type is google-recaptcha. |
| `--redirect-type` | one of: google-recaptcha, external-302 |  | Type for the redirect action. Default to external-302 if unspecified while --redirect-target is given. REDIRECT_TYPE must be one of: google-recaptcha, external-302. |
| `--region` | REGION |  | Region of the security policy to add. If not specified, you might be prompted to select a region (interactive mode only). A list of regions can be fetched by running: $ gcloud compute regions list Overrides the default compute/region property value for this command invocation. |
| `--request-headers-to-add` | [REQUEST_HEADERS_TO_ADD,...] |  | A comma-separated list of header names and header values to add to requests that match this rule. |
| `--security-policy` | SECURITY_POLICY |  | The security policy that this rule belongs to. |


**Examples:**
```bash
To create a rule at priority 1000 to block the IP range 1.2.3.0/24, run:

    $ gcloud compute security-policies rules create 1000 \
        --action=deny-403 --security-policy=my-policy \
        --description="block 1.2.3.0/24" --src-ip-ranges=1.2.3.0/24
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/security-policies/rules/create)

---
### `gcloud compute security-policies rules delete`

Delete Compute Engine security policy rules

gcloud compute security-policies rules delete is used to delete security
policy rules.

**Synopsis:**
```
gcloud compute security-policies rules delete [PRIORITY ...]
    [--region=REGION] [--security-policy=SECURITY_POLICY]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[PRIORITY ...]
   The priority of the rules to delete. Rules are evaluated in order from
   highest priority to lowest priority where 0 is the highest priority and
   2147483647 is the lowest priority.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the security policy to delete. If not specified, you might be prompted to select a region (interactive mode only). A list of regions can be fetched by running: $ gcloud compute regions list Overrides the default compute/region property value for this command invocation. |
| `--security-policy` | SECURITY_POLICY |  | The security policy that this rule belongs to. |


**Examples:**
```bash
To delete the rule at priority 1000, run:

    $ gcloud compute security-policies rules delete 1000 \
        --security-policy=my-policy
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/security-policies/rules/delete)

---
### `gcloud compute security-policies rules describe`

Describe a Compute Engine security policy rule

gcloud compute security-policies rules describe displays all data
associated with a security policy rule.

**Synopsis:**
```
gcloud compute security-policies rules describe PRIORITY [--region=REGION]
    [--security-policy=SECURITY_POLICY] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PRIORITY
   The priority of the rule to describe. Rules are evaluated in order from
   highest priority to lowest priority where 0 is the highest priority and
   2147483647 is the lowest priority.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the security policy to describe. If not specified, you might be prompted to select a region (interactive mode only). A list of regions can be fetched by running: $ gcloud compute regions list Overrides the default compute/region property value for this command invocation. |
| `--security-policy` | SECURITY_POLICY |  | The security policy that this rule belongs to. |


**Examples:**
```bash
To describe the rule at priority 1000, run:

    $ gcloud compute security-policies rules describe 1000 \
        --security-policy=my-policy
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/security-policies/rules/describe)

---
### `gcloud compute security-policies rules remove-preconfig-waf-exclusion`

Remove an exclusion configuration for preconfigured WAF evaluation from a security policy rule

gcloud compute security-policies rules remove-preconfig-waf-exclusion is
used to remove an exclusion configuration for preconfigured WAF evaluation
from a security policy rule.

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
gcloud compute security-policies rules remove-preconfig-waf-exclusion
    PRIORITY --target-rule-set=TARGET_RULE_SET [--region=REGION]
    [--request-cookie-to-exclude=[op=OP],[val=VAL]]
    [--request-header-to-exclude=[op=OP],[val=VAL]]
    [--request-query-param-to-exclude=[op=OP],[val=VAL]]
    [--request-uri-to-exclude=[op=OP],[val=VAL]]
    [--security-policy=SECURITY_POLICY] [--target-rule-ids=[RULE_ID,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PRIORITY
   The priority of the rule to remove the exclusion configuration for
   preconfigured WAF evaluation. Rules are evaluated in order from highest
   priority to lowest priority where 0 is the highest priority and
   2147483647 is the lowest priority.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--target-rule-set` | TARGET_RULE_SET |  | Target WAF rule set from where to remove the request field exclusions. This, together with the target rule IDs (if given), determines the target for associating request field exclusions. See --target-rule-ids. Note that the removal of request field exclusions is restricted to those associated with a matching target. Set this flag to * if you want to remove request field exclusions regardless of the target. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the security policy to remove the exclusion configuration for preconfigured WAF evaluation. If not specified, you might be prompted to select a region (interactive mode only). A list of regions can be fetched by running: $ gcloud compute regions list Overrides the default compute/region property value for this command invocation. |
| `--request-cookie-to-exclude` | [op=OP],[val=VAL] |  | Removes a request cookie from the existing request field exclusions associated with the rule set and rule IDs (if given). You can specify an exact match or a partial match by using a field operator and a field value. Available field operators are: * EQUALS: the operator matches if the field value equals the specified value. * STARTS_WITH: the operator matches if the field value starts with the specified value. * ENDS_WITH: the operator matches if the field value ends with the specified value. * CONTAINS: the operator matches if the field value contains the specified value. * EQUALS_ANY: the operator matches if the field value is any value. A field value must be given if the field operator is not EQUALS_ANY, and cannot be given if the field operator is EQUALS_ANY. For example, --request-header-to-exclude op=EQUALS,val=abc or --request-header-to-exclude op=EQUALS_ANY. This flag can be repeated to specify multiple request headers to exclude. For example, --request-header-to-exclude op=EQUALS,val=abc --request-header-to-exclude op=STARTS_WITH,val=xyz. |
| `--request-header-to-exclude` | [op=OP],[val=VAL] |  | Removes a request header from the existing request field exclusions associated with the rule set and rule IDs (if given). Refer to the syntax under --request-cookie-to-exclude. This flag can be repeated to specify multiple request headers. |
| `--request-query-param-to-exclude` | [op=OP],[val=VAL] |  | Removes a request query parameter from the existing request field exclusions associated with the rule set and rule IDs (if given). Refer to the syntax under --request-cookie-to-exclude. This flag can be repeated to specify multiple request query parameters. |
| `--request-uri-to-exclude` | [op=OP],[val=VAL] |  | Removes a request URI from the existing request field exclusions associated with the rule set and rule IDs (if given). Refer to the syntax under --request-cookie-to-exclude. This flag can be repeated to specify multiple request URIs. |
| `--security-policy` | SECURITY_POLICY |  | The security policy that this rule belongs to. |
| `--target-rule-ids` | [RULE_ID,...] |  | A comma-separated list of target rule IDs under the WAF rule set from where to remove the request field exclusions. If omitted, the removal of request field exclusions is restricted to those associated with the rule set only, without specific rule IDs. |


**Examples:**
```bash
To remove specific request field exclusions that are associated with the
target of 'sqli-stable': ['owasp-crs-v030001-id942110-sqli',
'owasp-crs-v030001-id942120-sqli'], run:

    $ gcloud compute security-policies rules \
        remove-preconfig-waf-exclusion 1000 \
        --security-policy=my-policy --target-rule-set=sqli-stable \
        --target-rule-ids=owasp-crs-v030001-id942110-sqli,\
    owasp-crs-v030001-id942120-sqli \
        --request-header-to-exclude=op=EQUALS,val=abc \
        --request-header-to-exclude=op=STARTS_WITH,val=xyz \
        --request-uri-to-exclude=op=EQUALS_ANY

To remove all the request field exclusions that are associated with the
target of 'sqli-stable': ['owasp-crs-v030001-id942110-sqli',
'owasp-crs-v030001-id942120-sqli'], run:

    $ gcloud compute security-policies rules \
        remove-preconfig-waf-exclusion 1000 \
        --security-policy=my-policy --target-rule-set=sqli-stable \
        --target-rule-ids=owasp-crs-v030001-id942110-sqli,\
    owasp-crs-v030001-id942120-sqli

To remove all the request field exclusions that are associated with the
target of 'sqli-stable': [], run:

    $ gcloud compute security-policies rules \
        remove-preconfig-waf-exclusion 1000 \
        --security-policy=my-policy --target-rule-set=sqli-stable

To remove all the request field exclusions that are configured under the
security policy rule, regardless of the target, run:

    $ gcloud compute security-policies rules \
        remove-preconfig-waf-exclusion 1000 \
        --security-policy=my-policy --target-rule-set=*
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/security-policies/rules/remove-preconfig-waf-exclusion)

---
### `gcloud compute security-policies rules update`

Update a Compute Engine security policy rule

gcloud compute security-policies rules update is used to update security
policy rules.

**Synopsis:**
```
gcloud compute security-policies rules update PRIORITY [--action=ACTION]
    [--ban-duration-sec=BAN_DURATION_SEC]
    [--ban-threshold-count=BAN_THRESHOLD_COUNT]
    [--ban-threshold-interval-sec=BAN_THRESHOLD_INTERVAL_SEC]
    [--conform-action=CONFORM_ACTION] [--description=DESCRIPTION]
    [--enforce-on-key=ENFORCE_ON_KEY]
    [--enforce-on-key-configs=[[all],[ip],[xff-ip],
      [http-cookie=HTTP_COOKIE],[http-header=HTTP_HEADER],[http-path],[sni],
      [region-code],
      [tls-ja3-fingerprint],[user-ip],[tls-ja4-fingerprint]],[...]]
    [--enforce-on-key-name=ENFORCE_ON_KEY_NAME]
    [--exceed-action=EXCEED_ACTION]
    [--exceed-redirect-target=EXCEED_REDIRECT_TARGET]
    [--exceed-redirect-type=EXCEED_REDIRECT_TYPE] [--[no-]preview]
    [--rate-limit-threshold-count=RATE_LIMIT_THRESHOLD_COUNT]
    [--rate-limit-threshold-interval-sec=RATE_LIMIT_THRESHOLD_INTERVAL_SEC]
    [--recaptcha-action-site-keys=[SITE_KEY,...]]
    [--recaptcha-session-site-keys=[SITE_KEY,...]]
    [--redirect-target=REDIRECT_TARGET] [--redirect-type=REDIRECT_TYPE]
    [--region=REGION]
    [--request-headers-to-add=[REQUEST_HEADERS_TO_ADD,...]]
    [--security-policy=SECURITY_POLICY]
    [--expression=EXPRESSION --network-dest-ip-ranges=[DEST_IP_RANGE,...]
      --network-dest-ports=[DEST_PORT,...]
      --network-ip-protocols=[IP_PROTOCOL,...]
      --network-src-asns=[SRC_ASN,...]
      --network-src-ip-ranges=[SRC_IP_RANGE,...]
      --network-src-ports=[SRC_PORT,...]
      --network-src-region-codes=[SRC_REGION_CODE,...]
      --network-user-defined-fields=[NAME;VALUE:VALUE:...,...]
      --src-ip-ranges=[SRC_IP_RANGE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PRIORITY
   The priority of the rule to update. Rules are evaluated in order from
   highest priority to lowest priority where 0 is the highest priority and
   2147483647 is the lowest priority.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--action` | one of: allow Allows the request from HTTP(S) Load Balancing |  | The action to take if the request matches the match condition. ACTION must be one of: allow Allows the request from HTTP(S) Load Balancing. deny Denies the request from TCP/SSL Proxy and Network Load Balancing. deny-403 Denies the request from HTTP(S) Load Balancing, with an HTTP response status code of 403. deny-404 Denies the request from HTTP(S) Load Balancing, with an HTTP response status code of 404. deny-502 Denies the request from HTTP(S) Load Balancing, with an HTTP response status code of 502. rate-based-ban Enforces rate-based ban action from HTTP(S) Load Balancing, based on rate limit options. redirect Redirects the request from HTTP(S) Load Balancing, based on redirect options. redirect-to-recaptcha (DEPRECATED) Redirects the request from HTTP(S) Load Balancing, for reCAPTCHA Enterprise assessment. This flag choice is deprecated. Use --action=redirect and --redirect-type=google-recaptcha instead. throttle Enforces throttle action from HTTP(S) Load Balancing, based on rate limit options. |
| `--ban-duration-sec` | BAN_DURATION_SEC |  | Can only be specified if the action for the rule is rate-based-ban. If specified, determines the time (in seconds) the traffic will continue to be banned by the rate limit after the rate falls below the threshold. |
| `--ban-threshold-count` | BAN_THRESHOLD_COUNT |  | Number of HTTP(S) requests for calculating the threshold for banning requests. Can only be specified if the action for the rule is rate-based-ban. If specified, the key will be banned for the configured BAN_DURATION_SEC when the number of requests that exceed the RATE_LIMIT_THRESHOLD_COUNT also exceed this BAN_THRESHOLD_COUNT. |
| `--ban-threshold-interval-sec` | BAN_THRESHOLD_INTERVAL_SEC |  | Interval over which the threshold for banning requests is computed. Can only be specified if the action for the rule is rate-based-ban. If specified, the key will be banned for the configured BAN_DURATION_SEC when the number of requests that exceed the RATE_LIMIT_THRESHOLD_COUNT also exceed this BAN_THRESHOLD_COUNT. |
| `--conform-action` | CONFORM_ACTION |  | Action to take when requests are under the given threshold. When requests are throttled, this is also the action for all requests which are not dropped. CONFORM_ACTION must be (only one value is supported): allow. |
| `--description` | DESCRIPTION |  | An optional, textual description for the rule. |
| `--enforce-on-key` | one of: ip, all, http-header, xff-ip, http-cookie, http-path, sni, region-code, tls-ja3-fingerprint, user-ip, tls-ja4-fingerprint |  | Different key types available to enforce the rate limit threshold limit on: * ip: each client IP address has this limit enforced separately * all: a single limit is applied to all requests matching this rule * http-header: key type takes the value of the HTTP header configured in enforce-on-key-name as the key value * xff-ip: takes the original IP address specified in the X-Forwarded-For header as the key * http-cookie: key type takes the value of the HTTP cookie configured in enforce-on-key-name as the key value * http-path: key type takes the value of the URL path in the request * sni: key type takes the value of the server name indication from the TLS session of the HTTPS request * region-code: key type takes the value of the region code from which the request originates * tls-ja3-fingerprint: key type takes the value of JA3 TLS/SSL fingerprint if the client connects using HTTPS, HTTP/2 or HTTP/3 * user-ip: key type takes the IP address of the originating client, which is resolved based on user-ip-request-headers configured with the security policy * tls-ja4-fingerprint: key type takes the value of JA4 TLS/SSL fingerprint if the client connects using HTTPS, HTTP/2 or HTTP/3 ENFORCE_ON_KEY must be one of: ip, all, http-header, xff-ip, http-cookie, http-path, sni, region-code, tls-ja3-fingerprint, user-ip, tls-ja4-fingerprint. |
| `--enforce-on-key-configs` | [[all],[ip],[xff-ip],[http-cookie=HTTP_COOKIE],[http-header=HTTP_HEADER],[http-path],[sni],[region-code],[tls-ja3-fingerprint],[user-ip],[tls-ja4-fingerprint]],[...] |  | Specify up to 3 key type/name pairs to rate limit. Valid key types are: * ip: each client IP address has this limit enforced separately * all: a single limit is applied to all requests matching this rule * http-header: key type takes the value of the HTTP header configured in enforce-on-key-name as the key value * xff-ip: takes the original IP address specified in the X-Forwarded-For header as the key * http-cookie: key type takes the value of the HTTP cookie configured in enforce-on-key-name as the key value * http-path: key type takes the value of the URL path in the request * sni: key type takes the value of the server name indication from the TLS session of the HTTPS request * region-code: key type takes the value of the region code from which the request originates * tls-ja3-fingerprint: key type takes the value of JA3 TLS/SSL fingerprint if the client connects using HTTPS, HTTP/2 or HTTP/3 * user-ip: key type takes the IP address of the originating client, which is resolved based on user-ip-request-headers configured with the security policy * tls-ja4-fingerprint: key type takes the value of JA4 TLS/SSL fingerprint if the client connects using HTTPS, HTTP/2 or HTTP/3 Key names are only applicable to the following key types: * http-header: The name of the HTTP header whose value is taken as the key value. * http-cookie: The name of the HTTP cookie whose value is taken as the key value. |
| `--enforce-on-key-name` | ENFORCE_ON_KEY_NAME |  | Determines the key name for the rate limit key. Applicable only for the following rate limit key types: * http-header: The name of the HTTP header whose value is taken as the key value. * http-cookie: The name of the HTTP cookie whose value is taken as the key value. |
| `--exceed-action` | one of: deny-403, deny-404, deny-429, deny-502, deny, redirect |  | Action to take when requests are above the given threshold. When a request is denied, return the specified HTTP response code. When a request is redirected, use the redirect options based on --exceed-redirect-type and --exceed-redirect-target below. EXCEED_ACTION must be one of: deny-403, deny-404, deny-429, deny-502, deny, redirect. |
| `--exceed-redirect-target` | EXCEED_REDIRECT_TARGET |  | URL target for the redirect action that is configured as the exceed action when the redirect type is external-302. |
| `--exceed-redirect-type` | one of: google-recaptcha, external-302 |  | Type for the redirect action that is configured as the exceed action. EXCEED_REDIRECT_TYPE must be one of: google-recaptcha, external-302. |
| `--[no-]preview` |  |  | If specified, the action will not be enforced. Use --preview to enable and --no-preview to disable. |
| `--rate-limit-threshold-count` | RATE_LIMIT_THRESHOLD_COUNT |  | Number of HTTP(S) requests for calculating the threshold for rate limiting requests. |
| `--rate-limit-threshold-interval-sec` | RATE_LIMIT_THRESHOLD_INTERVAL_SEC |  | Interval over which the threshold for rate limiting requests is computed. |
| `--recaptcha-action-site-keys` | [SITE_KEY,...] |  | A comma-separated list of site keys to be used during the validation of reCAPTCHA action-tokens. The provided site keys need to be created from the reCAPTCHA API under the same project where the security policy is created. |
| `--recaptcha-session-site-keys` | [SITE_KEY,...] |  | A comma-separated list of site keys to be used during the validation of reCAPTCHA session-tokens. The provided site keys need to be created from the reCAPTCHA API under the same project where the security policy is created. |
| `--redirect-target` | REDIRECT_TARGET |  | URL target for the redirect action. Must be specified if the redirect type is external-302. Cannot be specified if the redirect type is google-recaptcha. |
| `--redirect-type` | one of: google-recaptcha, external-302 |  | Type for the redirect action. Default to external-302 if unspecified while --redirect-target is given. REDIRECT_TYPE must be one of: google-recaptcha, external-302. |
| `--region` | REGION |  | Region of the security policy to update. If not specified, you might be prompted to select a region (interactive mode only). A list of regions can be fetched by running: $ gcloud compute regions list Overrides the default compute/region property value for this command invocation. |
| `--request-headers-to-add` | [REQUEST_HEADERS_TO_ADD,...] |  | A comma-separated list of header names and header values to add to requests that match this rule. |
| `--security-policy` | SECURITY_POLICY |  | The security policy that this rule belongs to. |


**Examples:**
```bash
To update the description and IP ranges of a rule at priority 1000, run:

    $ gcloud compute security-policies rules update 1000 \
        --security-policy=my-policy --description="block 1.2.3.4/32" \
        --src-ip-ranges=1.2.3.4/32
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/security-policies/rules/update)

---
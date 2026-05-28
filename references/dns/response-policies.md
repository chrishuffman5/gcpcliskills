# gcloud dns response-policies

manage your Cloud DNS response policy

### `gcloud dns response-policies create`

Creates a new Cloud DNS response policy

This command creates a new Cloud DNS response policy.

**Synopsis:**
```
gcloud dns response-policies create RESPONSE_POLICIES
    --description=DESCRIPTION [--gkeclusters=[GKECLUSTERS,...]]
    [--location=LOCATION] [--networks=[NETWORKS,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Response policy resource - The response policy to create. This represents
a Cloud resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument response_policies on the command line with a
   fully specified name;
 * set the property core/project.

This must be specified.

  RESPONSE_POLICIES
     ID of the response_policy or fully qualified identifier for the
     response_policy.

     To set the response-policy attribute:
     + provide the argument response_policies on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | A description of the response policy. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--gkeclusters` | [GKECLUSTERS,...] |  | The comma-separated list of GKE cluster names to associate with the response policy. |
| `--location` | LOCATION |  | Specifies the desired service location the request is sent to. Defaults to Cloud DNS global service. Use --location=global if you want to target the global service. |
| `--networks` | [NETWORKS,...] |  | The comma-separated list of network names to associate with the response policy. |


**Examples:**
```bash
To create a new response policy with minimal arguments, run:

    $ gcloud dns response-policies create myresponsepolicy \
        --description='My new response policy.' --networks=''

To create a new response policy with all optional arguments, run:

    $ gcloud dns response-policies create myresponsepolicy \
        --description='My new response policy.' \
        --networks=network1,network2

To create a new zonal response policy scoped to a GKE cluster in        us-central1-a, run (alpha/beta):

    $ gcloud dns response-policies create beta myresponsepolicy \
        --description='My new response
    policy.' --gkeclusters=cluster1 --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/response-policies/create)

---
### `gcloud dns response-policies delete`

Deletes a Cloud DNS response policy

This command deletes a new Cloud DNS response policy.

**Synopsis:**
```
gcloud dns response-policies delete RESPONSE_POLICIES [--location=LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Response policy resource - The response policy to describe. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument response_policies on the command line with a
   fully specified name;
 * set the property core/project.

This must be specified.

  RESPONSE_POLICIES
     ID of the response_policy or fully qualified identifier for the
     response_policy.

     To set the response-policy attribute:
     + provide the argument response_policies on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Specifies the desired service location the request is sent to. Defaults to Cloud DNS global service. Use --location=global if you want to target the global service. |


**Examples:**
```bash
To delete a global response policy (default), run:

    $ gcloud dns response-policies delete myresponsepolicy
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/response-policies/delete)

---
### `gcloud dns response-policies describe`

Describes a Cloud DNS response policy

This command describes details of a Cloud DNS response policy.

**Synopsis:**
```
gcloud dns response-policies describe RESPONSE_POLICIES
    [--location=LOCATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Response policy resource - The response policy to describe. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument response_policies on the command line with a
   fully specified name;
 * set the property core/project.

This must be specified.

  RESPONSE_POLICIES
     ID of the response_policy or fully qualified identifier for the
     response_policy.

     To set the response-policy attribute:
     + provide the argument response_policies on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Specifies the desired service location the request is sent to. Defaults to Cloud DNS global service. Use --location=global if you want to target the global service. |


**Examples:**
```bash
To describe a global response policy (default), run:

    $ gcloud dns response-policies describe myresponsepolicy
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/response-policies/describe)

---
### `gcloud dns response-policies list`

Displays the list of all Cloud DNS response policies in a given project

**Synopsis:**
```
gcloud dns response-policies list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Specifies the desired service location the request is sent to. Defaults to Cloud DNS global service. Use --location=global if you want to target the global service. |


**Examples:**
```bash
To list response policies in Global Cloud DNS server (default), run:

    $ gcloud dns response-policies list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/response-policies/list)

---
### `gcloud dns response-policies update`

Updates a Cloud DNS response policy

This command updates a Cloud DNS response policy.

**Synopsis:**
```
gcloud dns response-policies update RESPONSE_POLICIES
    [--description=DESCRIPTION] [--gkeclusters=[GKECLUSTERS,...]]
    [--location=LOCATION] [--networks=[NETWORKS,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Response policy resource - The response policy to update. This represents
a Cloud resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument response_policies on the command line with a
   fully specified name;
 * set the property core/project.

This must be specified.

  RESPONSE_POLICIES
     ID of the response_policy or fully qualified identifier for the
     response_policy.

     To set the response-policy attribute:
     + provide the argument response_policies on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | A description of the response policy. |
| `--gkeclusters` | [GKECLUSTERS,...] |  | The comma-separated list of GKE cluster names to associate with the response policy. |
| `--location` | LOCATION |  | Specifies the desired service location the request is sent to. Defaults to Cloud DNS global service. Use --location=global if you want to target the global service. |
| `--networks` | [NETWORKS,...] |  | The comma-separated list of network names to associate with the response policy. |


**Examples:**
```bash
To update a response policy with minimal arguments, run:

    $ gcloud dns response-policies update myresponsepolicy \
        --description='My updated response policy.' --networks=''

To update a response policy with all optional arguments, run:

    $ gcloud dns response-policies update myresponsepolicy \
        --description='My updated response policy.' \
        --networks=network1,network2

To update a new zonal response policy scoped to a GKE cluster in
us-central1-a, run:

    $ gcloud dns response-policies update myresponsepolicy \
        --description='My new response policy.' --gkeclusters=cluster1 \
        --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/response-policies/update)

---

## `gcloud dns response-policies rules` — manage your Cloud DNS response policy rules
### `gcloud dns response-policies rules create`

Creates a new Cloud DNS response policy rule

**Synopsis:**
```
gcloud dns response-policies rules create
    (RESPONSE_POLICY_RULE : --response-policy=RESPONSE_POLICY)
    --dns-name=DNS_NAME [--behavior=BEHAVIOR]
    [--local-data=[LOCAL_DATA,...]] [--location=LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Response policy rule resource - The response policy rule to create. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument response_policy_rule on the command line with a
   fully specified name;
 * set the property core/project.

This must be specified.

  RESPONSE_POLICY_RULE
     ID of the response_policy_rule or fully qualified identifier for the
     response_policy_rule.

     To set the response-policy-rule attribute:
     + provide the argument response_policy_rule on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --response-policy=RESPONSE_POLICY
     The Cloud DNS response policy name response_policy_rule.

     To set the response-policy attribute:
     + provide the argument response_policy_rule on the command line
       with a fully specified name;
     + provide the argument --response-policy on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--dns-name` | DNS_NAME |  | DNS name (wildcard or exact) to apply this rule to. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--behavior` | one of: behaviorUnspecified, bypassResponsePolicy |  | The response policy rule query behavior. BEHAVIOR must be one of: behaviorUnspecified, bypassResponsePolicy. |
| `--local-data` | [LOCAL_DATA,...] |  | All resource record sets for this selector, one per resource record type. The name must match the dns_name. This is a repeated argument that can be specified multiple times to specify multiple local data rrsets. (e.g. --local-data=name="zone.com.",type="A",ttl=21600,rrdata="1.2.3.4 " --local-data=name="www.zone.com.",type="CNAME",ttl=21600,rrdata="1.2.3.4\|5.6.7.8") name The DnsName of a resource record set. type Type of all resource records in this set. For example, A, AAAA, SOA, MX, NS, TXT ... ttl Number of seconds that this ResourceRecordSet can be cached by resolvers. rrdatas The list of datas for this record, split by "\|". |
| `--location` | LOCATION |  | Specifies the desired service location the request is sent to. Defaults to Cloud DNS global service. Use --location=global if you want to target the global service. |


**Examples:**
```bash
To create a new response policy rule with local data rrsets, run:

    $ gcloud dns response-policies rules create myresponsepolicyrule \
        --response-policy="myresponsepolicy" \
        --dns-name="www.zone.com." \
        --local-data=name=www.zone.com.,type=CNAME,ttl=21600,\
    rrdatas=zone.com.

To create a new response policy rule with behavior, run:

    $ gcloud dns response-policies rules create myresponsepolicyrule \
        --response-policy="myresponsepolicy" \
        --dns-name="www.zone.com." --behavior=bypassResponsePolicy

To create a new response policy rule with behavior in a zonal response
policy in us-east1-a, run:

    $ gcloud dns response-policies rules create myresponsepolicyrule \
        --response-policy="myresponsepolicy" \
        --dns-name="www.zone.com." --behavior=bypassResponsePolicy \
        --location=us-east1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/response-policies/rules/create)

---
### `gcloud dns response-policies rules delete`

Deletes a Cloud DNS response policy rule

**Synopsis:**
```
gcloud dns response-policies rules delete
    (RESPONSE_POLICY_RULE : --response-policy=RESPONSE_POLICY)
    [--location=LOCATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Response policy rule resource - The response policy rule to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument response_policy_rule on the command line with a
   fully specified name;
 * set the property core/project.

This must be specified.

  RESPONSE_POLICY_RULE
     ID of the response_policy_rule or fully qualified identifier for the
     response_policy_rule.

     To set the response-policy-rule attribute:
     + provide the argument response_policy_rule on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --response-policy=RESPONSE_POLICY
     The Cloud DNS response policy name response_policy_rule.

     To set the response-policy attribute:
     + provide the argument response_policy_rule on the command line
       with a fully specified name;
     + provide the argument --response-policy on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Specifies the desired service location the request is sent to. Defaults to Cloud DNS global service. Use --location=global if you want to target the global service. |


**Examples:**
```bash
To delete a response policy rule, run:

    $ gcloud dns response-policies rules delete \
        --response-policy=myresponsepolicy rulename
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/response-policies/rules/delete)

---
### `gcloud dns response-policies rules describe`

Shows details about a Cloud DNS response policy rule

**Synopsis:**
```
gcloud dns response-policies rules describe
    (RESPONSE_POLICY_RULE : --response-policy=RESPONSE_POLICY)
    [--location=LOCATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Response policy rule resource - The response policy rule to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument response_policy_rule on the command line with a
   fully specified name;
 * set the property core/project.

This must be specified.

  RESPONSE_POLICY_RULE
     ID of the response_policy_rule or fully qualified identifier for the
     response_policy_rule.

     To set the response-policy-rule attribute:
     + provide the argument response_policy_rule on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --response-policy=RESPONSE_POLICY
     The Cloud DNS response policy name response_policy_rule.

     To set the response-policy attribute:
     + provide the argument response_policy_rule on the command line
       with a fully specified name;
     + provide the argument --response-policy on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Specifies the desired service location the request is sent to. Defaults to Cloud DNS global service. Use --location=global if you want to target the global service. |


**Examples:**
```bash
To show details about a response policy rule, run:

    $ gcloud dns response-policies rules describe \
        --response-policy=myresponsepolicy rulename
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/response-policies/rules/describe)

---
### `gcloud dns response-policies rules list`

Displays the list of all a Cloud DNS response policy rules

**Synopsis:**
```
gcloud dns response-policies rules list RESPONSE_POLICIES
    [--location=LOCATION] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Response policy resource - The response policy to list. This represents a
Cloud resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument response_policies on the command line with a
   fully specified name;
 * set the property core/project.

This must be specified.

  RESPONSE_POLICIES
     ID of the response_policy or fully qualified identifier for the
     response_policy.

     To set the response-policy attribute:
     + provide the argument response_policies on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Specifies the desired service location the request is sent to. Defaults to Cloud DNS global service. Use --location=global if you want to target the global service. |


**Examples:**
```bash
To list response policie rules in Global Cloud DNS server (default), run:

    $ gcloud dns response-policies rules list myresponsepolicy
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/response-policies/rules/list)

---
### `gcloud dns response-policies rules update`

Updates a new Cloud DNS response policy rule

This command updates a new Cloud DNS response policy rule.

**Synopsis:**
```
gcloud dns response-policies rules update
    (RESPONSE_POLICY_RULE : --response-policy=RESPONSE_POLICY)
    [--behavior=BEHAVIOR] [--dns-name=DNS_NAME]
    [--local-data=[LOCAL_DATA,...]] [--location=LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Response policy rule resource - The response policy rule to update. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument response_policy_rule on the command line with a
   fully specified name;
 * set the property core/project.

This must be specified.

  RESPONSE_POLICY_RULE
     ID of the response_policy_rule or fully qualified identifier for the
     response_policy_rule.

     To set the response-policy-rule attribute:
     + provide the argument response_policy_rule on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --response-policy=RESPONSE_POLICY
     The Cloud DNS response policy name response_policy_rule.

     To set the response-policy attribute:
     + provide the argument response_policy_rule on the command line
       with a fully specified name;
     + provide the argument --response-policy on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--behavior` | one of: behaviorUnspecified, bypassResponsePolicy |  | The response policy rule query behavior. BEHAVIOR must be one of: behaviorUnspecified, bypassResponsePolicy. |
| `--dns-name` | DNS_NAME |  | DNS name (wildcard or exact) to apply this rule to. |
| `--local-data` | [LOCAL_DATA,...] |  | All resource record sets for this selector, one per resource record type. The name must match the dns_name. This is a repeated argument that can be specified multiple times to specify multiple local data rrsets. (e.g. --local-data=name="zone.com.",type="A",ttl=21600,rrdata="1.2.3.4 " --local-data=name="www.zone.com.",type="CNAME",ttl=21600,rrdata="1.2.3.4\|5.6.7.8") name The DnsName of a resource record set. type Type of all resource records in this set. For example, A, AAAA, SOA, MX, NS, TXT ... ttl Number of seconds that this ResourceRecordSet can be cached by resolvers. rrdatas The list of datas for this record, split by "\|". |
| `--location` | LOCATION |  | Specifies the desired service location the request is sent to. Defaults to Cloud DNS global service. Use --location=global if you want to target the global service. |


**Examples:**
```bash
To update a new response policy rule with DNS name, run:

    $ gcloud dns response-policies rules update myresponsepolicyrule \
        --response-policy="myresponsepolicy" \
        --dns-name="www.newzone.com." # pylint: disable=line-too-long

To update a new response policy rule with local data rrsets, run:

    $ gcloud dns response-policies rules update myresponsepolicyrule \
        --response-policy="myresponsepolicy" \
        --local-data=name=www.zone.com.,type=A,ttl=21600,rrdatas=1.2.3.4

To update a new response policy rule with behavior, run:

    $ gcloud dns response-policies rules update myresponsepolicyrule \
        --response-policy="myresponsepolicy" \
        --behavior=bypassResponsePolicy
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/response-policies/rules/update)

---
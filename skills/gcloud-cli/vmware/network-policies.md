# gcloud vmware network-policies

manage VMware Engine network policies in Google Cloud VMware Engine

### `gcloud vmware network-policies create`

Create a VMware Engine network policy

Create a VMware Engine network policy. Only one network policy applies to a
VMware Engine network per region. Check the progress of a network policy
creation using gcloud vmware network-policies list.

**Synopsis:**
```
gcloud vmware network-policies create
    (NETWORK_POLICY : --location=LOCATION)
    --edge-services-cidr=EDGE_SERVICES_CIDR
    --vmware-engine-network=VMWARE_ENGINE_NETWORK [--async]
    [--description=DESCRIPTION] [--external-ip-access] [--internet-access]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VMware Engine Network Policy resource - network_policy. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument network_policy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NETWORK_POLICY
     ID of the VMware Engine Network Policy or fully qualified identifier
     for the VMware Engine Network Policy.

     To set the network-policy attribute:
     + provide the argument network_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The resource name of the location.

     To set the location attribute:
     + provide the argument network_policy on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--edge-services-cidr` | EDGE_SERVICES_CIDR |  | IP address range to use for internet access and external IP access gateways, in CIDR notation. An RFC 1918 CIDR block with a "/26" prefix is required. |
| `--vmware-engine-network` | VMWARE_ENGINE_NETWORK |  | Resource ID of the VMware Engine network to attach the new policy to. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--description` | DESCRIPTION |  | User-provided description of the network policy. |
| `--external-ip-access` |  |  | Enable or disable network service that allows external IP addresses to be assigned to VMware workloads. To enable this service, internet-access must also be enabled. Use --no-external-ip-access to disable. If the flag is not provided, access to VMware workloads through external IP addresses is disabled. |
| `--internet-access` |  |  | Enable or disable network service that allows VMware workloads to access the internet. Use --no-internet-access to disable. If the flag is not provided, internet access is disabled. |


**Examples:**
```bash
To create a network policy called my-network-policy which connects to the
VMware Engine network my-vmware-engine-network using the edge services
address range 192.168.0.0/26 with the internet access service enabled and
the external IP access service disabled, run:

    $ gcloud vmware network-policies create my-network-policy \
        --location=us-west2 --project=my-project \
        --vmware-engine-network=my-vmware-engine-network \
        --edge-services-cidr=192.168.0.0/26 --internet-access \
        --no-external-ip-access

Or:

    $ gcloud vmware network-policies create my-network-policy \
        --vmware-engine-network=my-vmware-engine-network \
        --edge-services-cidr=192.168.0.0/26 --internet-access

In the second example, the project and the location are taken from gcloud
properties core/project and compute/region respectively. If the
--external-ip-access flag is not specified, it is taken as False.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/network-policies/create)

---
### `gcloud vmware network-policies delete`

Delete a VMware Engine network policy

Delete a VMware Engine network policy.

**Synopsis:**
```
gcloud vmware network-policies delete
    (NETWORK_POLICY : --location=LOCATION) [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VMware Engine Network Policy resource - network_policy. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument network_policy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NETWORK_POLICY
     ID of the VMware Engine Network Policy or fully qualified identifier
     for the VMware Engine Network Policy.

     To set the network-policy attribute:
     + provide the argument network_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The resource name of the location.

     To set the location attribute:
     + provide the argument network_policy on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |


**Examples:**
```bash
To delete a network policy called my-network-policy in project my-project
and region us-west2, run:

    $ gcloud vmware network-policies delete my-network-policy \
        --location=us-west2 --project=my-project

Or:

    $ gcloud vmware network-policies delete my-network-policy

In the second example, the project and the location are taken from gcloud
properties core/project and compute/region respectively.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/network-policies/delete)

---
### `gcloud vmware network-policies describe`

Describe a VMware Engine network policy

Describe a VMware Engine network policy.

**Synopsis:**
```
gcloud vmware network-policies describe
    (NETWORK_POLICY : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VMware Engine Network Policy resource - network_policy. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument network_policy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NETWORK_POLICY
     ID of the VMware Engine Network Policy or fully qualified identifier
     for the VMware Engine Network Policy.

     To set the network-policy attribute:
     + provide the argument network_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The resource name of the location.

     To set the location attribute:
     + provide the argument network_policy on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/region.
```

**Examples:**
```bash
To get a description of a network policy called my-network-policy in
project my-project and region us-west2, run:

    $ gcloud vmware network-policies describe my-network-policy \
        --location=us-west2 --project=my-project

Or:

    $ gcloud vmware network-policies describe my-network-policy

In the second example, the project and the location are taken from gcloud
properties core/project and compute/region respectively.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/network-policies/describe)

---
### `gcloud vmware network-policies list`

List VMware Engine network policies

List VMware Engine network policies.

**Synopsis:**
```
gcloud vmware network-policies list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property compute/region. |


**Examples:**
```bash
To list network policies in your project in the region us-west2 sorted from
oldest to newest, run:

    $ gcloud vmware network-policies list --location=us-west2 \
        --project=my-project --sort-by=~create_time

Or:

    $ gcloud vmware network-policies list --sort-by=~create_time

In the second example, the project and the location are taken from gcloud
properties core/project and compute/region respectively.

To list network policies in your project from all regions, run:

    $ gcloud vmware network-policies list --location=- \
        --project=my-project

Or:

    $ gcloud vmware network-policies list --location=-

In the last example, the project is taken from gcloud properties
core/project.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/network-policies/list)

---
### `gcloud vmware network-policies update`

Update a VMware Engine network policy

Update a VMware Engine network policy.

**Synopsis:**
```
gcloud vmware network-policies update
    (NETWORK_POLICY : --location=LOCATION) [--async]
    [--description=DESCRIPTION] [--edge-services-cidr=EDGE_SERVICES_CIDR]
    [--external-ip-access] [--internet-access] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VMware Engine Network Policy resource - network_policy. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument network_policy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NETWORK_POLICY
     ID of the VMware Engine Network Policy or fully qualified identifier
     for the VMware Engine Network Policy.

     To set the network-policy attribute:
     + provide the argument network_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The resource name of the location.

     To set the location attribute:
     + provide the argument network_policy on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--description` | DESCRIPTION |  | Updated description for the network policy. |
| `--edge-services-cidr` | EDGE_SERVICES_CIDR |  | Updated IP address range to use for internet access and external IP access gateways, in CIDR notation. |
| `--external-ip-access` |  |  | Enable or disable network service that allows external IP addresses to be assigned to VMware workloads. To enable this service, internet-access must also be enabled. Use --no-external-ip-access to disable. |
| `--internet-access` |  |  | Enable or disable network service that allows VMware workloads to access the internet. Use --no-internet-access to disable. |


**Examples:**
```bash
To update a network policy named my-network-policy so that it disables the
external IP access service, run:

    $ gcloud vmware network-policies update my-network-policy \
        --location=us-west2 --project=my-project --no-external-ip-access

Or:

    $ gcloud vmware network-policies update my-network-policy \
        --no-external-ip-access

In the second example, the project and the location are taken from gcloud
properties core/project and compute/regions respectively.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/network-policies/update)

---

## `gcloud vmware network-policies external-access-rules` — manage VMware Engine external access firewall rules in Google Cloud VMware Engine
### `gcloud vmware network-policies external-access-rules create`

Create a VMware Engine external access firewall rule

Create a VMware Engine external access firewall rule. Check the progress of
a VMware Engine external access firewall rule creation using gcloud vmware
network-policies external-access-rules list.

**Synopsis:**
```
gcloud vmware network-policies external-access-rules create
    (EXTERNAL_ACCESS_RULE
      : --location=LOCATION --network-policy=NETWORK_POLICY)
    --destination-ranges=DESTINATION_IP_RANGES,[...]
    --ip-protocol=IP_PROTOCOL --priority=PRIORITY
    --source-ranges=SOURCE_IP_RANGES,[...]
    [--action=ACTION; default="ALLOW"] [--async]
    [--description=DESCRIPTION]
    [--destination-ports=DESTINATION_PORTS,[...]]
    [--source-ports=SOURCE_PORTS,[...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VMware Engine External Access Rule resource - external_access_rule. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument external_access_rule on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  EXTERNAL_ACCESS_RULE
     ID of the VMware Engine External Access Rule or fully qualified
     identifier for the VMware Engine External Access Rule.

     To set the external-access-rule attribute:
     + provide the argument external_access_rule on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The resource name of the location.

     To set the location attribute:
     + provide the argument external_access_rule on the command line
       with a fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/region.

  --network-policy=NETWORK_POLICY
     VMware Engine network policy

     To set the network-policy attribute:
     + provide the argument external_access_rule on the command line
       with a fully specified name;
     + provide the argument --network-policy on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination-ranges` | DESTINATION_IP_RANGES,[...] |  | A list of destination IP addresses that the rule applies to. Each entry in the list can be an ExternalAddress resource name or 0.0.0.0/0. When the value is set to 0.0.0.0/0, all IP addresses are allowed. |
| `--ip-protocol` | one of: TCP, UDP, ICMP |  | Internet protocol covered by the rule. Valid values are TCP, UDP, and ICMP. IP_PROTOCOL must be one of: TCP, UDP, ICMP. |
| `--priority` | PRIORITY |  | Priority of this external access rule. Valid values are numbers between 100 and 4096, with 100 being the highest priority. Firewall rules are processed from highest to lowest priority. |
| `--source-ranges` | SOURCE_IP_RANGES,[...] |  | A list of source IP addresses that the rule applies to. Each entry in the list can be a CIDR notation or a single IP address. When the value is set to 0.0.0.0/0, all IP addresses are allowed. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--action` | one of: ALLOW, DENY | ALLOW | Whether the firewall rule allows or denies traffic based on a successful rule match. By default, the action is ALLOW. ACTION must be one of: ALLOW, DENY. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--description` | DESCRIPTION |  | User-provided description of the external access rule. |
| `--destination-ports` | DESTINATION_PORTS,[...] |  | List of allowed destination ports. Each entry must be either an integer or a range. |
| `--source-ports` | SOURCE_PORTS,[...] |  | List of allowed source ports. Each entry must be either an integer or a range. |


**Examples:**
```bash
To create an external access firewall rule called my-external-access-rule
associated with the network policy my-network-policy in the us-west2
region, run:

    $ gcloud vmware network-policies external-access-rules create \
        my-external-access-rule --network-policy=my-network-policy \
        --priority=1000 --ip-protocol=TCP \
        --source-ranges=34.148.30.114/32 \
        --destination-ranges=projects/sample-project/locations/\
    us-west2-a/privateClouds/my-private-cloud/externalAddresses/\
    my-external-address --source-ports=22,10000-11000 \
        --destination-ports=22 --action=ALLOW --location=us-west2 \
        --project=sample-project

Or:

    $ gcloud vmware network-policies external-access-rules create \
        my-external-access-rule --network-policy=my-network-policy \
        --priority=1000 --ip-protocol=TCP \
        --source-ranges=34.148.30.114/32 \
        --destination-ranges=projects/sample-project/locations/\
    us-west2-a/privateClouds/my-private-cloud/externalAddresses/\
    my-external-address --source-ports=22,10000-11000 \
        --destination-ports=22

In the second example, the project and the location are taken from gcloud
properties core/project and compute/region respectively. The --action field
also isn't specified, so its value defaults to ALLOW.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/network-policies/external-access-rules/create)

---
### `gcloud vmware network-policies external-access-rules delete`

Delete a VMware Engine external access rule

Delete a VMware Engine external access firewall rule.

**Synopsis:**
```
gcloud vmware network-policies external-access-rules delete
    (EXTERNAL_ACCESS_RULE
      : --location=LOCATION --network-policy=NETWORK_POLICY) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VMware Engine External Access Rule resource - external_access_rule. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument external_access_rule on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  EXTERNAL_ACCESS_RULE
     ID of the VMware Engine External Access Rule or fully qualified
     identifier for the VMware Engine External Access Rule.

     To set the external-access-rule attribute:
     + provide the argument external_access_rule on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The resource name of the location.

     To set the location attribute:
     + provide the argument external_access_rule on the command line
       with a fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/region.

  --network-policy=NETWORK_POLICY
     VMware Engine network policy

     To set the network-policy attribute:
     + provide the argument external_access_rule on the command line
       with a fully specified name;
     + provide the argument --network-policy on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |


**Examples:**
```bash
To delete an external access firewall rule called my-external-access-rule
in project my-project and region us-west2 associated with network policy
my-network-policy, run:

    $ gcloud vmware network-policies external-access-rules delete \
        my-external-access-rule --location=us-west2 \
        --project=my-project --network-policy=my-network-policy

Or:

    $ gcloud vmware network-policies external-access-rules delete \
        my-external-access-rule --network-policy=my-network-policy

In the second example, the project and the location are taken from gcloud
properties core/project and compute/region respectively.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/network-policies/external-access-rules/delete)

---
### `gcloud vmware network-policies external-access-rules describe`

Describe a VMware Engine external access rule

Describe a VMware Engine external access firewall rule.

**Synopsis:**
```
gcloud vmware network-policies external-access-rules describe
    (EXTERNAL_ACCESS_RULE
      : --location=LOCATION --network-policy=NETWORK_POLICY)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VMware Engine External Access Rule resource - external_access_rule. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument external_access_rule on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  EXTERNAL_ACCESS_RULE
     ID of the VMware Engine External Access Rule or fully qualified
     identifier for the VMware Engine External Access Rule.

     To set the external-access-rule attribute:
     + provide the argument external_access_rule on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The resource name of the location.

     To set the location attribute:
     + provide the argument external_access_rule on the command line
       with a fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/region.

  --network-policy=NETWORK_POLICY
     VMware Engine network policy

     To set the network-policy attribute:
     + provide the argument external_access_rule on the command line
       with a fully specified name;
     + provide the argument --network-policy on the command line.
```

**Examples:**
```bash
To get a description of an external access firewall rule called
my-external-access-rule in project my-project and region us-west2
associated with network policy my-network-policy, run:

    $ gcloud vmware network-policies external-access-rules describe \
        my-external-access-rule --network-policy=my-network-policy \
        --location=us-west2 --project=my-project

Or:

    $ gcloud vmware network-policies external-access-rules describe \
        my-external-access-rule --network-policy=my-network-policy

In the second example, the project and the location are taken from gcloud
properties core/project and compute/region respectively.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/network-policies/external-access-rules/describe)

---
### `gcloud vmware network-policies external-access-rules list`

List VMware Engine external access rules

List VMware Engine external access firewall rules.

**Synopsis:**
```
gcloud vmware network-policies external-access-rules list
    (--network-policy=NETWORK_POLICY : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--network-policy` | NETWORK_POLICY |  | _[This must be specified.]_ ID of the VMware Engine Network Policy or fully qualified identifier for the VMware Engine Network Policy. To set the network-policy attribute: + provide the argument --network-policy on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The resource name of the location. To set the location attribute: + provide the argument --network-policy on the command line with a fully specified name; + provide the argument --location on the command line; + set the property compute/region. |


**Examples:**
```bash
To list external access firewall rules in your project in the region
us-west2 associated with network policy my-network-policy, sorted from
oldest to newest, run:

    $ gcloud vmware network-policies external-access-rules list \
        --location=us-west2 --project=my-project \
        --network-policy=my-network-policy --sort-by=~create_time

Or:

    $ gcloud vmware network-policies external-access-rules list \
        --sort-by=~create_time --network-policy=my-network-policy

In the second example, the project and the location are taken from gcloud
properties core/project and compute/region respectively.

To list custom set of fields of external access firewall rules in a
project, run:

    $ gcloud vmware network-policies external-access-rules list \
        --format="table(
            name.segment(-1):label=NAME,,
            priority,
            ipProtocol,
            sourceIpRanges.flatten(show='values'),
            sourcePorts.list(),
            destinationIpRanges.flatten(show='values'),
            destinationPorts.list(),
            action
        )"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/network-policies/external-access-rules/list)

---
### `gcloud vmware network-policies external-access-rules update`

Update a VMware Engine network policy

Update a VMware Engine external access firewall rule.

**Synopsis:**
```
gcloud vmware network-policies external-access-rules update
    (EXTERNAL_ACCESS_RULE
      : --location=LOCATION --network-policy=NETWORK_POLICY)
    [--action=ACTION] [--async] [--description=DESCRIPTION]
    [--destination-ports=DESTINATION_PORTS,[...]]
    [--destination-ranges=DESTINATION_IP_RANGES,[...]]
    [--ip-protocol=IP_PROTOCOL] [--priority=PRIORITY]
    [--source-ports=SOURCE_PORTS,[...]]
    [--source-ranges=SOURCE_IP_RANGES,[...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VMware Engine External Access Rule resource - external_access_rule. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument external_access_rule on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  EXTERNAL_ACCESS_RULE
     ID of the VMware Engine External Access Rule or fully qualified
     identifier for the VMware Engine External Access Rule.

     To set the external-access-rule attribute:
     + provide the argument external_access_rule on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The resource name of the location.

     To set the location attribute:
     + provide the argument external_access_rule on the command line
       with a fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/region.

  --network-policy=NETWORK_POLICY
     VMware Engine network policy

     To set the network-policy attribute:
     + provide the argument external_access_rule on the command line
       with a fully specified name;
     + provide the argument --network-policy on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--action` | one of: ALLOW, DENY |  | Whether the firewall rule allows or denies traffic based on a successful rule match. ACTION must be one of: ALLOW, DENY. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--description` | DESCRIPTION |  | User-provided description of the external access rule. |
| `--destination-ports` | DESTINATION_PORTS,[...] |  | List of allowed destination ports. Each entry must be either an integer or a range. |
| `--destination-ranges` | DESTINATION_IP_RANGES,[...] |  | A list of destination IP addresses that the rule applies to. Each entry in the list be an ExternalAddress resource name or 0.0.0.0/0. When the value is set to 0.0.0.0/0, all IP addresses are allowed. |
| `--ip-protocol` | one of: TCP, UDP, ICMP |  | Internet protocol covered by the rule. Valid values are TCP, UDP, and ICMP. IP_PROTOCOL must be one of: TCP, UDP, ICMP. |
| `--priority` | PRIORITY |  | Priority of this external access rule. Valid values are numbers between 100 and 4096, with 100 being the highest priority. Firewall rules are processed from highest to lowest priority. |
| `--source-ports` | SOURCE_PORTS,[...] |  | List of allowed source ports. Each entry must be either an integer or a range. |
| `--source-ranges` | SOURCE_IP_RANGES,[...] |  | A list of source IP addresses that the rule applies to. Each entry in the list can be a CIDR notation or a single IP address. When the value is set to 0.0.0.0/0, all IP addresses are allowed. |


**Examples:**
```bash
To update an external access firewall rule named my-external-access-rule so
that it denies the traffic for that rule, run:

    $ gcloud vmware network-policies external-access-rules update \
        my-external-access-rule --network-policy=my-network-policy \
        --action=DENY --location=us-west2 --project=my-project

Or:

    $ gcloud vmware network-policies external-access-rules update \
        my-external-access-rule --network-policy=my-network-policy \
        --action=DENY

In the second example, the project and the location are taken from gcloud
properties core/project and compute/regions respectively.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/network-policies/external-access-rules/update)

---
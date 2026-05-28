# gcloud network-connectivity policy-based-routes

manage Policy-based Routes

### `gcloud network-connectivity policy-based-routes create`

Create a new policy-based route

Create a new policy-based route with the given name.

**Synopsis:**
```
gcloud network-connectivity policy-based-routes create POLICY_BASED_ROUTE
    --network=NETWORK [--async] [--description=DESCRIPTION]
    [--destination-range=DESTINATION_RANGE] [--ip-protocol=IP_PROTOCOL]
    [--labels=[KEY=VALUE,...]] [--priority=PRIORITY]
    [--protocol-version=PROTOCOL_VERSION; default="IPV4"]
    [--source-range=SOURCE_RANGE]
    [--interconnect-attachment-region=INTERCONNECT_ATTACHMENT_REGION
      | --tags=[TAGS,...]]
    [--next-hop-ilb-ip=NEXT_HOP_ILB_IP
      | --next-hop-other-routes=NEXT_HOP_OTHER_ROUTES]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Policy based route resource - Name of the policy-based route to be
created. This represents a Cloud resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument policy_based_route on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  POLICY_BASED_ROUTE
     ID of the policy based route or fully qualified identifier for the
     policy based route.

     To set the policy_based_route attribute:
     + provide the argument policy_based_route on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--network` | NETWORK |  | Fully-qualified URL of the network that this route applies to. E.g. projects/my-project/global/networks/my-network |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Optional description of this resource. Provide this field when you create the resource. |
| `--destination-range` | DESTINATION_RANGE |  | Destination IP range of outgoing packets that this policy-based route applies to. |
| `--ip-protocol` | IP_PROTOCOL |  | IP protocol that this policy-based route applies to. Valid values are TCP, UDP, and ALL. Default is ALL. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--priority` | PRIORITY |  | Priority of this policy-based route. Priority is used to break ties in cases where there are more than one matching policy-based routes found. In cases where multiple policy-based routes are matched, the one with the lowest-numbered priority value wins. The default value is 1000. The priority value must be from 1 to 65535, inclusive. Note the priority of policy-based route is always higher than other types of route (e.g. static routes/advanced routes) |
| `--protocol-version` | one of: ipv4, ipv6, protocol-version-unspecified | IPV4 | Internet protocol versions that this policy-based route applies to. For this version, only IPV4 is supported. PROTOCOL_VERSION must be one of: ipv4, ipv6, protocol-version-unspecified. |
| `--source-range` | SOURCE_RANGE |  | Source IP range of outgoing packets that this policy-based route applies to. |


**Examples:**
```bash
To create a policy-based route with the name my-pbr to route all traffic in
default network to an internal load balancer with IP 10.0.0.1, run:

    $ gcloud network-connectivity policy-based-routes create my-pbr \
        --network="projects/my-project/global/networks/default" \
        --next-hop-ilb-ip=10.0.0.1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/policy-based-routes/create)

---
### `gcloud network-connectivity policy-based-routes delete`

Delete a policy-based route

Delete the specified policy-based route.

**Synopsis:**
```
gcloud network-connectivity policy-based-routes delete POLICY_BASED_ROUTE
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Policy based route resource - Name of the policy-based route to be
deleted. This represents a Cloud resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument policy_based_route on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  POLICY_BASED_ROUTE
     ID of the policy based route or fully qualified identifier for the
     policy based route.

     To set the policy_based_route attribute:
     + provide the argument policy_based_route on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a policy-based route named my-pbr, run:

    $ gcloud network-connectivity policy-based-routes delete my-pbr
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/policy-based-routes/delete)

---
### `gcloud network-connectivity policy-based-routes describe`

Describe a policy-based route

Retrieve and display details about a policy-based route.

**Synopsis:**
```
gcloud network-connectivity policy-based-routes describe POLICY_BASED_ROUTE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Policy based route resource - Name of the policy-based route to be
described. This represents a Cloud resource. (NOTE) Some attributes are
not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument policy_based_route on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  POLICY_BASED_ROUTE
     ID of the policy based route or fully qualified identifier for the
     policy based route.

     To set the policy_based_route attribute:
     + provide the argument policy_based_route on the command line.
```

**Examples:**
```bash
To display details about a policy-based route named my-pbr, run:

    $ gcloud network-connectivity policy-based-routes describe my-pbr
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/policy-based-routes/describe)

---
### `gcloud network-connectivity policy-based-routes list`

List policy-based routes

Retrieve and display a list of all policy-based routes in the specified
project.

**Synopsis:**
```
gcloud network-connectivity policy-based-routes list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To display details about a policy-based route named my-pbr, run:

    $ gcloud network-connectivity policy-based-routes list my-pbr
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/policy-based-routes/list)

---
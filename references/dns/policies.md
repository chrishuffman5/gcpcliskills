# gcloud dns policies

manage your Cloud DNS policies

### `gcloud dns policies create`

Creates a new Cloud DNS policy

This command creates a new Cloud DNS policy.

**Synopsis:**
```
gcloud dns policies create POLICY --description=DESCRIPTION
    --networks=[NETWORKS,...]
    [--alternative-name-servers=[NAME_SERVERS,...]]
    [--enable-dns64-all-queries] [--enable-inbound-forwarding]
    [--enable-logging]
    [--private-alternative-name-servers=[NAME_SERVERS,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Policy resource - The policy to create. This represents a Cloud resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument policy on the command line with a fully
   specified name;
 * set the property core/project.

This must be specified.

  POLICY
     ID of the policy or fully qualified identifier for the policy.

     To set the policy attribute:
     + provide the argument policy on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | A description of the policy. |
| `--networks` | [NETWORKS,...] |  | The comma separated list of network names to associate with the policy. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--alternative-name-servers` | [NAME_SERVERS,...] |  | List of alternative name servers to forward to. Non-RFC1918 addresses will forward to the target through the Internet.RFC1918 addresses will forward through the VPC. |
| `--enable-dns64-all-queries` |  |  | Specifies whether to allow networks bound to this policy to use DNS64 for IPv6-only VM instances. |
| `--enable-inbound-forwarding` |  |  | Specifies whether to allow networks bound to this policy to receive DNS queries sent by VMs or applications over VPN connections. Defaults to False. |
| `--enable-logging` |  |  | Specifies whether to enable query logging. Defaults to False. |
| `--private-alternative-name-servers` | [NAME_SERVERS,...] |  | List of alternative name servers to forward to. All addresses specified for this parameter will be reached through the VPC. |


**Examples:**
```bash
To create a new policy with minimal arguments, run:

    $ gcloud dns policies create mypolicy \
        --description='My new policy test policy 5' --networks=''

To create a new policy with all optional arguments, run:

    $ gcloud dns policies create mypolicy \
        --description='My new policy test policy 5' \
        --networks=network1,network2 \
        --alternative-name-servers=192.168.1.1,192.168.1.2 \
        --enable-inbound-forwarding --enable-logging \
        --enable-dns64-all-queries
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/policies/create)

---
### `gcloud dns policies delete`

Deletes a Cloud DNS policy

Deletes a Cloud DNS policy.

**Synopsis:**
```
gcloud dns policies delete POLICY [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Policy resource - The name of the policy you want to delete. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument policy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  POLICY
     ID of the policy or fully qualified identifier for the policy.

     To set the policy attribute:
     + provide the argument policy on the command line.
```

**Examples:**
```bash
To delete a policy, run:

    $ gcloud dns policies delete mypolicy
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/policies/delete)

---
### `gcloud dns policies describe`

Describes a Cloud DNS policy

Describes details of a Cloud DNS policy.

**Synopsis:**
```
gcloud dns policies describe POLICY [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Policy resource - The name of the policy you want to describe. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument policy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  POLICY
     ID of the policy or fully qualified identifier for the policy.

     To set the policy attribute:
     + provide the argument policy on the command line.
```

**Examples:**
```bash
To describe a policy, run:

    $ gcloud dns policies describe mypolicy
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/policies/describe)

---
### `gcloud dns policies list`

View the list of all your Cloud DNS policies

Displays the list of all Cloud DNS policies in a given project.

**Synopsis:**
```
gcloud dns policies list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To see the list of all policies, run:

    $ gcloud dns policies list

To see the list of first 10 policies, run:

    $ gcloud dns policies list --limit=10
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/policies/list)

---
### `gcloud dns policies update`

Update an existing Cloud DNS policy

Update an existing Cloud DNS policy.

**Synopsis:**
```
gcloud dns policies update POLICY
    [--alternative-name-servers=[NAME_SERVERS,...]]
    [--description=DESCRIPTION] [--[no-]enable-dns64-all-queries]
    [--enable-inbound-forwarding] [--enable-logging]
    [--networks=[NETWORKS,...]]
    [--private-alternative-name-servers=[NAME_SERVERS,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Policy resource - The policy to update. This represents a Cloud resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument policy on the command line with a fully
   specified name;
 * set the property core/project.

This must be specified.

  POLICY
     ID of the policy or fully qualified identifier for the policy.

     To set the policy attribute:
     + provide the argument policy on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--alternative-name-servers` | [NAME_SERVERS,...] |  | List of alternative name servers to forward to. Non-RFC1918 addresses will forward to the target through the Internet.RFC1918 addresses will forward through the VPC. |
| `--description` | DESCRIPTION |  | A description of the policy. |
| `--[no-]enable-dns64-all-queries` |  |  | Specifies whether to allow networks bound to this policy to use DNS64 for IPv6-only VM instances. Use --enable-dns64-all-queries to enable and --no-enable-dns64-all-queries to disable. |
| `--enable-inbound-forwarding` |  |  | Specifies whether to allow networks bound to this policy to receive DNS queries sent by VMs or applications over VPN connections. Defaults to False. |
| `--enable-logging` |  |  | Specifies whether to enable query logging. Defaults to False. |
| `--networks` | [NETWORKS,...] |  | The comma separated list of network names to associate with the policy. |
| `--private-alternative-name-servers` | [NAME_SERVERS,...] |  | List of alternative name servers to forward to. All addresses specified for this parameter will be reached through the VPC. |


**Examples:**
```bash
To change the description of a policy, run:

    $ gcloud dns policies update mypolicy --description="Hello, world!"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/policies/update)

---
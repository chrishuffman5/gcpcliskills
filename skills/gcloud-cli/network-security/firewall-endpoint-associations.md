# gcloud network-security firewall-endpoint-associations

create and manage Firewall Plus endpoint associations

### `gcloud network-security firewall-endpoint-associations create`

Create a Firewall Plus endpoint association

Associate the specified network with the firewall endpoint. Successful
creation of a firewall endpoint association results in an association in
READY state. Check the progress of association creation by using gcloud
network-security firewall-endpoint-associations list.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security firewall-endpoint-associations create
    [ASSOCIATION_ID] --network=NETWORK --zone=ZONE
    (--endpoint=ENDPOINT
      : --endpoint-zone=ENDPOINT_ZONE --organization=ORGANIZATION)
    [--async] [--labels=[KEY=VALUE,...]]
    [--max-wait=MAX_WAIT; default="60m"]
    [--tls-inspection-policy=TLS_INSPECTION_POLICY
      : --tls-inspection-policy-project=TLS_INSPECTION_POLICY_PROJECT
      --tls-inspection-policy-region=TLS_INSPECTION_POLICY_REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[ASSOCIATION_ID]
   Name to give the association. If not specified, an auto-generated UUID
   will be used.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--network` | NETWORK |  | _[This must be specified.]_ ID of the network or fully qualified identifier for the network. To set the network-name attribute: + provide the argument --network on the command line. |
| `--zone` | ZONE |  | _[This must be specified.]_ Zone of a firewall endpoint association |
| `--endpoint` | ENDPOINT |  | _[This must be specified.]_ ID of the firewall endpoint or fully qualified identifier for the firewall endpoint. To set the endpoint-name attribute: + provide the argument --endpoint on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--endpoint-zone` | ENDPOINT_ZONE |  | _[This must be specified.]_ Zone of the firewall endpoint. To set the endpoint-zone attribute: + provide the argument --endpoint on the command line with a fully specified name; + provide the argument --endpoint-zone on the command line; + provide the argument --zone on the command line; + provide the argument FIREWALL_ENDPOINT_ASSOCIATION on the command line with a fully specified name. |
| `--organization` | ORGANIZATION |  | _[This must be specified.]_ Organization ID to which the changes should apply. To set the organization attribute: + provide the argument --endpoint on the command line with a fully specified name; + provide the argument --organization on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--max-wait` | MAX_WAIT | 60m | Time to synchronously wait for the operation to complete, after which the operation continues asynchronously. Ignored if --no-async isn't specified. See $ gcloud topic datetimes for information on time formats. |


**Examples:**
```bash
To associate a network with a firewall endpoint, run:

    $ gcloud network-security firewall-endpoint-associations create \
      --network=projects/my-project/networks/global/myNetwork \
      --endpoint=organizations/1234/locations/us-central1-a/\
    firewallEndpoints/my-endpoint --zone=us-central1-a \
        --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/firewall-endpoint-associations/create)

---
### `gcloud network-security firewall-endpoint-associations delete`

Delete a Firewall Plus endpoint association

Unassociate the specified network from a firewall endpoint. Check the
progress of association deletion by using gcloud network-security
firewall-endpoint-associations list.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security firewall-endpoint-associations delete
    (FIREWALL_ENDPOINT_ASSOCIATION : --zone=ZONE) [--async]
    [--max-wait=MAX_WAIT; default="60m"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Firewall endpoint association resource - Firewall Plus. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument FIREWALL_ENDPOINT_ASSOCIATION on the command
   line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FIREWALL_ENDPOINT_ASSOCIATION
     ID of the firewall endpoint association or fully qualified identifier
     for the firewall endpoint association.

     To set the association-name attribute:
     + provide the argument FIREWALL_ENDPOINT_ASSOCIATION on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     Zone of the firewall endpoint association.

     To set the zone attribute:
     + provide the argument FIREWALL_ENDPOINT_ASSOCIATION on the command
       line with a fully specified name;
     + provide the argument --zone on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--max-wait` | MAX_WAIT | 60m | Time to synchronously wait for the operation to complete, after which the operation continues asynchronously. Ignored if --no-async isn't specified. See $ gcloud topic datetimes for information on time formats. |


**Examples:**
```bash
To unassociate a network from a firewall, run:

    $ gcloud network-security firewall-endpoint-associations delete \
        my-assoc --zone=us-central1-a --project=my-project OR
    $ gcloud network-security firewall-endpoint-associations delete \
        projects/my-project/locations/us-central1-a/\
    firewallEndpointAssociations/my-association
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/firewall-endpoint-associations/delete)

---
### `gcloud network-security firewall-endpoint-associations describe`

Describe a Firewall Plus endpoint association

Describe a firewall endpoint association.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security firewall-endpoint-associations describe
    (FIREWALL_ENDPOINT_ASSOCIATION : --zone=ZONE) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Firewall endpoint association resource - Firewall Plus. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument FIREWALL_ENDPOINT_ASSOCIATION on the command
   line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FIREWALL_ENDPOINT_ASSOCIATION
     ID of the firewall endpoint association or fully qualified identifier
     for the firewall endpoint association.

     To set the association-name attribute:
     + provide the argument FIREWALL_ENDPOINT_ASSOCIATION on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     Zone of the firewall endpoint association.

     To set the zone attribute:
     + provide the argument FIREWALL_ENDPOINT_ASSOCIATION on the command
       line with a fully specified name;
     + provide the argument --zone on the command line.
```

**Examples:**
```bash
To get a description of a firewall endpoint association called
my-association, run:

    $ gcloud network-security firewall-endpoint-associations describe \
        my-association --zone=us-central1-a --project=my-project OR
    $ gcloud network-security firewall-endpoint-associations describe \
        projects/my-project/locations/us-central1-a/\
    firewallEndpointAssociations/my-association
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/firewall-endpoint-associations/describe)

---
### `gcloud network-security firewall-endpoint-associations list`

List Firewall Plus endpoint associations

List firewall endpoint associations.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security firewall-endpoint-associations list
    [--zone=ZONE; default="-"] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE | - | Zone for the list operation |


**Examples:**
```bash
To list firewall endpoint associations, run:

    $ gcloud network-security firewall-endpoint-associations list \
        --zone=us-central1-a --project=my-project

To list firewall endpoint associations in all zones, run:

    $ gcloud network-security firewall-endpoint-associations list \
        --project=my-project

The project is automatically read from the core/project property if it is
defined.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/firewall-endpoint-associations/list)

---
### `gcloud network-security firewall-endpoint-associations update`

Update a Firewall Plus endpoint association

Update a firewall endpoint association. Check the progress of association
update by using gcloud network-security firewall-endpoint-associations
describe.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security firewall-endpoint-associations update
    (FIREWALL_ENDPOINT_ASSOCIATION : --zone=ZONE) [--async]
    [--max-wait=MAX_WAIT; default="60m"]
    [--disabled | --update-labels=[KEY=VALUE,...] --clear-labels
      | --remove-labels=[KEY,...] --no-tls-inspection-policy
      | [--tls-inspection-policy=TLS_INSPECTION_POLICY
      : --tls-inspection-policy-project=TLS_INSPECTION_POLICY_PROJECT
      --tls-inspection-policy-region=TLS_INSPECTION_POLICY_REGION]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Firewall endpoint association resource - Firewall Plus. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument FIREWALL_ENDPOINT_ASSOCIATION on the command
   line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FIREWALL_ENDPOINT_ASSOCIATION
     ID of the firewall endpoint association or fully qualified identifier
     for the firewall endpoint association.

     To set the association-name attribute:
     + provide the argument FIREWALL_ENDPOINT_ASSOCIATION on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     Zone of the firewall endpoint association.

     To set the zone attribute:
     + provide the argument FIREWALL_ENDPOINT_ASSOCIATION on the command
       line with a fully specified name;
     + provide the argument --zone on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--max-wait` | MAX_WAIT | 60m | Time to synchronously wait for the operation to complete, after which the operation continues asynchronously. Ignored if --no-async isn't specified. See $ gcloud topic datetimes for information on time formats. |


**Examples:**
```bash
To update labels k1 and k2, run:

    $ gcloud network-security firewall-endpoint-associations update \
        my-assoc --zone=us-central1-a --project=my-proj \
        --update-labels=k1=v1,k2=v2

To remove labels k3 and k4, run:

    $ gcloud network-security firewall-endpoint-associations update \
        my-assoc --zone=us-central1-a --project=my-proj \
        --remove-labels=k3,k4

To clear all labels from the firewall endpoint association, run:

    $ gcloud network-security firewall-endpoint-associations update \
        my-assoc --zone=us-central1-a --project=my-proj --clear-labels
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/firewall-endpoint-associations/update)

---
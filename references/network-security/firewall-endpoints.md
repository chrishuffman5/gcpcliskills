# gcloud network-security firewall-endpoints

create and manage Firewall Plus endpoints

### `gcloud network-security firewall-endpoints create`

Create a Firewall Plus endpoint

Create a firewall endpoint. Successful creation of an endpoint results in
an endpoint in READY state. Check the progress of endpoint creation by
using gcloud network-security firewall-endpoints list.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security firewall-endpoints create
    (FIREWALL_ENDPOINT : --organization=ORGANIZATION --zone=ZONE)
    --billing-project=BILLING_PROJECT [--async] [--description=DESCRIPTION]
    [--enable-jumbo-frames] [--labels=[KEY=VALUE,...]]
    [--max-wait=MAX_WAIT; default="60m"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Firewall endpoint resource - Firewall Plus. The arguments in this group
can be used to specify the attributes of this resource.

This must be specified.

  FIREWALL_ENDPOINT
     ID of the firewall endpoint or fully qualified identifier for the
     firewall endpoint.

     To set the endpoint-name attribute:
     + provide the argument FIREWALL_ENDPOINT on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --organization=ORGANIZATION
     Organization ID of the firewall endpoint.

     To set the organization attribute:
     + provide the argument FIREWALL_ENDPOINT on the command line with a
       fully specified name;
     + provide the argument --organization on the command line.

  --zone=ZONE
     Zone of the firewall endpoint.

     To set the zone attribute:
     + provide the argument FIREWALL_ENDPOINT on the command line with a
       fully specified name;
     + provide the argument --zone on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--billing-project` | BILLING_PROJECT |  | The Google Cloud project ID to use for API enablement check, quota, and endpoint uptime billing. Overrides the default billing/quota_project property value for this command invocation. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--description` | DESCRIPTION |  | Description of the endpoint |
| `--enable-jumbo-frames` |  |  | Enable jumbo frames for the firewall endpoint. To disable jumbo frames, use --no-enable-jumbo-frames. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--max-wait` | MAX_WAIT | 60m | Time to synchronously wait for the operation to complete, after which the operation continues asynchronously. Ignored if --no-async isn't specified. See $ gcloud topic datetimes for information on time formats. |


**Examples:**
```bash
To create a firewall endpoint called my-endpoint, in zone us-central1-a and
organization ID 1234, run:

    $ gcloud network-security firewall-endpoints create my-endpoint \
        --zone=us-central1-a --organization=1234
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/firewall-endpoints/create)

---
### `gcloud network-security firewall-endpoints delete`

Delete a Firewall Plus endpoint

Delete a firewall endpoint. Check the progress of endpoint deletion by
using gcloud network-security firewall-endpoints list.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security firewall-endpoints delete
    (FIREWALL_ENDPOINT : --organization=ORGANIZATION --zone=ZONE) [--async]
    [--max-wait=MAX_WAIT; default="60m"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Firewall endpoint resource - Firewall Plus. The arguments in this group
can be used to specify the attributes of this resource.

This must be specified.

  FIREWALL_ENDPOINT
     ID of the firewall endpoint or fully qualified identifier for the
     firewall endpoint.

     To set the endpoint-name attribute:
     + provide the argument FIREWALL_ENDPOINT on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --organization=ORGANIZATION
     Organization ID of the firewall endpoint.

     To set the organization attribute:
     + provide the argument FIREWALL_ENDPOINT on the command line with a
       fully specified name;
     + provide the argument --organization on the command line.

  --zone=ZONE
     Zone of the firewall endpoint.

     To set the zone attribute:
     + provide the argument FIREWALL_ENDPOINT on the command line with a
       fully specified name;
     + provide the argument --zone on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--max-wait` | MAX_WAIT | 60m | Time to synchronously wait for the operation to complete, after which the operation continues asynchronously. Ignored if --no-async isn't specified. See $ gcloud topic datetimes for information on time formats. |


**Examples:**
```bash
To delete a firewall endpoint called my-endpoint, in zone us-central1-a and
organization ID 1234, run:

    $ gcloud network-security firewall-endpoints delete my-endpoint \
        --zone=us-central1-a --organization=1234

OR

    $ gcloud network-security firewall-endpoints delete \
        organizations/1234/locations/us-central1-a/firewallEndpoints/\
    my-endpoint
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/firewall-endpoints/delete)

---
### `gcloud network-security firewall-endpoints describe`

Describe a Firewall Plus endpoint

Describe a firewall endpoint.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security firewall-endpoints describe
    (FIREWALL_ENDPOINT : --organization=ORGANIZATION --zone=ZONE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Firewall endpoint resource - Firewall Plus. The arguments in this group
can be used to specify the attributes of this resource.

This must be specified.

  FIREWALL_ENDPOINT
     ID of the firewall endpoint or fully qualified identifier for the
     firewall endpoint.

     To set the endpoint-name attribute:
     + provide the argument FIREWALL_ENDPOINT on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --organization=ORGANIZATION
     Organization ID of the firewall endpoint.

     To set the organization attribute:
     + provide the argument FIREWALL_ENDPOINT on the command line with a
       fully specified name;
     + provide the argument --organization on the command line.

  --zone=ZONE
     Zone of the firewall endpoint.

     To set the zone attribute:
     + provide the argument FIREWALL_ENDPOINT on the command line with a
       fully specified name;
     + provide the argument --zone on the command line.
```

**Examples:**
```bash
To get a description of a firewall endpoint called my-endpoint in zone
us-central1-a and organization ID 1234, run:

    $ gcloud network-security firewall-endpoints describe my-endpoint \
        --zone=us-central1-a --organization=1234

OR

    $ gcloud network-security firewall-endpoints describe \
        organizations/1234/locations/us-central1-a/firewallEndpoints/\
    my-endpoint
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/firewall-endpoints/describe)

---
### `gcloud network-security firewall-endpoints list`

List Firewall Plus endpoints

List firewall endpoints.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security firewall-endpoints list --organization=ORGANIZATION
    --zone=ZONE [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION |  | The organization for a list operation |
| `--zone` | ZONE |  | The zone for a list operation |


**Examples:**
```bash
To list firewall endpoints in organization ID 1234, run:

    $ gcloud network-security firewall-endpoints list --organization=1234
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/firewall-endpoints/list)

---
### `gcloud network-security firewall-endpoints update`

Update a Firewall Plus endpoint

Update a firewall endpoint. Check the progress of endpoint update by using
gcloud network-security firewall-endpoints describe.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security firewall-endpoints update
    (FIREWALL_ENDPOINT : --organization=ORGANIZATION --zone=ZONE) [--async]
    [--description=DESCRIPTION] [--max-wait=MAX_WAIT; default="60m"]
    [--update-billing-project=BILLING_PROJECT]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Firewall endpoint resource - Firewall Plus. The arguments in this group
can be used to specify the attributes of this resource.

This must be specified.

  FIREWALL_ENDPOINT
     ID of the firewall endpoint or fully qualified identifier for the
     firewall endpoint.

     To set the endpoint-name attribute:
     + provide the argument FIREWALL_ENDPOINT on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --organization=ORGANIZATION
     Organization ID of the firewall endpoint.

     To set the organization attribute:
     + provide the argument FIREWALL_ENDPOINT on the command line with a
       fully specified name;
     + provide the argument --organization on the command line.

  --zone=ZONE
     Zone of the firewall endpoint.

     To set the zone attribute:
     + provide the argument FIREWALL_ENDPOINT on the command line with a
       fully specified name;
     + provide the argument --zone on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--description` | DESCRIPTION |  | Description of the endpoint |
| `--max-wait` | MAX_WAIT | 60m | Time to synchronously wait for the operation to complete, after which the operation continues asynchronously. Ignored if --no-async isn't specified. See $ gcloud topic datetimes for information on time formats. |
| `--update-billing-project` | BILLING_PROJECT |  | The Google Cloud project ID to use for API enablement check, quota, and endpoint uptime billing. Overrides the default billing/quota_project property value for this command invocation. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update labels k1 and k2, run:

    $ gcloud network-security firewall-endpoints update my-endpoint \
        --zone=us-central1-a --organization=1234 \
        --update-labels=k1=v1,k2=v2

To remove labels k3 and k4, run:

    $ gcloud network-security firewall-endpoints update my-endpoint \
        --zone=us-central1-a --organization=1234 --remove-labels=k3,k4

To clear all labels from the firewall endpoint, run:

    $ gcloud network-security firewall-endpoints update my-endpoint \
        --zone=us-central1-a --organization=1234 --clear-labels
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/firewall-endpoints/update)

---
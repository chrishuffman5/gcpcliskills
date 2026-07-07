# gcloud network-services multicast-domain-activations

manage Network Services MulticastDomainActivations

### `gcloud network-services multicast-domain-activations create`

Create a multicast domain activation

Create a multicast domain activation in the specified location of the
current project.

**Synopsis:**
```
gcloud network-services multicast-domain-activations create
    (MULTICAST_DOMAIN_ACTIVATION : --location=LOCATION)
    --multicast-domain=MULTICAST_DOMAIN [--async]
    [--description=DESCRIPTION] [--disable-placement-policy]
    [--labels=[KEY=VALUE,...]]
    [--aggr-egress-pps=AGGR_EGRESS_PPS
      : --aggr-ingress-pps=AGGR_INGRESS_PPS
      --avg-packet-size=AVG_PACKET_SIZE
      --max-per-group-ingress-pps=MAX_PER_GROUP_INGRESS_PPS
      --max-per-group-subscribers=MAX_PER_GROUP_SUBSCRIBERS]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Multicast domain activation resource - Name of the multicast domain
activation to be created. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument multicast_domain_activation on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MULTICAST_DOMAIN_ACTIVATION
     ID of the multicast domain activation or fully qualified identifier
     for the multicast domain activation.

     To set the multicast_domain_activation attribute:
     + provide the argument multicast_domain_activation on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument multicast_domain_activation on the command
       line with a fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--multicast-domain` | MULTICAST_DOMAIN |  | The multicast domain to be used. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | The description for the multicast domain activation. |
| `--disable-placement-policy` |  |  | True to disable the use of the placement policy for this multicast domain activation. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--aggr-egress-pps` | AGGR_EGRESS_PPS |  | Aggregated egress Packet-Per-Second for all multicast groups in the domain in this zone. |
| `--aggr-ingress-pps` | AGGR_INGRESS_PPS |  | Aggregated ingress Packet-Per-Second for all multicast groups in the domain in this zone. |
| `--avg-packet-size` | AVG_PACKET_SIZE |  | Average packet size (defaults to 512 bytes). |
| `--max-per-group-ingress-pps` | MAX_PER_GROUP_INGRESS_PPS |  | Maximum ingress Packet-Per-Second for a single multicast group in this zone. |
| `--max-per-group-subscribers` | MAX_PER_GROUP_SUBSCRIBERS |  | Maximum number of subscribers for a single multicast group in this zone. |


**Examples:**
```bash
Create a multicast domain activation with the name
'my-multicast-domain-activation', multicast-domain 'path-to-md', and
location 'zone'.

    $ gcloud network-services multicast-domain-activations create \
        my-multicast-domain-activation --multicast-domain=path-to-md \
        --location=zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-domain-activations/create)

---
### `gcloud network-services multicast-domain-activations delete`

Delete a multicast domain activation

Delete a multicast domain activation in the specified location of the
current project.

**Synopsis:**
```
gcloud network-services multicast-domain-activations delete
    (MULTICAST_DOMAIN_ACTIVATION : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Multicast domain activation resource - The multicast domain activation to
delete. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument multicast_domain_activation on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MULTICAST_DOMAIN_ACTIVATION
     ID of the multicast domain activation or fully qualified identifier
     for the multicast domain activation.

     To set the multicast_domain_activation attribute:
     + provide the argument multicast_domain_activation on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument multicast_domain_activation on the command
       line with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a multicast domain activation in the current project, run:

    $ gcloud network-services multicast-domain-activations delete \
        my-multicast-domain-activation --location=zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-domain-activations/delete)

---
### `gcloud network-services multicast-domain-activations describe`

Describe a multicast domain activation

Show details of a multicast domain activation in the specified location of
the current project.

**Synopsis:**
```
gcloud network-services multicast-domain-activations describe
    (MULTICAST_DOMAIN_ACTIVATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Multicast domain activation resource - The multicast domain activation to
display. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument multicast_domain_activation on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MULTICAST_DOMAIN_ACTIVATION
     ID of the multicast domain activation or fully qualified identifier
     for the multicast domain activation.

     To set the multicast_domain_activation attribute:
     + provide the argument multicast_domain_activation on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument multicast_domain_activation on the command
       line with a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe details of a multicast domain activation in the current project
and location, run:

    $ gcloud network-services multicast-domain-activations describe \
        my-multicast-domain-activation --location=zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-domain-activations/describe)

---
### `gcloud network-services multicast-domain-activations list`

List multicast domain activations

List all multicast domain activations in the specified location of the
current project.

**Synopsis:**
```
gcloud network-services multicast-domain-activations list
    --location=LOCATION [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list multicast domain activations in the current project and location,
run:

    $ gcloud network-services multicast-domain-activations list \
        --location=zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-domain-activations/list)

---
### `gcloud network-services multicast-domain-activations update`

Update a multicast domain activation

Update a multicast domain activation in the specified location of the
current project.

**Synopsis:**
```
gcloud network-services multicast-domain-activations update
    (MULTICAST_DOMAIN_ACTIVATION : --location=LOCATION) [--async]
    [--description=DESCRIPTION] [--update-labels=[KEY=VALUE,...]]
    [--aggr-egress-pps=AGGR_EGRESS_PPS --aggr-ingress-pps=AGGR_INGRESS_PPS
      --avg-packet-size=AVG_PACKET_SIZE
      --max-per-group-ingress-pps=MAX_PER_GROUP_INGRESS_PPS
      --max-per-group-subscribers=MAX_PER_GROUP_SUBSCRIBERS]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Multicast domain activation resource - Name of the multicast domain
activation to be updated. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument multicast_domain_activation on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MULTICAST_DOMAIN_ACTIVATION
     ID of the multicast domain activation or fully qualified identifier
     for the multicast domain activation.

     To set the multicast_domain_activation attribute:
     + provide the argument multicast_domain_activation on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument multicast_domain_activation on the command
       line with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | The description for the multicast domain activation. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--aggr-egress-pps` | AGGR_EGRESS_PPS |  | Aggregated egress packets per second for all multicast groups in the domain in this zone. |
| `--aggr-ingress-pps` | AGGR_INGRESS_PPS |  | Aggregated ingress Packet-Per-Second for all multicast groups in the domain in this zone. |
| `--avg-packet-size` | AVG_PACKET_SIZE |  | Average packet size (defaults to 512 bytes). |
| `--max-per-group-ingress-pps` | MAX_PER_GROUP_INGRESS_PPS |  | Maximum ingress Packet-Per-Second for a single multicast group in this zone. |
| `--max-per-group-subscribers` | MAX_PER_GROUP_SUBSCRIBERS |  | Maximum number of subscribers for a single multicast group in this zone. |


**Examples:**
```bash
Update a multicast domain activation with the name
my-multicast-domain-activation and location zone.

    $ gcloud network-services multicast-domain-activations update \
        my-multicast-domain-activation --aggr-egress-pps=10000 \
        --max-per-group-subscribers=10 --location=zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-domain-activations/update)

---
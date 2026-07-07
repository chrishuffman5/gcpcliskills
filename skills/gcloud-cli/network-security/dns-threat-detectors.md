# gcloud network-security dns-threat-detectors

manage Dns Threat Detector resources

### `gcloud network-security dns-threat-detectors create`

Create a DnsThreatDetector resource

Create a DnsThreatDetector resource.

**Synopsis:**
```
gcloud network-security dns-threat-detectors create
    (DNS_THREAT_DETECTOR : --location=LOCATION) --provider=PROVIDER
    [--excluded-networks=[EXCLUDED_NETWORKS,...]] [--labels=[LABELS,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DnsThreatDetector resource - Identifier. Name of the DnsThreatDetector
resource. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument dns_threat_detector on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DNS_THREAT_DETECTOR
     ID of the dnsThreatDetector or fully qualified identifier for the
     dnsThreatDetector.

     To set the dns_threat_detector attribute:
     + provide the argument dns_threat_detector on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the dnsThreatDetector resource.

     To set the location attribute:
     + provide the argument dns_threat_detector on the command line with
       a fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--provider` | PROVIDER |  | The provider used for DNS threat analysis. PROVIDER must be (only one value is supported): infoblox The Infoblox DNS threat detector provider. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--excluded-networks` | [EXCLUDED_NETWORKS,...] |  | _[* set the property core/project.]_ IDs of the networks or fully qualified identifiers for the networks. To set the network attribute: + provide the argument --excluded-networks on the command line. |
| `--labels` | [LABELS,...] |  | _[* set the property core/project.]_ Any labels associated with the DnsThreatDetector, listed as key value pairs. KEY Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. VALUE Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Shorthand Example: --labels=string=string JSON Example: --labels='{"string": "string"}' File Example: --labels=path_to_file.(yaml\|json) |


**Examples:**
```bash
To create DnsThreatDetector resource my-dns-threat-detector, and using the
Infoblox threat detection engine, run:

    $ gcloud network-security dns-threat-detectors create \
        --location=global --provider=infoblox my-dns-threat-detector
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/dns-threat-detectors/create)

---
### `gcloud network-security dns-threat-detectors delete`

Delete a DnsThreatDetector resource

Delete a DnsThreatDetector resource.

**Synopsis:**
```
gcloud network-security dns-threat-detectors delete
    (DNS_THREAT_DETECTOR : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DnsThreatDetector resource - Name of the DnsThreatDetector resource. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument dns_threat_detector on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DNS_THREAT_DETECTOR
     ID of the dnsThreatDetector or fully qualified identifier for the
     dnsThreatDetector.

     To set the dns_threat_detector attribute:
     + provide the argument dns_threat_detector on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the dnsThreatDetector resource.

     To set the location attribute:
     + provide the argument dns_threat_detector on the command line with
       a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To delete DnsThreatDetector resource my-dns-threat-detector, run:

    $ gcloud network-security dns-threat-detectors delete \
        --location=global my-dns-threat-detector
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/dns-threat-detectors/delete)

---
### `gcloud network-security dns-threat-detectors describe`

Describe a DnsThreatDetector resource

Gets details of a DnsThreatDetector resource.

**Synopsis:**
```
gcloud network-security dns-threat-detectors describe
    (DNS_THREAT_DETECTOR : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DnsThreatDetector resource - Name of the DnsThreatDetector resource. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument dns_threat_detector on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DNS_THREAT_DETECTOR
     ID of the dnsThreatDetector or fully qualified identifier for the
     dnsThreatDetector.

     To set the dns_threat_detector attribute:
     + provide the argument dns_threat_detector on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the dnsThreatDetector resource.

     To set the location attribute:
     + provide the argument dns_threat_detector on the command line with
       a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To get details of DnsThreatDetector resource my-dns-threat-detector, run:

    $ gcloud network-security dns-threat-detectors describe \
        --location=global my-dns-threat-detector
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/dns-threat-detectors/describe)

---
### `gcloud network-security dns-threat-detectors list`

List DnsThreatDetector resources

Lists all DnsThreatDetector resources.

**Synopsis:**
```
gcloud network-security dns-threat-detectors list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all DnsThreatDetector resources, run:

    $ gcloud network-security dns-threat-detectors list --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/dns-threat-detectors/list)

---
### `gcloud network-security dns-threat-detectors update`

Update a DnsThreatDetector resource

Update a DnsThreatDetector resource.

**Synopsis:**
```
gcloud network-security dns-threat-detectors update
    (DNS_THREAT_DETECTOR : --location=LOCATION) [--provider=PROVIDER]
    [--excluded-networks=[EXCLUDED_NETWORKS,...]
      | --add-excluded-networks=[ADD_EXCLUDED_NETWORKS,...]
      --clear-excluded-networks
      | --remove-excluded-networks=[REMOVE_EXCLUDED_NETWORKS,...]]
    [--labels=[LABELS,...]
      | --update-labels=[UPDATE_LABELS,...] --clear-labels
      | --remove-labels=REMOVE_LABELS] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DnsThreatDetector resource - Identifier. Name of the DnsThreatDetector
resource. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument dns_threat_detector on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DNS_THREAT_DETECTOR
     ID of the dnsThreatDetector or fully qualified identifier for the
     dnsThreatDetector.

     To set the dns_threat_detector attribute:
     + provide the argument dns_threat_detector on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the dnsThreatDetector resource.

     To set the location attribute:
     + provide the argument dns_threat_detector on the command line with
       a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--provider` | PROVIDER |  | The provider used for DNS threat analysis. PROVIDER must be (only one value is supported): infoblox The Infoblox DNS threat detector provider. |


**Examples:**
```bash
To update DnsThreatDetector resource my-dns-threat-detector with an
additional excluded network, run:

    $ gcloud network-security dns-threat-detectors update \
        --location=global \
        --add-excluded-networks=projects/.../global/networks/\
    my-excluded-network my-dns-threat-detector
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/dns-threat-detectors/update)

---
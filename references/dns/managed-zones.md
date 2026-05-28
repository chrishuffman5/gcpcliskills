# gcloud dns managed-zones

manage your Cloud DNS managed-zones

### `gcloud dns managed-zones create`

Create a Cloud DNS managed-zone

This command creates a Cloud DNS managed-zone.

**Synopsis:**
```
gcloud dns managed-zones create ZONE_NAME --dns-name=DNS_NAME
    [--denial-of-existence=DENIAL_OF_EXISTENCE] [--description=DESCRIPTION]
    [--dnssec-state=DNSSEC_STATE] [--forwarding-targets=[IP_ADDRESSES,...]]
    [--gkeclusters=[GKECLUSTERS,...]] [--ksk-algorithm=KSK_ALGORITHM]
    [--ksk-key-length=KSK_KEY_LENGTH] [--labels=[KEY=VALUE,...]]
    [--location=LOCATION] [--[no-]log-dns-queries]
    [--managed-reverse-lookup] [--networks=[NETWORK,...]]
    [--private-forwarding-targets=[IP_ADDRESSES,...]]
    [--service-directory-namespace=SERVICE_DIRECTORY_NAMESPACE]
    [--visibility=VISIBILITY; default="public"]
    [--zsk-algorithm=ZSK_ALGORITHM] [--zsk-key-length=ZSK_KEY_LENGTH]
    [--target-network=TARGET_NETWORK --target-project=TARGET_PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ZONE_NAME
   The name of the managed-zone to be created.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--dns-name` | DNS_NAME |  | The DNS name suffix that will be managed with the created zone. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--denial-of-existence` | one of: nsec, nsec3 |  | Requires DNSSEC enabled. DENIAL_OF_EXISTENCE must be one of: nsec, nsec3. |
| `--description` | DESCRIPTION |  | Short description for the managed zone. |
| `--dnssec-state` | one of: off Disable DNSSEC for the managed zone |  | The DNSSEC state for this managed zone. DNSSEC_STATE must be one of: off Disable DNSSEC for the managed zone. on Enable DNSSEC for the managed zone. transfer Enable DNSSEC and allow transferring a signed zone in or out. |
| `--forwarding-targets` | [IP_ADDRESSES,...] |  | List of IPv4/IPv6 addresses or one domain name of the target name server that the zone will forward queries to. Ignored for public visibility. Non-RFC1918 addresses will forward to the target through the Internet. RFC1918 addresses will forward through the VPC. |
| `--gkeclusters` | [GKECLUSTERS,...] |  | List of GKE clusters that the zone should be visible in if the zone visibility is [private]. |
| `--ksk-algorithm` | one of: ecdsap256sha256, ecdsap384sha384, rsasha1, rsasha256, rsasha512 |  | String mnemonic specifying the DNSSEC algorithm of the key-signing key. Requires DNSSEC enabled. KSK_ALGORITHM must be one of: ecdsap256sha256, ecdsap384sha384, rsasha1, rsasha256, rsasha512. |
| `--ksk-key-length` | KSK_KEY_LENGTH |  | Length of the key-signing key in bits. Requires DNSSEC enabled. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--location` | LOCATION |  | Specifies the desired service location the request is sent to. Defaults to Cloud DNS global service. Use --location=global if you want to target the global service. |
| `--[no-]log-dns-queries` |  |  | Specifies whether to enable query logging. Defaults to False. Use --log-dns-queries to enable and --no-log-dns-queries to disable. |
| `--managed-reverse-lookup` |  |  | Specifies whether this zone is a managed reverse lookup zone, required for Cloud DNS to correctly resolve Non-RFC1918 PTR records. |
| `--networks` | [NETWORK,...] |  | List of networks that the zone should be visible in if the zone visibility is [private]. |
| `--private-forwarding-targets` | [IP_ADDRESSES,...] |  | List of IPv4/IPv6 addresses or one domain name of the target name server that the zone will forward queries to. Ignored for public visibility. All addresses specified for this parameter will be reached through the VPC. |
| `--service-directory-namespace` | SERVICE_DIRECTORY_NAMESPACE |  | The fully qualified URL of the service directory namespace that should be associated with the zone. Ignored for public visibility zones. |
| `--visibility` | one of: public, private | public | Visibility of the zone. Public zones are visible to the public internet. Private zones are only visible in your internal networks denoted by the --networks flag. VISIBILITY must be one of: public, private. |
| `--zsk-algorithm` | one of: ecdsap256sha256, ecdsap384sha384, rsasha1, rsasha256, rsasha512 |  | String mnemonic specifying the DNSSEC algorithm of the key-signing key. Requires DNSSEC enabled. ZSK_ALGORITHM must be one of: ecdsap256sha256, ecdsap384sha384, rsasha1, rsasha256, rsasha512. |
| `--zsk-key-length` | ZSK_KEY_LENGTH |  | Length of the zone-signing key in bits. Requires DNSSEC enabled. |
| `--target-network` | TARGET_NETWORK |  | Network ID of the Google Compute Engine private network to forward queries to. |
| `--target-project` | TARGET_PROJECT |  | Project ID of the Google Compute Engine private network to forward queries to. |


**Examples:**
```bash
To create a managed-zone, run:

    $ gcloud dns managed-zones create my-zone --dns-name=my.zone.com. \
        --description="My zone!"

To create a managed-zone with DNSSEC, run:

    $ gcloud dns managed-zones create my-zone-2 \
        --description="Signed Zone" --dns-name=myzone.example \
        --dnssec-state=on

    To create a zonal managed-zone scoped to a GKE Cluster in us-east1-a, run:

    $ gcloud dns managed-zones create my-zonal-zone \
        --description="Signed Zone" --dns-name=cluster.local \
        --visibility=private --gkeclusters=cluster1 \
        --location=us-east1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/managed-zones/create)

---
### `gcloud dns managed-zones delete`

Delete an empty Cloud DNS managed-zone

This command deletes an empty Cloud DNS managed-zone. An empty managed-zone
has only SOA and NS record-sets.

**Synopsis:**
```
gcloud dns managed-zones delete ZONE_NAME [--location=LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ZONE_NAME
   The name of the empty managed-zone to be deleted.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Specifies the desired service location the request is sent to. Defaults to Cloud DNS global service. Use --location=global if you want to target the global service. |


**Examples:**
```bash
To delete an empty managed-zone, run:

    $ gcloud dns managed-zones delete my-zone

To delete an empty zonal managed-zone in us-east1-c, run:

    $ gcloud dns managed-zones delete my-zone --location=us-east1-c
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/managed-zones/delete)

---
### `gcloud dns managed-zones describe`

View the details of a Cloud DNS managed-zone

This command displays the details of the specified managed-zone.

**Synopsis:**
```
gcloud dns managed-zones describe ZONE [--location=LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Zone resource - The name of the managed-zone to be described. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument zone on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ZONE
     ID of the zone or fully qualified identifier for the zone.

     To set the zone attribute:
     + provide the argument zone on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Specifies the desired service location the request is sent to. Defaults to Cloud DNS global service. Use --location=global if you want to target the global service. |


**Examples:**
```bash
To display the details of your managed-zone, run:

    $ gcloud dns managed-zones describe my-zone

To display the details of a zonal managed-zone in Zonal Cloud DNS service
in us-east1-c, run:

    $ gcloud dns managed-zones describe my-zone --location=us-east1-c
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/managed-zones/describe)

---
### `gcloud dns managed-zones get-iam-policy`

Get the IAM policy for a Cloud DNS managed-zone

This command displays the IAM policy of the specified managed-zone.

**Synopsis:**
```
gcloud dns managed-zones get-iam-policy ZONE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Zone resource - The name of the managed-zone to get the IAM policy for.
This represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument zone on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ZONE
     ID of the zone or fully qualified identifier for the zone.

     To set the zone attribute:
     + provide the argument zone on the command line.
```

**Examples:**
```bash
To view the details of your managed-zone IAM policy , run:

    $ gcloud dns managed-zones get-iam-policy my-zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/managed-zones/get-iam-policy)

---
### `gcloud dns managed-zones list`

View the list of all your managed-zones

This command displays the list of your managed-zones.

**Synopsis:**
```
gcloud dns managed-zones list [--location=LOCATION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Specifies the desired service location the request is sent to. Defaults to Cloud DNS global service. Use --location=global if you want to target the global service. |


**Examples:**
```bash
To see the list of all managed-zones, run:

    $ gcloud dns managed-zones list

To see the list of first 10 managed-zones, run:

    $ gcloud dns managed-zones list --limit=10

To see the list of all managed-zones in a Zonal Cloud DNS service in
us-east1-c, run:

    $ gcloud dns managed-zones list --location=us-east1-c
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/managed-zones/list)

---
### `gcloud dns managed-zones set-iam-policy`

Set the IAM policy for a Cloud DNS managed-zone

This command sets the IAM policy of the specified managed-zone.

**Synopsis:**
```
gcloud dns managed-zones set-iam-policy ZONE --policy-file=POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Zone resource - The name of the managed-zone to set the IAM policy for.
This represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument zone on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ZONE
     ID of the zone or fully qualified identifier for the zone.

     To set the zone attribute:
     + provide the argument zone on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--policy-file` | POLICY_FILE |  | JSON or YAML file with the IAM policy |


**Examples:**
```bash
To set the IAM policy of your managed-zone , run:

    $ gcloud dns managed-zones set-iam-policy my-zone \
        --policy-file=policy.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/managed-zones/set-iam-policy)

---
### `gcloud dns managed-zones update`

Update an existing Cloud DNS managed-zone

Update an existing Cloud DNS managed-zone.

**Synopsis:**
```
gcloud dns managed-zones update ZONE [--async]
    [--denial-of-existence=DENIAL_OF_EXISTENCE] [--description=DESCRIPTION]
    [--dnssec-state=DNSSEC_STATE] [--forwarding-targets=[IP_ADDRESSES,...]]
    [--gkeclusters=[GKECLUSTERS,...]] [--ksk-algorithm=KSK_ALGORITHM]
    [--ksk-key-length=KSK_KEY_LENGTH] [--location=LOCATION]
    [--[no-]log-dns-queries] [--managed-reverse-lookup]
    [--networks=[NETWORK,...]]
    [--private-forwarding-targets=[IP_ADDRESSES,...]]
    [--update-labels=[KEY=VALUE,...]] [--zsk-algorithm=ZSK_ALGORITHM]
    [--zsk-key-length=ZSK_KEY_LENGTH]
    [--clear-labels | --remove-labels=[KEY,...]]
    [--target-network=TARGET_NETWORK --target-project=TARGET_PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Zone resource - The name of the managed-zone to be updated. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument zone on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ZONE
     ID of the zone or fully qualified identifier for the zone.

     To set the zone attribute:
     + provide the argument zone on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--denial-of-existence` | one of: nsec, nsec3 |  | Requires DNSSEC enabled. DENIAL_OF_EXISTENCE must be one of: nsec, nsec3. |
| `--description` | DESCRIPTION |  | Short description for the managed zone. |
| `--dnssec-state` | one of: off Disable DNSSEC for the managed zone |  | The DNSSEC state for this managed zone. DNSSEC_STATE must be one of: off Disable DNSSEC for the managed zone. on Enable DNSSEC for the managed zone. transfer Enable DNSSEC and allow transferring a signed zone in or out. |
| `--forwarding-targets` | [IP_ADDRESSES,...] |  | List of IPv4/IPv6 addresses or one domain name of the target name server that the zone will forward queries to. Ignored for public visibility. Non-RFC1918 addresses will forward to the target through the Internet. RFC1918 addresses will forward through the VPC. |
| `--gkeclusters` | [GKECLUSTERS,...] |  | List of GKE clusters that the zone should be visible in if the zone visibility is [private]. |
| `--ksk-algorithm` | one of: ecdsap256sha256, ecdsap384sha384, rsasha1, rsasha256, rsasha512 |  | String mnemonic specifying the DNSSEC algorithm of the key-signing key. Requires DNSSEC enabled. KSK_ALGORITHM must be one of: ecdsap256sha256, ecdsap384sha384, rsasha1, rsasha256, rsasha512. |
| `--ksk-key-length` | KSK_KEY_LENGTH |  | Length of the key-signing key in bits. Requires DNSSEC enabled. |
| `--location` | LOCATION |  | Specifies the desired service location the request is sent to. Defaults to Cloud DNS global service. Use --location=global if you want to target the global service. |
| `--[no-]log-dns-queries` |  |  | Specifies whether to enable query logging. Defaults to False. Use --log-dns-queries to enable and --no-log-dns-queries to disable. |
| `--managed-reverse-lookup` |  |  | Specifies whether this zone is a managed reverse lookup zone, required for Cloud DNS to correctly resolve Non-RFC1918 PTR records. |
| `--networks` | [NETWORK,...] |  | List of networks that the zone should be visible in if the zone visibility is [private]. |
| `--private-forwarding-targets` | [IP_ADDRESSES,...] |  | List of IPv4/IPv6 addresses or one domain name of the target name server that the zone will forward queries to. Ignored for public visibility. All addresses specified for this parameter will be reached through the VPC. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--zsk-algorithm` | one of: ecdsap256sha256, ecdsap384sha384, rsasha1, rsasha256, rsasha512 |  | String mnemonic specifying the DNSSEC algorithm of the key-signing key. Requires DNSSEC enabled. ZSK_ALGORITHM must be one of: ecdsap256sha256, ecdsap384sha384, rsasha1, rsasha256, rsasha512. |
| `--zsk-key-length` | ZSK_KEY_LENGTH |  | Length of the zone-signing key in bits. Requires DNSSEC enabled. |
| `--target-network` | TARGET_NETWORK |  | _[--update-labels is applied first.]_ Network ID of the Google Compute Engine private network to forward queries to. |
| `--target-project` | TARGET_PROJECT |  | _[--update-labels is applied first.]_ Project ID of the Google Compute Engine private network to forward queries to. |


**Examples:**
```bash
To change the description of a managed-zone, run:

    $ gcloud dns managed-zones update my-zone \
        --description="Hello, world!"

To change the description of a zonal managed-zone in us-east1-a, run:

    $ gcloud dns managed-zones update my-zone \
        --description="Hello, world!" --location=us-east1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/managed-zones/update)

---
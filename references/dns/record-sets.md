# gcloud dns record-sets

manage the record-sets within your managed-zones

### `gcloud dns record-sets create`

Creates a record-set in a managed-zone

This command creates a record-set contained within the specified
managed-zone.

**Synopsis:**
```
gcloud dns record-sets create DNS_NAME --type=TYPE --zone=ZONE, -z ZONE
    (--rrdatas=[RRDATA,...] | [--routing-policy-type=ROUTING_POLICY_TYPE
      (--routing-policy-data=ROUTING_POLICY_DATA
      | --routing-policy-item=[ROUTING_POLICY_ITEM,...]
      | [--routing-policy-backup-data-type=ROUTING_POLICY_BACKUP_DATA_TYPE
      --routing-policy-primary-data=ROUTING_POLICY_PRIMARY_DATA
      (--routing-policy-backup-data=ROUTING_POLICY_BACKUP_DATA
      | --routing-policy-backup-item=[ROUTING_POLICY_BACKUP_ITEM,...])
      : --backup-data-trickle-ratio=BACKUP_DATA_TRICKLE_RATIO])
      : --enable-geo-fencing --enable-health-checking
      | --health-check=HEALTH_CHECK]) [--location=LOCATION] [--ttl=TTL]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DNS_NAME
   DNS or domain name of the record-set.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--type` | TYPE |  | DNS record type of the record-set (e.g. A, AAAA, MX etc.). |
| `--zone` | ZONE, -z ZONE |  | Name of the managed zone whose record sets you want to manage. |
| `--routing-policy-data` |  |  | _[Resource record sets arguments. Can specify either --rrdatas or both]_ |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Specifies the desired service location the request is sent to. Defaults to Cloud DNS global service. Use --location=global if you want to target the global service. |
| `--ttl` | TTL |  | TTL (time to live) for the record-set. |


**Examples:**
```bash
To create a record-set with dnsName foo.bar.com., record type A, rrdata
[1.2.3.4, 9.8.7.6] and ttl 60 in my_zone run this:

    $ gcloud dns record-sets create foo.bar.com. \
        --rrdatas=1.2.3.4,9.8.7.6 --type=A --ttl=60 --zone=my_zone

To create a geo routed record-set with dnsName foo.bar.com., record type A,
routing_policy_data "us-centra1=1.2.3.4,2.3.4.5;us-west1=3.4.5.6,9.8.7.6"
and ttl 60 in my_zone.

    $ gcloud dns record-sets create foo.bar.com. \
        --routing_policy_data="us-centra1=1.2.3.4,2.3.4.5;us-west1=3.4.5\
    .6,9.8.7.6" --routing_policy_type=GEO --type=A --ttl=60 \
        --zone=my_zone --location=us-east1-a

To create a record-set with dnsName foo.bar.com., record type A, rrdata
[1.2.3.4, 9.8.7.6] and ttl 60 in my_zone in us-east1-a run this:

    $ gcloud dns record-sets create us-east1-a.bar.com. \
        --rrdatas=1.2.3.4,9.8.7.6 --type=A --ttl=60 --zone=my_zone \
        --location=us-east1-a

To create a failover type health checked routed record-set with dnsName
foo.bar.com., record type A, primary routing data "config1", backup routing
data "us-centra1=1.2.3.4,2.3.4.5;us-west1=3.4.5.6,9.8.7.6", with a trickle
traffic ratio of 10% to the backup data, and ttl 60 in my_zone.

    $ gcloud dns record-sets create foo.bar.com. --type=A --ttl=60 \
        --zone=routing-policy-test --routing_policy_type=FAILOVER \
        --routing-policy-primary-data='config1' \
        --routing-policy-backup-data-type=GEO \
        --routing-policy-backup-data='us-centra1=1.2.3.4,2.3.4.5;us-west\
    1=3.4.5.6,9.8.7.6' --backup-data-trickle-ratio=0.1 \
        --enable-health-checking --zone=my_zone

To create a geo fenced health checked routed record-set with dnsName
foo.bar.com., record type A, routing-policy-data
"us-centra1=config1,config2;us-west1=3.4.5.6,9.8.7.6", and ttl 60 in
my_zone.

    $ gcloud dns record-sets create foo.bar.com. --type=A --ttl=60 \
        --zone=routing-policy-test --routing_policy_type=GEO \
        --routing_policy_data='us-centra1=config1,config2;us-west1=3.4.5\
    .6,9.8.7.6' --enable-health-checking --enable-geo-fencing \
        --zone=my_zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/record-sets/create)

---
### `gcloud dns record-sets delete`

Delete a record-set in a managed-zone

This command deletes a record-set contained within the specified
managed-zone.

**Synopsis:**
```
gcloud dns record-sets delete DNS_NAME --type=TYPE --zone=ZONE, -z ZONE
    [--location=LOCATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DNS_NAME
   DNS or domain name of the record-set.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--type` | TYPE |  | DNS record type of the record-set (e.g. A, AAAA, MX etc.). |
| `--zone` | ZONE, -z ZONE |  | Name of the managed zone whose record sets you want to manage. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Specifies the desired service location the request is sent to. Defaults to Cloud DNS global service. Use --location=global if you want to target the global service. |


**Examples:**
```bash
To delete a record-set with dnsName foo.bar.com. and record type A, rrdata
run:

    $ gcloud dns record-sets delete foo.bar.com. --type=A --zone=my_zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/record-sets/delete)

---
### `gcloud dns record-sets describe`

Describe a record-set in a managed-zone

This command describes a record-set contained within the specified
managed-zone.

**Synopsis:**
```
gcloud dns record-sets describe DNS_NAME --type=TYPE --zone=ZONE, -z ZONE
    [--location=LOCATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DNS_NAME
   DNS or domain name of the record-set.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--type` | TYPE |  | DNS record type of the record-set (e.g. A, AAAA, MX etc.). |
| `--zone` | ZONE, -z ZONE |  | Name of the managed zone whose record sets you want to manage. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Specifies the desired service location the request is sent to. Defaults to Cloud DNS global service. Use --location=global if you want to target the global service. |


**Examples:**
```bash
To describe a record-set with dnsName foo.bar.com. and record type A,
rrdata run:

    $ gcloud dns record-sets describe foo.bar.com. --type=A \
        --zone=my_zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/record-sets/describe)

---
### `gcloud dns record-sets export`

Export your record-sets into a file

This command exports the record-sets contained within the specified
managed-zone into a file. The formats you can export to are YAML records
format (default) and BIND zone file format.

**Synopsis:**
```
gcloud dns record-sets export RECORDS_FILE --zone=ZONE, -z ZONE
    [--location=LOCATION] [--zone-file-format] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RECORDS_FILE
   File to which record-sets should be exported.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE, -z ZONE |  | Name of the managed zone whose record sets you want to manage. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Specifies the desired service location the request is sent to. Defaults to Cloud DNS global service. Use --location=global if you want to target the global service. |
| `--zone-file-format` |  |  | Indicates that records-file should be in the zone file format. When using this flag, expect the record-set to be exported to a BIND zone formatted file. If you omit this flag, the record-set is exported into a YAML formatted records file. Note, this format flag determines the format of the output recorded in the records-file; it is different from the global --format flag which affects console output alone. |


**Examples:**
```bash
To export record-sets into a yaml file, run:

    $ gcloud dns record-sets export records.yaml --zone=examplezonename

To export record-sets into a BIND zone formatted file instead, run:

    $ gcloud dns record-sets export pathto.zonefile \
        --zone=examplezonename --zone-file-format

Similarly, to import record-sets into a BIND zone formatted zone file, run:

    $ gcloud dns record-sets import pathto.zonefile --zone-file-format \
        --zone=examplezonename
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/record-sets/export)

---
### `gcloud dns record-sets import`

Import record-sets into your managed-zone

This command imports record-sets contained within the specified record-sets
file into your managed-zone. Note that NS records for the origin of the
zone and the SOA NS field are not imported since name-servers are managed
by Cloud DNS. By default, record-sets cannot be imported if there are any
conflicts. A conflict exists if an existing record-set has the same name
and type as a record-set that is being imported. In contrast, if the
--delete-all-existing flag is used, the imported record-sets will replace
all the records-sets currently in the managed-zone.

**Synopsis:**
```
gcloud dns record-sets import RECORDS_FILE --zone=ZONE, -z ZONE
    [--delete-all-existing] [--location=LOCATION] [--replace-origin-ns]
    [--zone-file-format] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RECORDS_FILE
   File from which record-sets should be imported. For examples of
   YAML-formatted and BIND zone-formatted records files, refer to
   https://cloud.google.com/dns/records#importing_and_exporting_record_sets
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE, -z ZONE |  | Name of the managed zone whose record sets you want to manage. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--delete-all-existing` |  |  | Indicates that all existing record-sets should be deleted before importing the record-sets in the records-file. |
| `--location` | LOCATION |  | Specifies the desired service location the request is sent to. Defaults to Cloud DNS global service. Use --location=global if you want to target the global service. |
| `--replace-origin-ns` |  |  | Indicates that NS records for the origin of a zone should be imported if defined |
| `--zone-file-format` |  |  | Indicates that the input records-file is in BIND zone format. If omitted, indicates that the records-file is in YAML format. |


**Examples:**
```bash
To import record-sets from a yaml record-sets file, run:

    $ gcloud dns record-sets import YAML_RECORDS_FILE --zone=MANAGED_ZONE

To import record-sets from a zone file, run:

    $ gcloud dns record-sets import ZONE_FILE --zone-file-format \
        --zone=MANAGED_ZONE

To replace all the record-sets in your zone with records from a yaml file,
run:

    $ gcloud dns record-sets import YAML_RECORDS_FILE \
        --delete-all-existing --zone=MANAGED_ZONE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/record-sets/import)

---
### `gcloud dns record-sets list`

View the list of record-sets in a managed-zone

This command displays the list of record-sets contained within the
specified managed-zone.

**Synopsis:**
```
gcloud dns record-sets list --zone=ZONE, -z ZONE [--location=LOCATION]
    [--name=NAME : --type=TYPE] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE, -z ZONE |  | Name of the managed zone whose record sets you want to manage. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Specifies the desired service location the request is sent to. Defaults to Cloud DNS global service. Use --location=global if you want to target the global service. |
| `--name` | NAME |  | Only list record-sets with this exact domain name. |
| `--type` | TYPE |  | Only list records of this type. If present, the --name parameter must also be present. |


**Examples:**
```bash
To see the list of all record-sets in my_zone, run:

    $ gcloud dns record-sets list --zone=my_zone

To see the list of first 10 record-sets in my_zone, run:

    $ gcloud dns record-sets list --zone=my_zone --limit=10

To see the list of 'my.zone.com.' record-sets in my_zone, run:

    $ gcloud dns record-sets list --zone=my_zone --name="my.zone.com."

To see the list of 'my.zone.com.' CNAME record-sets in my_zone, run:

    $ gcloud dns record-sets list --zone=my_zone --name="my.zone.com." \
        --type="CNAME"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/record-sets/list)

---
### `gcloud dns record-sets update`

Updates a record-set in a managed-zone

This command updates a record-set contained within the specified
managed-zone.

**Synopsis:**
```
gcloud dns record-sets update DNS_NAME --type=TYPE --zone=ZONE, -z ZONE
    (--rrdatas=[RRDATA,...] | [--routing-policy-type=ROUTING_POLICY_TYPE
      (--routing-policy-data=ROUTING_POLICY_DATA
      | --routing-policy-item=[ROUTING_POLICY_ITEM,...]
      | [--routing-policy-backup-data-type=ROUTING_POLICY_BACKUP_DATA_TYPE
      --routing-policy-primary-data=ROUTING_POLICY_PRIMARY_DATA
      (--routing-policy-backup-data=ROUTING_POLICY_BACKUP_DATA
      | --routing-policy-backup-item=[ROUTING_POLICY_BACKUP_ITEM,...])
      : --backup-data-trickle-ratio=BACKUP_DATA_TRICKLE_RATIO])
      : --enable-geo-fencing --enable-health-checking
      | --health-check=HEALTH_CHECK]) [--location=LOCATION] [--ttl=TTL]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DNS_NAME
   DNS or domain name of the record-set.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--type` | TYPE |  | DNS record type of the record-set (e.g. A, AAAA, MX etc.). |
| `--zone` | ZONE, -z ZONE |  | Name of the managed zone whose record sets you want to manage. |
| `--routing-policy-data` |  |  | _[Resource record sets arguments. Can specify either --rrdatas or both]_ |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Specifies the desired service location the request is sent to. Defaults to Cloud DNS global service. Use --location=global if you want to target the global service. |
| `--ttl` | TTL |  | TTL (time to live) for the record-set. |


**Examples:**
```bash
To update a record-set with dnsName foo.bar.com., record type A to have
rrdata [1.2.3.4, 9.8.7.6] and ttl 60 in my_zone, run:

    $ gcloud dns record-sets update foo.bar.com. \
        --rrdatas=1.2.3.4,9.8.7.6 --type=A --ttl=60 --zone=my_zone

To update a record-set with dnsName foo.bar.com., record type A to have
rrdata [1.2.3.4, 9.8.7.6] and ttl 60 in my_zone that is located in
us-east1-a, run:

    $ gcloud dns record-sets update foo.bar.com. \
        --rrdatas=1.2.3.4,9.8.7.6 --type=A --ttl=60 --zone=my_zone \
        --location=us-east1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/record-sets/update)

---

## `gcloud dns record-sets changes` — view details about changes to your Cloud DNS record-sets
### `gcloud dns record-sets changes describe`

View the details of a change

This command displays the details of the specified change.

**Synopsis:**
```
gcloud dns record-sets changes describe CHANGE_ID --zone=ZONE, -z ZONE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CHANGE_ID
   The ID of the change you want details for.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE, -z ZONE |  | Name of the managed zone whose record sets you want to manage. |


**Examples:**
```bash
To display the details of a change, run:

    $ gcloud dns record-sets changes describe change_id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/record-sets/changes/describe)

---
### `gcloud dns record-sets changes list`

View the list of changes that have been made to your record-sets

This command displays the list of changes that have been made to your
record-sets.

**Synopsis:**
```
gcloud dns record-sets changes list --zone=ZONE, -z ZONE
    [--sort-order=SORT_ORDER] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE, -z ZONE |  | Name of the managed zone whose record sets you want to manage. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--sort-order` | one of: ascending, descending |  | Sort order for listing. SORT_ORDER must be one of: ascending, descending. |


**Examples:**
```bash
To see the list of changes, run:

    $ gcloud dns record-sets changes list

To see the list of first 10 changes, run:

    $ gcloud dns record-sets changes list --limit=10
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/record-sets/changes/list)

---

## `gcloud dns record-sets transaction` — make scriptable and transactional changes to your record-sets
### `gcloud dns record-sets transaction abort`

Abort transaction

This command aborts the transaction and deletes the transaction file.

**Synopsis:**
```
gcloud dns record-sets transaction abort --zone=ZONE, -z ZONE
    [--transaction-file=TRANSACTION_FILE; default="transaction.yaml"]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE, -z ZONE |  | Name of the managed zone whose record sets you want to manage. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--transaction-file` | TRANSACTION_FILE | transaction.yaml | Path of the file which contains the transaction. |


**Examples:**
```bash
To abort the transaction, run:

    $ gcloud dns record-sets transaction abort --zone=MANAGED_ZONE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/record-sets/transaction/abort)

---
### `gcloud dns record-sets transaction add`

Append a record-set addition to the transaction

This command appends a record-set addition to the transaction.

For a guide detailing how to manage records, see:
https://cloud.google.com/dns/records/

**Synopsis:**
```
gcloud dns record-sets transaction add RRDATAS [RRDATAS ...] --name=NAME
    --ttl=TTL --type=TYPE --zone=ZONE, -z ZONE
    [--transaction-file=TRANSACTION_FILE; default="transaction.yaml"]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RRDATAS [RRDATAS ...]
   DNS data (Address/CNAME/MX info, etc.) of the record-set to add. This
   is RDATA; the format of this information varies depending on the type
   and class of the resource record.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--name` | NAME |  | DNS or domain name of the record-set to add. |
| `--ttl` | TTL |  | TTL (time to live) for the record-set to add. |
| `--type` | TYPE |  | DNS record type of the record-set to add. |
| `--zone` | ZONE, -z ZONE |  | Name of the managed zone whose record sets you want to manage. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--transaction-file` | TRANSACTION_FILE | transaction.yaml | Path of the file which contains the transaction. |


**Examples:**
```bash
To add an A record with an IP address of "1.2.3.4", domain name of
"my.domain.", and a managed zone "MANAGED_ZONE", run:

    $ gcloud dns record-sets transaction add "1.2.3.4" \
        --name=my.domain. --ttl=1234 --type=A --zone=MANAGED_ZONE

To add a TXT record with multiple data values while specifying time to live
as 14400 seconds, run:

    $ gcloud dns record-sets transaction add "Hello world" "Bye world" \
        --name=my.domain. --ttl=14400 --type=TXT --zone=MANAGED_ZONE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/record-sets/transaction/add)

---
### `gcloud dns record-sets transaction describe`

Describe the transaction

This command displays the contents of the transaction.

**Synopsis:**
```
gcloud dns record-sets transaction describe --zone=ZONE, -z ZONE
    [--transaction-file=TRANSACTION_FILE; default="transaction.yaml"]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE, -z ZONE |  | Name of the managed zone whose record sets you want to manage. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--transaction-file` | TRANSACTION_FILE | transaction.yaml | Path of the file which contains the transaction. |


**Examples:**
```bash
To look at the contents of the transaction, run:

    $ gcloud dns record-sets transaction describe --zone=MANAGED_ZONE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/record-sets/transaction/describe)

---
### `gcloud dns record-sets transaction execute`

Execute the transaction on Cloud DNS

This command executes the transaction on Cloud DNS. This will result in
record-sets being changed as specified in the transaction.

**Synopsis:**
```
gcloud dns record-sets transaction execute --zone=ZONE, -z ZONE
    [--transaction-file=TRANSACTION_FILE; default="transaction.yaml"]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE, -z ZONE |  | Name of the managed zone whose record sets you want to manage. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--transaction-file` | TRANSACTION_FILE | transaction.yaml | Path of the file which contains the transaction. |


**Examples:**
```bash
To execute the transaction, run:

    $ gcloud dns record-sets transaction execute --zone=MANAGED_ZONE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/record-sets/transaction/execute)

---
### `gcloud dns record-sets transaction remove`

Append a record-set deletion to the transaction

This command appends a record-set deletion to the transaction.

**Synopsis:**
```
gcloud dns record-sets transaction remove RRDATAS [RRDATAS ...] --name=NAME
    --ttl=TTL --type=TYPE --zone=ZONE, -z ZONE
    [--transaction-file=TRANSACTION_FILE; default="transaction.yaml"]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RRDATAS [RRDATAS ...]
   DNS name of the record-set to be removed.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--name` | NAME |  | DNS name of the record-set to be removed. |
| `--ttl` | TTL |  | TTL for the record-set to be removed. |
| `--type` | TYPE |  | Type of the record-set to be removed. |
| `--zone` | ZONE, -z ZONE |  | Name of the managed zone whose record sets you want to manage. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--transaction-file` | TRANSACTION_FILE | transaction.yaml | Path of the file which contains the transaction. |


**Examples:**
```bash
To remove an A record, run:

    $ gcloud dns record-sets transaction remove --zone=MANAGED_ZONE \
        --name=my.domain. --ttl=1234 --type=A "1.2.3.4"

To remove a TXT record with multiple data values, run:

    $ gcloud dns record-sets transaction remove --zone=MANAGED_ZONE \
        --name=my.domain. --ttl=2345 --type=TXT "Hello world" \
        "Bye world"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/record-sets/transaction/remove)

---
### `gcloud dns record-sets transaction start`

Start a transaction

This command starts a transaction.

**Synopsis:**
```
gcloud dns record-sets transaction start --zone=ZONE, -z ZONE
    [--transaction-file=TRANSACTION_FILE; default="transaction.yaml"]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE, -z ZONE |  | Name of the managed zone whose record sets you want to manage. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--transaction-file` | TRANSACTION_FILE | transaction.yaml | Path of the file which contains the transaction. |


**Examples:**
```bash
To start a transaction, run:

    $ gcloud dns record-sets transaction start --zone=MANAGED_ZONE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/record-sets/transaction/start)

---
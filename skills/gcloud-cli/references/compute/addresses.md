# gcloud compute addresses

read and manipulate Compute Engine addresses

### `gcloud compute addresses create`

Reserve IP addresses

gcloud compute addresses create is used to reserve one or more IP
addresses. Once an IP address is reserved, it will be associated with the
project until it is released using 'gcloud compute addresses delete'.
Ephemeral IP addresses that are in use by resources in the project can be
reserved using the '--addresses' flag.

**Synopsis:**
```
gcloud compute addresses create [NAME ...] [--description=DESCRIPTION]
    [--endpoint-type=ENDPOINT_TYPE] [--ip-collection=IP_COLLECTION]
    [--network=NETWORK] [--network-tier=NETWORK_TIER]
    [--prefix-length=PREFIX_LENGTH] [--purpose=PURPOSE] [--subnet=SUBNET]
    [--addresses=ADDRESS,[ADDRESS,...] | --ip-version=IP_VERSION]
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[NAME ...]
   Names of the addresses to create.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional textual description for the addresses. |
| `--endpoint-type` | one of: VM, NETLB |  | The endpoint type of the external IPv6 address to be reserved. ENDPOINT_TYPE must be one of: VM, NETLB. |
| `--ip-collection` | IP_COLLECTION |  | If specified, the public delegated prefix (PDP) from which to allocate the BYOIP IP address. The PDP must support enhanced IPv4 allocations. If not specified, the address will be allocated from the Google-owned IP pool. |
| `--network` | NETWORK |  | If specified, the network resource in which the address(es) should be reserved. This is only available for global internal address, which represents an internal IP range reservation from within the network. |
| `--network-tier` | one of: PREMIUM, STANDARD |  | The network tier to assign to the reserved IP addresses. NETWORK_TIER must be one of: PREMIUM, STANDARD. The default value is PREMIUM. While regional external addresses (--region specified, --subnet omitted) can use either PREMIUM or STANDARD, global external addresses (--global specified, --subnet omitted) can only use PREMIUM. Internal addresses can only use PREMIUM. |
| `--prefix-length` | PREFIX_LENGTH |  | The prefix length of the IP range. If the address is an IPv4 address, it must be a value between 8 and 30 inclusive. If the address is an IPv6 address, the only allowed value is 96. If not present, it means the address field is a single IP address. This field is not applicable to external IPv4 addresses or global IPv6 addresses. |
| `--purpose` | one of: VPC_PEERING, SHARED_LOADBALANCER_VIP, GCE_ENDPOINT, IPSEC_INTERCONNECT, PRIVATE_SERVICE_CONNECT |  | The purpose of the address resource. This field is not applicable to external addresses. PURPOSE must be one of: VPC_PEERING, SHARED_LOADBALANCER_VIP, GCE_ENDPOINT, IPSEC_INTERCONNECT, PRIVATE_SERVICE_CONNECT. |
| `--subnet` | SUBNET |  | If specified, the subnet name in which the address(es) should be reserved. The subnet must be in the same region as the address. The address will represent an internal IP reservation from within the subnet. If --address is specified, it must be within the subnet's IP range. May not be specified with --global. |


**Examples:**
```bash
To reserve three IP addresses in the 'us-central1' region, run:

    $ gcloud compute addresses create address-1 address-2 address-3 \
        --region=us-central1

To reserve ephemeral IP addresses '162.222.181.198' and '23.251.146.189'
which are being used by virtual machine instances in the 'us-central1'
region, run:

    $ gcloud compute addresses create \
        --addresses=162.222.181.198,23.251.146.189 --region=us-central1

In the above invocation, the two addresses will be assigned random names.

To reserve an IP address named subnet-address-1 from the subnet 'default'
in the 'us-central1' region, run:

    $ gcloud compute addresses create subnet-address-1 \
        --region=us-central1 --subnet=default

To reserve an IP range '10.110.0.0/16' from the network 'default' for
'VPC_PEERING', run:

    $ gcloud compute addresses create ip-range-1 --global \
        --addresses=10.110.0.0 --prefix-length=16 \
        --purpose=VPC_PEERING --network=default

To reserve any IP range with prefix length '16' from the network 'default'
for 'VPC_PEERING', run:

    $ gcloud compute addresses create ip-range-1 --global \
        --prefix-length=16 --purpose=VPC_PEERING --network=default

To reserve an address from network 'default' for PRIVATE_SERVICE_CONNECT,
run:

    $ gcloud compute addresses create psc-address-1 --global \
        --addresses=10.110.0.10 --purpose=PRIVATE_SERVICE_CONNECT \
        --network=default
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/addresses/create)

---
### `gcloud compute addresses delete`

Release reserved IP addresses

gcloud compute addresses delete releases one or more Compute Engine IP
addresses.

**Synopsis:**
```
gcloud compute addresses delete NAME [NAME ...]
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME [NAME ...]
   Names of the addresses to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the addresses are global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the addresses to delete. Overrides the default compute/region property value for this command invocation. |


**Examples:**
```bash
To release an address with the name 'address-name', run:

    $ gcloud compute addresses delete address-name

To release two addresses with the names 'address-name1' and
'address-name2', run:

    $ gcloud compute addresses delete address-name1 address-name2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/addresses/delete)

---
### `gcloud compute addresses describe`

Display detailed information about a reserved static address

gcloud compute addresses describe displays all data associated with a
reserved static address in a project.

**Synopsis:**
```
gcloud compute addresses describe NAME [--global | --region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the address to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the address is global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the address to describe. Overrides the default compute/region property value for this command invocation. |


**Examples:**
```bash
To get details about a global address, run:

    $ gcloud compute addresses describe my-address-name --global

To get details about a regional address, run:

    $ gcloud compute addresses describe my-address-name \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/addresses/describe)

---
### `gcloud compute addresses list`

List addresses

gcloud compute addresses list lists summary information of addresses in a
project. The --uri option can be used to display URIs instead. Users who
want to see more data should use gcloud compute addresses describe.

By default, global addresses and addresses from all regions are listed. The
results can be narrowed down by providing the --regions or --global flag.

**Synopsis:**
```
gcloud compute addresses list [NAME ...] [--regexp=REGEXP, -r REGEXP]
    [--global | --regions=[REGION,...]] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[NAME ...]
   (DEPRECATED) If provided, show details for the specified names and/or
   URIs of resources.

   Argument NAME is deprecated. Use --filter="name=( 'NAME' ... )"
   instead.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--regexp` | REGEXP, -r REGEXP |  | (DEPRECATED) Regular expression to filter the names of the results on. Any names that do not match the entire regular expression will be filtered out. Flag --regexp is deprecated. Use --filter="name~'REGEXP'" instead. |


**Examples:**
```bash
To list all addresses in a project in table form, run:

    $ gcloud compute addresses list

To list the URIs of all addresses in a project, run:

    $ gcloud compute addresses list --uri

To list all of the global addresses in a project, run:

    $ gcloud compute addresses list --global

To list all of the addresses from the us-central1 region, run:

    $ gcloud compute addresses list --filter=region:us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/addresses/list)

---
### `gcloud compute addresses move`

Move an address to another project

**Synopsis:**
```
gcloud compute addresses move NAME --target-project=TARGET_PROJECT
    [--description=DESCRIPTION] [--new-name=NEW_NAME]
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the address to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--target-project` | TARGET_PROJECT |  | The target project to move address to. It can be either a project name or a project numerical ID. It must not be the same as the current project. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description of moved new address. |
| `--new-name` | NEW_NAME |  | Name of moved new address. If not specified, current address's name is used. |


**Examples:**
```bash
The following command moves address external-ip1 in region us-central1 to
project test-playground with new address name test-ip1:

    $ gcloud compute addresses move external-ip1 --new-name=test-ip1 \
       --target-project=test-playground --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/addresses/move)

---
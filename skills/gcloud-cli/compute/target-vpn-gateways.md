# gcloud compute target-vpn-gateways

read and manipulate classic VPN gateways

### `gcloud compute target-vpn-gateways create`

Create a Cloud VPN Classic Target VPN Gateway

gcloud compute target-vpn-gateways create is used to create a Cloud VPN
Classic Target VPN Gateway. A Target VPN Gateway can reference one or more
VPN tunnels that connect it to the remote tunnel endpoint. A Target VPN
Gateway may also be referenced by one or more forwarding rules that define
which packets the gateway is responsible for routing.

**Synopsis:**
```
gcloud compute target-vpn-gateways create NAME --network=NETWORK
    [--description=DESCRIPTION] [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the Target VPN Gateway to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--network` | NETWORK |  | A reference to a network in this project to contain the VPN Gateway. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional, textual description for the target VPN Gateway. |
| `--region` | REGION |  | Region of the Target VPN Gateway to create. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-vpn-gateways/create)

---
### `gcloud compute target-vpn-gateways delete`

Delete Cloud VPN Classic Target VPN Gateways

gcloud compute target-vpn-gateways delete deletes one or more Compute
Engine Cloud VPN Classic Target VPN Gateways.

**Synopsis:**
```
gcloud compute target-vpn-gateways delete NAME [NAME ...] [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME [NAME ...]
   Names of the Target VPN Gateways to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the Target VPN Gateways to delete. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-vpn-gateways/delete)

---
### `gcloud compute target-vpn-gateways describe`

Describe a Compute Engine Cloud VPN Classic Target VPN Gateway

gcloud compute target-vpn-gateways describe displays all data associated
with a Compute Engine Cloud VPN Target VPN Gateway in a project.

**Synopsis:**
```
gcloud compute target-vpn-gateways describe NAME [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the Target VPN Gateway to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the Target VPN Gateway to describe. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-vpn-gateways/describe)

---
### `gcloud compute target-vpn-gateways list`

List Google Compute Engine Cloud VPN Classic Target VPN Gateways

gcloud compute target-vpn-gateways list displays all Google Compute Engine
Cloud VPN Classic Target VPN Gateways in a project.

By default, Cloud VPN Classic Target VPN Gateways from all regions are
listed. The results can be narrowed down using a filter: --filter="region:(
REGION ... )".

**Synopsis:**
```
gcloud compute target-vpn-gateways list [NAME ...]
    [--regexp=REGEXP, -r REGEXP] [--regions=REGION,[REGION,...]]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
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
| `--regions` | REGION,[REGION,...] |  | If provided, only resources from the given regions are queried. |


**Examples:**
```bash
To list all Cloud VPN Classic Target VPN Gateways in a project in table
form, run:

    $ gcloud compute target-vpn-gateways list

To list the URIs of all Cloud VPN Classic Target VPN Gateways in a project,
run:

    $ gcloud compute target-vpn-gateways list --uri

To list all Cloud VPN Classic Target VPN Gateways in the us-central1 and
europe-west1 regions, run:

    $ gcloud compute target-vpn-gateways list \
        --filter="region:( us-central1 europe-west1 )"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-vpn-gateways/list)

---
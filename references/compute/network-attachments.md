# gcloud compute network-attachments

manage Compute Engine network attachment resources

### `gcloud compute network-attachments create`

Create a Google Compute Engine network attachment

gcloud compute network-attachments create is used to create network
attachments. A service consumer creates network attachments and makes it
available to producers. Service producers then use a multi-NIC VM to form a
bi-directional, non-NAT'd communication channel.

**Synopsis:**
```
gcloud compute network-attachments create NAME
    --subnets=SUBNETS,[SUBNETS,...]
    [--connection-preference=CONNECTION_PREFERENCE;
      default="ACCEPT_AUTOMATIC"] [--description=DESCRIPTION]
    [--producer-accept-list=[ACCEPT_LIST,...]]
    [--producer-reject-list=[REJECT_LIST,...]] [--region=REGION]
    [--subnets-region=SUBNETS_REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the network attachment to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--subnets` | SUBNETS,[SUBNETS,...] |  | The subnetworks provided by the consumer for the producers |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--connection-preference` | one of: ACCEPT_AUTOMATIC, ACCEPT_MANUAL | ACCEPT_AUTOMATIC | The connection preference of network attachment. The value can be set to ACCEPT_AUTOMATIC or ACCEPT_MANUAL. An ACCEPT_AUTOMATIC network attachment is one that always accepts the connection from producer NIC. An ACCEPT_MANUAL network attachment is one that requires an explicit addition of the producer project id or project number to the producer accept list. CONNECTION_PREFERENCE must be one of: ACCEPT_AUTOMATIC, ACCEPT_MANUAL. |
| `--description` | DESCRIPTION |  | An optional, textual description for the network attachment. |
| `--producer-accept-list` | [ACCEPT_LIST,...] |  | Projects that are allowed to connect to this network attachment. |
| `--producer-reject-list` | [REJECT_LIST,...] |  | Projects that are not allowed to connect to this network attachment. |
| `--region` | REGION |  | Region of the network attachment to create. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--subnets-region` | SUBNETS_REGION |  | Region of the subnetworks to operate on. Overrides the default compute/region property value for this command invocation. |


**Examples:**
```bash
    $ gcloud compute network-attachments create \
        NETWORK_ATTACHMENT_NAME --region=us-central1 \
        --subnets=MY_SUBNET --connection-preference=ACCEPT_MANUAL \
        --producer-accept-list=PROJECT1,PROJECT2 \
        --producer-reject-list=PROJECT3,PROJECT4

To create a network attachment with a textual description, run:

    $ gcloud compute network-attachments create \
        NETWORK_ATTACHMENT_NAME --region=us-central1 \
        --subnets=MY_SUBNET --connection-preference=ACCEPT_MANUAL \
        --producer-accept-list=PROJECT1,PROJECT2 \
        --producer-reject-list=PROJECT3,PROJECT4 \
        --description='default network attachment'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/network-attachments/create)

---
### `gcloud compute network-attachments delete`

Delete one or more Google Compute Engine network attachments

Delete one or more Google Compute Engine network attachments.

**Synopsis:**
```
gcloud compute network-attachments delete NAME [NAME ...] [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME [NAME ...]
   Names of the network attachments to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the network attachments to delete. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To delete a network attachment, run:

    $ gcloud compute network-attachments delete \
      NETWORK_ATTACHMENT_NAME --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/network-attachments/delete)

---
### `gcloud compute network-attachments describe`

Describes a Google Compute Engine network attachment

Describes a Google Compute Engine network attachment.

**Synopsis:**
```
gcloud compute network-attachments describe NAME [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the network attachment to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the network attachment to describe. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To describe a network attachment, run:

    $ gcloud compute network-attachments describe \
      NETWORK_ATTACHMENT_NAME --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/network-attachments/describe)

---
### `gcloud compute network-attachments list`

List Google Compute Engine network attachments

List Google Compute Engine network attachments.

**Synopsis:**
```
gcloud compute network-attachments list [NAME ...]
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
To list all the network attachments, run:

    $ gcloud compute network-attachments list

To list the network attachments in given region(s), run:

    $ gcloud compute network-attachments list --regions=region-1,region-2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/network-attachments/list)

---
### `gcloud compute network-attachments update`

Update a Google Compute Engine network attachment

gcloud compute network-attachments update is used to update network
attachments. You can update the following fields: description, subnets,
producer-accept-list and producer-reject-list. If you update the
producer-accept-list or producer-reject-list, the full new list should be
specified.

**Synopsis:**
```
gcloud compute network-attachments update NAME [--description=DESCRIPTION]
    [--producer-accept-list=[ACCEPT_LIST,...]]
    [--producer-reject-list=[REJECT_LIST,...]] [--region=REGION]
    [--subnets=SUBNETS,[SUBNETS,...]] [--subnets-region=SUBNETS_REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the network attachment to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional, textual description for the network attachment. |
| `--producer-accept-list` | [ACCEPT_LIST,...] |  | Projects that are allowed to connect to this network attachment. |
| `--producer-reject-list` | [REJECT_LIST,...] |  | Projects that are not allowed to connect to this network attachment. |
| `--region` | REGION |  | Region of the network attachment to update. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--subnets` | SUBNETS,[SUBNETS,...] |  | The subnetworks provided by the consumer for the producers |
| `--subnets-region` | SUBNETS_REGION |  | Region of the subnetworks to operate on. Overrides the default compute/region property value for this command invocation. |


**Examples:**
```bash
To update all the parameters with the new list, run:

    $ gcloud compute network-attachments update \
        NETWORK_ATTACHMENT_NAME --region=us-central1 \
        --subnets=MY_SUBNET2 \
        --description='default network attachment' \
        --producer-accept-list=PROJECT5,PROJECT6 \
        --producer-reject-list=PROJECT7,PROJECT8

To update a network attachment to change only the subnet to MY_SUBNET3,
run:

    $ gcloud compute network-attachments update \
        NETWORK_ATTACHMENT_NAME --region=us-central1 \
        --subnets=MY_SUBNET3
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/network-attachments/update)

---
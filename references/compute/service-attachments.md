# gcloud compute service-attachments

manage Compute Engine service attachment resources

### `gcloud compute service-attachments create`

Create a Google Compute Engine service attachment

gcloud compute service-attachments create is used to create service
attachments. A service producer creates service attachments to make a
service available to consumers. Service consumers use Private Service
Connect endpoints to privately forward traffic to the service attachment.

**Synopsis:**
```
gcloud compute service-attachments create NAME
    --nat-subnets=NAT_SUBNETS,[NAT_SUBNETS,...]
    (--producer-forwarding-rule=PRODUCER_FORWARDING_RULE
      | --target-service=TARGET_SERVICE)
    [--connection-preference=CONNECTION_PREFERENCE;
      default="ACCEPT_AUTOMATIC"]
    [--consumer-accept-list=[PROJECT_OR_NETWORK=LIMIT,...]]
    [--consumer-reject-list=[REJECT_LIST,...]] [--description=DESCRIPTION]
    [--domain-names=[DOMAIN_NAMES,...]] [--enable-proxy-protocol]
    [--nat-subnets-region=NAT_SUBNETS_REGION]
    [--propagated-connection-limit=PROPAGATED_CONNECTION_LIMIT]
    [--reconcile-connections] [--region=REGION]
    [--global-producer-forwarding-rule
      | --producer-forwarding-rule-region=PRODUCER_FORWARDING_RULE_REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the service attachment to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--nat-subnets` | NAT_SUBNETS,[NAT_SUBNETS,...] |  | The subnetworks provided by service producer to use for NAT |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--connection-preference` | one of: ACCEPT_AUTOMATIC Always accept connection requests from consumers automatically | ACCEPT_AUTOMATIC | This defines the service attachment's connection preference. CONNECTION_PREFERENCE must be one of: ACCEPT_AUTOMATIC Always accept connection requests from consumers automatically. ACCEPT_MANUAL Only accept connection requests from consumers with the approval of the service provider. |
| `--consumer-accept-list` | [PROJECT_OR_NETWORK=LIMIT,...] |  | Specifies which consumer projects or networks are allowed to connect to the service attachment. Each project or network has a connection limit. A given service attachment can manage connections at either the project or network level. Therefore, both the accept and reject lists for a given service attachment must contain either only projects or only networks. For example, --consumer-accept-list myProjectId1=20 accepts a consumer project myProjectId1 with connection limit 20; --consumer-accept-list projects/myProjectId1/global/networks/myNet1=20 accepts a consumer network myNet1 with connection limit 20 * PROJECT_OR_NETWORK - Consumer project ID, project number or network URL. * CONNECTION_LIMIT - The maximum number of allowed connections. |
| `--consumer-reject-list` | [REJECT_LIST,...] |  | Specifies a comma separated list of projects or networks that are not allowed to connect to this service attachment. The project can be specified using its project ID or project number and the network can be specified using its URL. A given service attachment can manage connections at either the project or network level. Therefore, both the reject and accept lists for a given service attachment must contain either only projects or only networks. |
| `--description` | DESCRIPTION |  | An optional, textual description for the service attachment. |
| `--domain-names` | [DOMAIN_NAMES,...] |  | Specifies a comma separated list of DNS domain names that are used during DNS integration on PSC connected endpoints. |
| `--enable-proxy-protocol` |  |  | If True, then enable the proxy protocol which is for supplying client TCP/IP address data in TCP connections that traverse proxies on their way to destination servers. |
| `--nat-subnets-region` | NAT_SUBNETS_REGION |  | Region of the subnetworks to operate on. If not specified, it will be set to the region of the service attachment. Overrides the default compute/region property value for this command invocation. |
| `--propagated-connection-limit` | PROPAGATED_CONNECTION_LIMIT |  | The number of consumer spokes that connected Private Service Connect endpoints can be propagated to through Network Connectivity Center. This limit lets the service producer limit how many propagated Private Service Connect connections can be established to this service attachment from a single consumer. If the connection preference of the service attachment is ACCEPT_MANUAL, the limit applies to each project or network that is listed in the consumer accept list. If the connection preference of the service attachment is ACCEPT_AUTOMATIC, the limit applies to each project that contains a connected endpoint. If unspecified, the default propagated connection limit is 250. |
| `--reconcile-connections` |  |  | Determines whether to apply changes to consumer accept or reject lists to existing connections or only to new connections. If false, existing endpoints with a connection status of ACCEPTED or REJECTED are not updated. If true, existing endpoints with a connection status of ACCEPTED or REJECTED are updated based on the connection policy update. For example, if a project or network is removed from the --consumer-accept-list and added to --consumer-reject-list, all the endpoints in that project or network with the ACCEPTED state are set to REJECTED. |
| `--region` | REGION |  | Region of the service attachment to create. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
If there is an already-created internal load balancer (ILB) with the name
MY_ILB in region us-central1 and there is an already-created Private
Service Connect subnets MY_SUBNET1 and MY_SUBNET2, create a service
attachment pointing to the ILB by running:

    $ gcloud compute service-attachments create \
        SERVICE_ATTACHMENT_NAME --region=us-central1 \
        --producer-forwarding-rule=MY_ILB \
        --connection-preference=ACCEPT_AUTOMATIC \
        --nat-subnets=MY_SUBNET1,MY_SUBNET2

To create a service attachment with a textual description, run:

    $ gcloud compute service-attachments create \
        SERVICE_ATTACHMENT_NAME --region=us-central1 \
        --producer-forwarding-rule=MY_ILB \
        --connection-preference=ACCEPT_AUTOMATIC \
        --nat-subnets=MY_SUBNET1,MY_SUBNET2 \
        --description='default service attachment'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/service-attachments/create)

---
### `gcloud compute service-attachments delete`

Delete one or more Google Compute Engine service attachments

Delete one or more Google Compute Engine service attachments.

**Synopsis:**
```
gcloud compute service-attachments delete NAME [NAME ...] [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME [NAME ...]
   Names of the service attachments to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the service attachments to delete. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To delete a service attachment, run:

    $ gcloud compute service-attachments delete \
      SERVICE_ATTACHMENT_NAME --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/service-attachments/delete)

---
### `gcloud compute service-attachments describe`

Display details about a Google Compute Engine service attachment

Display details about a Google Compute Engine service attachment.

**Synopsis:**
```
gcloud compute service-attachments describe NAME [--region=REGION]
    [--show-nat-ips] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the service attachment to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the service attachment to describe. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--show-nat-ips` |  |  | Determines whether to include the NAT IPs of connected endpoints in the service attachment output. If enabled (--show-nat-ips), the output will include the list of NAT IPs for each connected PSC endpoint and any endpoints propagated from them. |


**Examples:**
```bash
To describe a service attachment, run:

    $ gcloud compute service-attachments describe \
      SERVICE_ATTACHMENT_NAME --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/service-attachments/describe)

---
### `gcloud compute service-attachments list`

List Google Compute Engine service attachments

gcloud compute service-attachments list displays all Google Compute Engine
service attachments in a project.

By default, service attachments from all regions are listed. The results
can be narrowed down using a filter: --filter="region:( REGION ... )".

**Synopsis:**
```
gcloud compute service-attachments list [NAME ...]
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
To list all service attachments in a project in table form, run:

    $ gcloud compute service-attachments list

To list the URIs of all service attachments in a project, run:

    $ gcloud compute service-attachments list --uri

To list all service attachments in the us-central1 and europe-west1
regions, run:

    $ gcloud compute service-attachments list \
        --filter="region:( us-central1 europe-west1 )"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/service-attachments/list)

---
### `gcloud compute service-attachments update`

Update a Google Compute Engine service attachment

gcloud compute service-attachments update is used to update service
attachments. A service producer creates service attachments to make a
service available to consumers. Service consumers use Private Service
Connect endpoints to privately forward traffic to the service attachment.

**Synopsis:**
```
gcloud compute service-attachments update NAME
    [--connection-preference=CONNECTION_PREFERENCE]
    [--consumer-accept-list=[PROJECT_OR_NETWORK=LIMIT,...]]
    [--consumer-reject-list=[REJECT_LIST,...]] [--description=DESCRIPTION]
    [--[no-]enable-proxy-protocol]
    [--nat-subnets=NAT_SUBNETS,[NAT_SUBNETS,...]]
    [--nat-subnets-region=NAT_SUBNETS_REGION]
    [--propagated-connection-limit=PROPAGATED_CONNECTION_LIMIT]
    [--[no-]reconcile-connections] [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the service attachment to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--connection-preference` | one of: ACCEPT_AUTOMATIC Always accept connection requests from consumers automatically |  | This defines the service attachment's connection preference. CONNECTION_PREFERENCE must be one of: ACCEPT_AUTOMATIC Always accept connection requests from consumers automatically. ACCEPT_MANUAL Only accept connection requests from consumers with the approval of the service provider. |
| `--consumer-accept-list` | [PROJECT_OR_NETWORK=LIMIT,...] |  | Specifies which consumer projects or networks are allowed to connect to the service attachment. Each project or network has a connection limit. A given service attachment can manage connections at either the project or network level. Therefore, both the accept and reject lists for a given service attachment must contain either only projects or only networks. For example, --consumer-accept-list myProjectId1=20 accepts a consumer project myProjectId1 with connection limit 20; --consumer-accept-list projects/myProjectId1/global/networks/myNet1=20 accepts a consumer network myNet1 with connection limit 20 * PROJECT_OR_NETWORK - Consumer project ID, project number or network URL. * CONNECTION_LIMIT - The maximum number of allowed connections. |
| `--consumer-reject-list` | [REJECT_LIST,...] |  | Specifies a comma separated list of projects or networks that are not allowed to connect to this service attachment. The project can be specified using its project ID or project number and the network can be specified using its URL. A given service attachment can manage connections at either the project or network level. Therefore, both the reject and accept lists for a given service attachment must contain either only projects or only networks. |
| `--description` | DESCRIPTION |  | An optional, textual description for the service attachment. |
| `--[no-]enable-proxy-protocol` |  |  | If True, then enable the proxy protocol which is for supplying client TCP/IP address data in TCP connections that traverse proxies on their way to destination servers. Use --enable-proxy-protocol to enable and --no-enable-proxy-protocol to disable. |
| `--nat-subnets` | NAT_SUBNETS,[NAT_SUBNETS,...] |  | The subnetworks provided by service producer to use for NAT |
| `--nat-subnets-region` | NAT_SUBNETS_REGION |  | Region of the subnetworks to operate on. If not specified, it will be set to the region of the service attachment. Overrides the default compute/region property value for this command invocation. |
| `--propagated-connection-limit` | PROPAGATED_CONNECTION_LIMIT |  | The number of consumer spokes that connected Private Service Connect endpoints can be propagated to through Network Connectivity Center. This limit lets the service producer limit how many propagated Private Service Connect connections can be established to this service attachment from a single consumer. If the connection preference of the service attachment is ACCEPT_MANUAL, the limit applies to each project or network that is listed in the consumer accept list. If the connection preference of the service attachment is ACCEPT_AUTOMATIC, the limit applies to each project that contains a connected endpoint. If unspecified, the default propagated connection limit is 250. |
| `--[no-]reconcile-connections` |  |  | Determines whether to apply changes to consumer accept or reject lists to existing connections or only to new connections. If false, existing endpoints with a connection status of ACCEPTED or REJECTED are not updated. If true, existing endpoints with a connection status of ACCEPTED or REJECTED are updated based on the connection policy update. For example, if a project or network is removed from the --consumer-accept-list and added to --consumer-reject-list, all the endpoints in that project or network with the ACCEPTED state are set to REJECTED. Use --reconcile-connections to enable and --no-reconcile-connections to disable. |
| `--region` | REGION |  | Region of the service attachment to update. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To update the connection policy of a service attachment to be
ACCEPT_MANUAL, run:

    $ gcloud compute service-attachments update \
        SERVICE_ATTACHMENT_NAME --region=us-central1 \
        --connection-preference=ACCEPT_MANUAL

To update all supported fields of a service attachment, run:

    $ gcloud compute service-attachments update \
        SERVICE_ATTACHMENT_NAME --region=us-central1 \
        --connection-preference=ACCEPT_AUTOMATIC \
        --nat-subnets=MY_SUBNET1,MY_SUBNET2 --enable-proxy-protocol \
        --consumer-reject-list=PROJECT_ID1,PROJECT_ID2 \
        --consumer-accept-list=PROJECT_ID3=10,PROJECT_ID4=20
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/service-attachments/update)

---
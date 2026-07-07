# gcloud ai index-endpoints

manage Vertex AI index endpoints

### `gcloud ai index-endpoints create`

Create a new Vertex AI index endpoint

**Synopsis:**
```
gcloud ai index-endpoints create --display-name=DISPLAY_NAME
    [--description=DESCRIPTION] [--enable-private-service-connect]
    [--encryption-kms-key-name=ENCRYPTION_KMS_KEY_NAME]
    [--labels=[KEY=VALUE,...]] [--network=NETWORK]
    [--project-allowlist=[PROJECTS,...]] [--public-endpoint-enabled]
    [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | Display name of the index endpoint. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description of the index endpoint. |
| `--enable-private-service-connect` |  |  | If true, expose the index endpoint via private service connect. |
| `--encryption-kms-key-name` | ENCRYPTION_KMS_KEY_NAME |  | The Cloud KMS resource identifier of the customer managed encryption key used to protect a resource. Has the form: projects/my-project/locations/my-region/keyRings/my-kr/cryptoKeys/my-key. The key needs to be in the same region as where the compute resource is created. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--network` | NETWORK |  | The Google Compute Engine network name to which the IndexEndpoint should be peered. |
| `--project-allowlist` | [PROJECTS,...] |  | List of projects from which the forwarding rule will target the service attachment. |
| `--public-endpoint-enabled` |  |  | If true, the deployed index will be accessible through public endpoint. |


**Examples:**
```bash
To create an index endpoint under project example with network
projects/123/global/networks/test-network in region us-central1, run:

    $ gcloud ai index-endpoints create --display-name=index-endpoint \
        --description=test \
        --network=projects/123/global/networks/test-network \
        --project=example --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/index-endpoints/create)

---
### `gcloud ai index-endpoints delete`

Delete an existing Vertex AI index endpoint

**Synopsis:**
```
gcloud ai index-endpoints delete (INDEX_ENDPOINT : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Index endpoint resource - The index endpoint to delete. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument index_endpoint on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INDEX_ENDPOINT
     ID of the index_endpoint or fully qualified identifier for the
     index_endpoint.

     To set the name attribute:
     + provide the argument index_endpoint on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the index_endpoint.

     To set the region attribute:
     + provide the argument index_endpoint on the command line with a
       fully specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Examples:**
```bash
To delete an index endpoint 123 of project example in region us-central1,
run:

    $ gcloud ai index-endpoints delete 123 --project=example \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/index-endpoints/delete)

---
### `gcloud ai index-endpoints deploy-index`

Deploy an index to a Vertex AI index endpoint

Deploy an index to a Vertex AI index endpoint.

**Synopsis:**
```
gcloud ai index-endpoints deploy-index (INDEX_ENDPOINT : --region=REGION)
    --deployed-index-id=DEPLOYED_INDEX_ID --display-name=DISPLAY_NAME
    --index=INDEX [--allowed-issuers=[ALLOWED_ISSUERS,...]]
    [--audiences=[AUDIENCES,...]] [--deployment-group=DEPLOYMENT_GROUP]
    [--deployment-tier=DEPLOYMENT_TIER] [--enable-access-logging]
    [--machine-type=MACHINE_TYPE] [--max-replica-count=MAX_REPLICA_COUNT]
    [--min-replica-count=MIN_REPLICA_COUNT]
    [--psc-automation-configs=[network=NETWORK],[project-id=PROJECT-ID]]
    [--reserved-ip-ranges=[RESERVED_IP_RANGES,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Index endpoint resource - The index endpoint to deploy an index. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument index_endpoint on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INDEX_ENDPOINT
     ID of the index_endpoint or fully qualified identifier for the
     index_endpoint.

     To set the name attribute:
     + provide the argument index_endpoint on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the index_endpoint.

     To set the region attribute:
     + provide the argument index_endpoint on the command line with a
       fully specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--deployed-index-id` | DEPLOYED_INDEX_ID |  | Id of the deployed index. |
| `--display-name` | DISPLAY_NAME |  | Display name of the deployed index. |
| `--index` | INDEX |  | ID of the index. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allowed-issuers` | [ALLOWED_ISSUERS,...] |  | List of allowed JWT issuers for a deployed index. Each entry must be a valid Google service account, in the following format: service-account-name@project-id.iam.gserviceaccount.com |
| `--audiences` | [AUDIENCES,...] |  | List of JWT audiences that are allowed to access a deployed index. JWT containing any of these audiences (https://tools.ietf.org/html/draft-ietf-oauth-json-web-token-32#section -4.1.3) will be accepted. |
| `--deployment-group` | DEPLOYMENT_GROUP |  | Deployment group can be no longer than 64 characters (eg:test, prod). If not set, we will use the default deployment group. Creating deployment_groups with reserved_ip_ranges is a recommended practice when the peered network has multiple peering ranges.This creates your deployments from predictable IP spaces for easier traffic administration. |
| `--deployment-tier` | DEPLOYMENT_TIER |  | The deployment tier that the deployed index is deployed to. If not specified, a system-chosen default tier is used. DEPLOYMENT_TIER must be (only one value is supported): storage. |
| `--enable-access-logging` |  |  | If true, online prediction access logs are sent to Cloud Logging. These logs are standard server access logs, containing information like timestamp and latency for each prediction request. |
| `--machine-type` | MACHINE_TYPE |  | The machine resources to be used for each node of this deployment. For available machine types, see https://cloud.google.com/ai-platform-unified/docs/predictions/machine-types. |
| `--max-replica-count` | MAX_REPLICA_COUNT |  | Maximum number of machine replicas the deployed index will be always deployed on. |
| `--min-replica-count` | MIN_REPLICA_COUNT |  | Minimum number of machine replicas the deployed index will be always deployed on. If specified, the value must be equal to or larger than 1. |
| `--psc-automation-configs` | [network=NETWORK],[project-id=PROJECT-ID] |  | A pair of project-id and network the PSC index will be deployed to. For example: --psc-automation-configs=project-id=my-project,network=my-network. For multiple networks, this flag can be repeated: --psc-automation-configs=project-id=my-project,network=my-network --psc-automation-configs=project-id=my-project2,network=my-network2 |
| `--reserved-ip-ranges` | [RESERVED_IP_RANGES,...] |  | List of reserved IP ranges deployed index will be deployed to. |


**Examples:**
```bash
To deploy index 345 to an index endpoint 456 with 2 min replica count and
10 max replica count under project example in region us-central1, within
reserved ip ranges vertex-ai-ip-range-1 and vertex-ai-ip-range-2 run:

    $ gcloud ai index-endpoints deploy-index 456 --project=example \
        --region=us-central1 --index=345 \
        --deployed-index-id=deployed-index-345 \
        --display-name=deployed-index-345 --min-replica-count=2 \
        --max-replica-count=10 \
        --reserved-ip-ranges=vertex-ai-ip-range-1,vertex-ai-ip-range-2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/index-endpoints/deploy-index)

---
### `gcloud ai index-endpoints describe`

Gets detailed index endpoint information about the given index endpoint id

**Synopsis:**
```
gcloud ai index-endpoints describe (INDEX_ENDPOINT : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Index endpoint resource - The index endpoint to describe. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument index_endpoint on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INDEX_ENDPOINT
     ID of the index_endpoint or fully qualified identifier for the
     index_endpoint.

     To set the name attribute:
     + provide the argument index_endpoint on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the index_endpoint.

     To set the region attribute:
     + provide the argument index_endpoint on the command line with a
       fully specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Examples:**
```bash
Describe an index endpoint 123 of project example in region us-central1,
run:

    $ gcloud ai index-endpoints describe 123 --project=example \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/index-endpoints/describe)

---
### `gcloud ai index-endpoints list`

Lists the index endpoints of the given project and region

**Synopsis:**
```
gcloud ai index-endpoints list [--region=REGION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[* set the property core/project.]_ ID of the region or fully qualified identifier for the region. To set the region attribute: + provide the argument --region on the command line; + set the property ai/region; + choose one from the prompted list of available regions. |


**Examples:**
```bash
Lists the index endpoints of project example in region us-central1, run:

    $ gcloud ai index-endpoints list --project=example \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/index-endpoints/list)

---
### `gcloud ai index-endpoints mutate-deployed-index`

Mutate an existing deployed index from a Vertex AI index endpoint

Mutate an existing deployed index from a Vertex AI index endpoint.

**Synopsis:**
```
gcloud ai index-endpoints mutate-deployed-index
    (INDEX_ENDPOINT : --region=REGION)
    --deployed-index-id=DEPLOYED_INDEX_ID
    [--allowed-issuers=[ALLOWED_ISSUERS,...]] [--audiences=[AUDIENCES,...]]
    [--deployment-group=DEPLOYMENT_GROUP] [--enable-access-logging]
    [--machine-type=MACHINE_TYPE] [--max-replica-count=MAX_REPLICA_COUNT]
    [--min-replica-count=MIN_REPLICA_COUNT]
    [--reserved-ip-ranges=[RESERVED_IP_RANGES,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Index endpoint resource - The index endpoint ID of the index endpoint..
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument index_endpoint on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INDEX_ENDPOINT
     ID of the index_endpoint or fully qualified identifier for the
     index_endpoint.

     To set the name attribute:
     + provide the argument index_endpoint on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the index_endpoint.

     To set the region attribute:
     + provide the argument index_endpoint on the command line with a
       fully specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--deployed-index-id` | DEPLOYED_INDEX_ID |  | Id of the deployed index. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allowed-issuers` | [ALLOWED_ISSUERS,...] |  | List of allowed JWT issuers for a deployed index. Each entry must be a valid Google service account, in the following format: service-account-name@project-id.iam.gserviceaccount.com |
| `--audiences` | [AUDIENCES,...] |  | List of JWT audiences that are allowed to access a deployed index. JWT containing any of these audiences (https://tools.ietf.org/html/draft-ietf-oauth-json-web-token-32#section -4.1.3) will be accepted. |
| `--deployment-group` | DEPLOYMENT_GROUP |  | Deployment group can be no longer than 64 characters (eg:test, prod). If not set, we will use the default deployment group. Creating deployment_groups with reserved_ip_ranges is a recommended practice when the peered network has multiple peering ranges.This creates your deployments from predictable IP spaces for easier traffic administration. |
| `--enable-access-logging` |  |  | If true, online prediction access logs are sent to Cloud Logging. These logs are standard server access logs, containing information like timestamp and latency for each prediction request. |
| `--machine-type` | MACHINE_TYPE |  | The machine resources to be used for each node of this deployment. For available machine types, see https://cloud.google.com/ai-platform-unified/docs/predictions/machine-types. |
| `--max-replica-count` | MAX_REPLICA_COUNT |  | Maximum number of machine replicas the deployed index will be always deployed on. |
| `--min-replica-count` | MIN_REPLICA_COUNT |  | Minimum number of machine replicas the deployed index will be always deployed on. If specified, the value must be equal to or larger than 1. |
| `--reserved-ip-ranges` | [RESERVED_IP_RANGES,...] |  | List of reserved IP ranges deployed index will be deployed to. |


**Examples:**
```bash
To mutated a deployed index deployed-index-123 from an index endpoint 456
with 2 min replica count and 10 max replica count under project example in
region us-central1, within vertex-ai-ip-ranges-1 and vertex-ai-ip-ranges-2,
within deployment group test, enabling access logging, with JWT audiences
aud1 and aud2, JWT issuers issuer1 and issuer2 run:

    $ gcloud ai index-endpoints mutate-deployed-index 456 \
        --project=example --region=us-central1 \
        --deployed-index-id=deployed-index-123 --min-replica-count=2 \
        --max-replica-count=10 \
        --reserved-ip-ranges=vertex-ai-ip-ranges-1,\
    vertex-ai-ip-ranges-2 --enable-access-logging \
        --audiences=aud1,aud2 --allowed-issuers=issuer1,issuer2 \
        --deployment-group=test
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/index-endpoints/mutate-deployed-index)

---
### `gcloud ai index-endpoints undeploy-index`

Undeploy an index from a Vertex AI index endpoint

**Synopsis:**
```
gcloud ai index-endpoints undeploy-index (INDEX_ENDPOINT : --region=REGION)
    --deployed-index-id=DEPLOYED_INDEX_ID [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Index endpoint resource - The index endpoint to undeploy an index. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument index_endpoint on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INDEX_ENDPOINT
     ID of the index_endpoint or fully qualified identifier for the
     index_endpoint.

     To set the name attribute:
     + provide the argument index_endpoint on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the index_endpoint.

     To set the region attribute:
     + provide the argument index_endpoint on the command line with a
       fully specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--deployed-index-id` | DEPLOYED_INDEX_ID |  | Id of the deployed index. |


**Examples:**
```bash
To undeploy the deployed-index deployed-index-345 from an index endpoint
456 under project example in region us-central1, run:

    $ gcloud ai index-endpoints undeploy-index 456 --project=example \
        --region=us-central1 --deployed-index-id=deployed-index-345
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/index-endpoints/undeploy-index)

---
### `gcloud ai index-endpoints update`

Update an Vertex AI index endpoint

**Synopsis:**
```
gcloud ai index-endpoints update (INDEX_ENDPOINT : --region=REGION)
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Index endpoint resource - The index endpoint to update. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument index_endpoint on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INDEX_ENDPOINT
     ID of the index_endpoint or fully qualified identifier for the
     index_endpoint.

     To set the name attribute:
     + provide the argument index_endpoint on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the index_endpoint.

     To set the region attribute:
     + provide the argument index_endpoint on the command line with a
       fully specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description of the index endpoint. |
| `--display-name` | DISPLAY_NAME |  | Display name of the index endpoint. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update display name of index endpoint 123 under project example in
region us-central1, run:

    $ gcloud ai index-endpoints update --display-name=new-name \
        --project=example --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/index-endpoints/update)

---
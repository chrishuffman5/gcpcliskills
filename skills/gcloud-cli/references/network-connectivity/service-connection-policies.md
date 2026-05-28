# gcloud network-connectivity service-connection-policies

manage Service Connection Policies

### `gcloud network-connectivity service-connection-policies create`

Create a new Service Connection Policy

Create a new Service Connection Policy with the given name.

**Synopsis:**
```
gcloud network-connectivity service-connection-policies create
    SERVICE_CONNECTION_POLICY --network=NETWORK
    --service-class=SERVICE_CLASS
    (--subnets=[SUBNETS,...]
      : --allowed-google-producers-resource-hierarchy-level=[ALLOWED_GOOGLE_PRODUCERS_RESOURCE_HIERARCHY_LEVEL,
      ...] --producer-instance-location=PRODUCER_INSTANCE_LOCATION
      --psc-connection-limit=PSC_CONNECTION_LIMIT) [--async]
    [--description=DESCRIPTION] [--labels=[KEY=VALUE,...]]
    [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service connection policy resource - Name of the Service Connection Policy
to be created. This represents a Cloud resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument service_connection_policy on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the region attribute:
 * provide the argument service_connection_policy on the command line
   with a fully specified name;
 * provide the argument --region on the command line.

This must be specified.

  SERVICE_CONNECTION_POLICY
     ID of the service connection policy or fully qualified identifier for
     the service connection policy.

     To set the service_connection_policy attribute:
     + provide the argument service_connection_policy on the command
       line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--network` | NETWORK |  | _[This must be specified.]_ ID of the network or fully qualified identifier for the network. To set the network attribute: + provide the argument --network on the command line. |
| `--service-class` | SERVICE_CLASS |  | _[This must be specified.]_ Service class that this policy is created for. E.g. my-service-class-ad32fa4b |
| `--allowed-google-producers-resource-hierarchy-level` | [ALLOWED_GOOGLE_PRODUCERS_RESOURCE_HIERARCHY_LEVEL,...] |  | _[- provide the argument --subnets on the command line.]_ List of projects, folders, or orgs where the producer instance can be located in the form "projects/123456789", folders/123456789", or "organizations/123456789". |
| `--producer-instance-location` | one of: custom-resource-hierarchy-levels The producer instance must be located in one of the values provided in the allowed-google-producers-resource-hierarchy-level flag |  | _[- provide the argument --subnets on the command line.]_ Option that determines where the producer instances can be located for which connections can be created in the network controlled by this policy. PRODUCER_INSTANCE_LOCATION must be one of: custom-resource-hierarchy-levels The producer instance must be located in one of the values provided in the allowed-google-producers-resource-hierarchy-level flag. none The producer instance must be within the same project as this connection policy. |
| `--psc-connection-limit` | PSC_CONNECTION_LIMIT |  | _[- provide the argument --subnets on the command line.]_ Max number of PSC connections for this policy. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Description of the Service Connection Policy to be created. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. |
| `--region` | REGION |  | For resources [service_connection_policy, subnets], provides fallback value for resource region attribute. When the resource's full URI path is not provided, region will fallback to this flag value. |


**Examples:**
```bash
Create a Service Connection Policy with name my-service-conn-policy for
network projects/my-project/global/networks/net1 and service class
my-service-class-ad32fa4b in region us-central1 using subnet
projects/my-project/regions/us-central1/subnetworks/subnet1 subject to
custom-resource-hierarchy-levels that allows connections from
Google-managed producer instances in projects/my-project.

    $ gcloud network-connectivity service-connection-policies create \
        my-service-conn-policy \
        --network="projects/my-project/global/networks/net1" \
        --service-class=my-service-class-ad32fa4b --region=us-central1 \
        --subnets=projects/my-project/regions/us-central1/subnetworks/\
    subnet1 --psc-connection-limit=100 \
        --producer-instance-location=custom-resource-hierarchy-levels \
        --allowed-google-producers-resource-hierarchy-level=projects/\
    my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/service-connection-policies/create)

---
### `gcloud network-connectivity service-connection-policies delete`

Delete a service connection policy

Delete the specified service connection policy.

**Synopsis:**
```
gcloud network-connectivity service-connection-policies delete
    (SERVICE_CONNECTION_POLICY : --region=REGION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service connection policy resource - Name of the Service Connection Policy
to be deleted. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument service_connection_policy on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE_CONNECTION_POLICY
     ID of the service connection policy or fully qualified identifier for
     the service connection policy.

     To set the service_connection_policy attribute:
     + provide the argument service_connection_policy on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The location Id.

     To set the region attribute:
     + provide the argument service_connection_policy on the command
       line with a fully specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a service connection policy with name pol1 in region us-central1,
run:

    $ gcloud network-connectivity service-connection-policies delete \
        pol1 --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/service-connection-policies/delete)

---
### `gcloud network-connectivity service-connection-policies describe`

Describe a service connection policy

Retrieve and display details about a service connection policy.

**Synopsis:**
```
gcloud network-connectivity service-connection-policies describe
    (SERVICE_CONNECTION_POLICY : --region=REGION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service connection policy resource - Name of the service connection policy
you want to describe. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument service_connection_policy on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE_CONNECTION_POLICY
     ID of the service connection policy or fully qualified identifier for
     the service connection policy.

     To set the service_connection_policy attribute:
     + provide the argument service_connection_policy on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The location Id.

     To set the region attribute:
     + provide the argument service_connection_policy on the command
       line with a fully specified name;
     + provide the argument --region on the command line.
```

**Examples:**
```bash
To display details about the service connection policy named pol1 in region
us-central1, run:

    $ gcloud network-connectivity service-connection-policies describe \
        pol1 --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/service-connection-policies/describe)

---
### `gcloud network-connectivity service-connection-policies list`

List service connection policies

Retrieve and display a list of all service connection policies in the
specified project.

**Synopsis:**
```
gcloud network-connectivity service-connection-policies list
    --region=REGION [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[This must be specified.]_ ID of the region or fully qualified identifier for the region. To set the region attribute: + provide the argument --region on the command line. |


**Examples:**
```bash
To list all service connection policies in region us-central1, run:

    $ gcloud network-connectivity service-connection-policies list \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/service-connection-policies/list)

---
### `gcloud network-connectivity service-connection-policies update`

Update a service connection policy

Update a Service Connection Policy with the given name.

**Synopsis:**
```
gcloud network-connectivity service-connection-policies update
    SERVICE_CONNECTION_POLICY
    [--allowed-google-producers-resource-hierarchy-level=[ALLOWED_GOOGLE_PRODUCERS_RESOURCE_HIERARCHY_LEVEL,
      ...]] [--async] [--description=DESCRIPTION]
    [--labels=[KEY=VALUE,...]]
    [--producer-instance-location=PRODUCER_INSTANCE_LOCATION]
    [--psc-connection-limit=PSC_CONNECTION_LIMIT] [--region=REGION]
    [--subnets=[SUBNETS,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service connection policy resource - Name of the Service Connection Policy
to be updated. This represents a Cloud resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument service_connection_policy on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the region attribute:
 * provide the argument service_connection_policy on the command line
   with a fully specified name;
 * provide the argument --region on the command line.

This must be specified.

  SERVICE_CONNECTION_POLICY
     ID of the service connection policy or fully qualified identifier for
     the service connection policy.

     To set the service_connection_policy attribute:
     + provide the argument service_connection_policy on the command
       line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allowed-google-producers-resource-hierarchy-level` | [ALLOWED_GOOGLE_PRODUCERS_RESOURCE_HIERARCHY_LEVEL,...] |  | List of projects, folders, or orgs where the producer instance can be located in the form "projects/123456789", folders/123456789", or "organizations/123456789". |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Description of the Service Connection Policy to be updated. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. |
| `--producer-instance-location` | one of: custom-resource-hierarchy-levels The producer instance must be located in one of the values provided in the allowed-google-producers-resource-hierarchy-level flag |  | Option that determines where the producer instances can be located for which connections can be created in the network controlled by this policy. PRODUCER_INSTANCE_LOCATION must be one of: custom-resource-hierarchy-levels The producer instance must be located in one of the values provided in the allowed-google-producers-resource-hierarchy-level flag. none The producer instance must be within the same project as this connection policy. |
| `--psc-connection-limit` | PSC_CONNECTION_LIMIT |  | Max number of PSC connections for this policy. |
| `--region` | REGION |  | For resources [service_connection_policy, subnets], provides fallback value for resource region attribute. When the resource's full URI path is not provided, region will fallback to this flag value. |


**Examples:**
```bash
Update a Service Connection Policy with name my-service-conn-policy in
region us-central1.

    $ gcloud network-connectivity service-connection-policies update \
        my-service-conn-policy --region=us-central1 \
        --psc-connection-limit=5 --subnets=my-subnet \
        --producer-instance-location=custom-resource-hierarchy-levels \
        --allowed-google-producers-resource-hierarchy-level=projects/\
    my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/service-connection-policies/update)

---
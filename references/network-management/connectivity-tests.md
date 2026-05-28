# gcloud network-management connectivity-tests

manage Network Management ConnectivityTests

### `gcloud network-management connectivity-tests create`

Create a new connectivity test

Create a new connectivity test with the given name.

**Synopsis:**
```
gcloud network-management connectivity-tests create CONNECTIVITY_TEST
    (--destination-cloud-sql-instance=DESTINATION_CLOUD_SQL_INSTANCE
      --destination-forwarding-rule=DESTINATION_FORWARDING_RULE
      --destination-gke-master-cluster=DESTINATION_GKE_MASTER_CLUSTER
      --destination-instance=DESTINATION_INSTANCE
      --destination-ip-address=DESTINATION_IP_ADDRESS
      --destination-redis-cluster=DESTINATION_REDIS_CLUSTER
      --destination-redis-instance=DESTINATION_REDIS_INSTANCE)
    (--source-app-engine-version=SOURCE_APP_ENGINE_VERSION
      --source-cloud-function=SOURCE_CLOUD_FUNCTION
      --source-cloud-run-revision=SOURCE_CLOUD_RUN_REVISION
      --source-cloud-sql-instance=SOURCE_CLOUD_SQL_INSTANCE
      --source-gke-master-cluster=SOURCE_GKE_MASTER_CLUSTER
      --source-instance=SOURCE_INSTANCE
      --source-ip-address=SOURCE_IP_ADDRESS) [--async]
    [--bypass-firewall-checks] [--description=DESCRIPTION]
    [--destination-fqdn=DESTINATION_FQDN]
    [--destination-network=DESTINATION_NETWORK]
    [--destination-port=DESTINATION_PORT]
    [--destination-project=DESTINATION_PROJECT] [--labels=[KEY=VALUE,...]]
    [--other-projects=[OTHER_PROJECTS,...]] [--protocol=PROTOCOL]
    [--round-trip] [--source-network=SOURCE_NETWORK]
    [--source-network-type=SOURCE_NETWORK_TYPE; default="gcp-network"]
    [--source-project=SOURCE_PROJECT] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connectivity test resource - Name of the connectivity test you want to
create. This represents a Cloud resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument connectivity_test on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTIVITY_TEST
     ID of the connectivity test or fully qualified identifier for the
     connectivity test.

     To set the connectivity_test attribute:
     + provide the argument connectivity_test on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination-cloud-sql-instance` | DESTINATION_CLOUD_SQL_INSTANCE |  | _[At least one of these must be specified:]_ A Cloud SQL instance URI as the destination endpoint. |
| `--destination-forwarding-rule` | DESTINATION_FORWARDING_RULE |  | _[At least one of these must be specified:]_ A forwarding rule URI as the destination endpoint. |
| `--destination-gke-master-cluster` | DESTINATION_GKE_MASTER_CLUSTER |  | _[At least one of these must be specified:]_ A cluster URI for Google Kubernetes Engine master as the destination endpoint. |
| `--destination-instance` | DESTINATION_INSTANCE |  | _[At least one of these must be specified:]_ A Compute Engine instance URI as the destination endpoint. |
| `--destination-ip-address` | DESTINATION_IP_ADDRESS |  | _[At least one of these must be specified:]_ The IP address of the destination which can be an external or internal IP. |
| `--destination-redis-cluster` | DESTINATION_REDIS_CLUSTER |  | _[At least one of these must be specified:]_ A Redis cluster URI as the destination endpoint. |
| `--destination-redis-instance` | DESTINATION_REDIS_INSTANCE |  | _[At least one of these must be specified:]_ A Redis instance URI as the destination endpoint. |
| `--source-app-engine-version` | SOURCE_APP_ENGINE_VERSION |  | _[At least one of these must be specified:]_ App Engine version URI as the source endpoint. |
| `--source-cloud-function` | SOURCE_CLOUD_FUNCTION |  | _[At least one of these must be specified:]_ A Cloud function URI as the source endpoint. |
| `--source-cloud-run-revision` | SOURCE_CLOUD_RUN_REVISION |  | _[At least one of these must be specified:]_ Cloud Run revision URI as the source endpoint. |
| `--source-cloud-sql-instance` | SOURCE_CLOUD_SQL_INSTANCE |  | _[At least one of these must be specified:]_ A Cloud SQL instance URI as the source endpoint. |
| `--source-gke-master-cluster` | SOURCE_GKE_MASTER_CLUSTER |  | _[At least one of these must be specified:]_ A cluster URI for Google Kubernetes Engine master as the source endpoint. |
| `--source-instance` | SOURCE_INSTANCE |  | _[At least one of these must be specified:]_ A Compute Engine instance URI as the source endpoint. |
| `--source-ip-address` | SOURCE_IP_ADDRESS |  | _[At least one of these must be specified:]_ The IP address of the source which can be an external or internal IP. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--bypass-firewall-checks` |  |  | This boolean controls whether to skip firewall checking. |
| `--description` | DESCRIPTION |  | The description of the connectivity test. |
| `--destination-fqdn` | DESTINATION_FQDN |  | A hostname as the destination endpoint. Only applicable for Google Kubernetes Engine. |
| `--destination-network` | DESTINATION_NETWORK |  | A VPC network URI where the destination is located. |
| `--destination-port` | DESTINATION_PORT |  | The IP protocol port of the destination. Only applicable when protocol is TCP or UDP. |
| `--destination-project` | DESTINATION_PROJECT |  | Project ID of the destination endpoint. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. |
| `--other-projects` | [OTHER_PROJECTS,...] |  | IDs of other projects involved in the connectivity test, besides the source and destination project. |
| `--protocol` | PROTOCOL |  | Type of protocol for the test. When not provided, "TCP" is assumed. |
| `--round-trip` |  |  | This boolean controls whether return traces (from the destination to the source) will be additionally calculated if packet successfully reaches the destination from the source. |
| `--source-network` | SOURCE_NETWORK |  | A VPC network URI where the source is located. |
| `--source-network-type` | one of: gcp-network Network in Google Cloud Platform | gcp-network | Type of the network where the source is located. SOURCE_NETWORK_TYPE must be one of: gcp-network Network in Google Cloud Platform. non-gcp-network Network outside Google Cloud Platform. |
| `--source-project` | SOURCE_PROJECT |  | Project ID of the source endpoint. |


**Examples:**
```bash
The following command creates a connectivity test with the name my-test,
and the test between a source VM and a destination IP address in a peering
network.

    $ gcloud network-management connectivity-tests create my-test \
        --source-instance=projects/my-project/zones/us-west-1/\
    instances/my-instance --destination-ip-address=10.142.0.2 \
        --destination-network=projects/my-project/global/networks/\
    peering-network
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-management/connectivity-tests/create)

---
### `gcloud network-management connectivity-tests delete`

Delete a connectivity test

Delete the specified connectivity test.

**Synopsis:**
```
gcloud network-management connectivity-tests delete CONNECTIVITY_TEST
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connectivity test resource - Name of the connectivity test you want to
delete. This represents a Cloud resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument connectivity_test on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTIVITY_TEST
     ID of the connectivity test or fully qualified identifier for the
     connectivity test.

     To set the connectivity_test attribute:
     + provide the argument connectivity_test on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command deletes a connectivity test with the name my-test.

    $ gcloud network-management connectivity-tests delete my-test
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-management/connectivity-tests/delete)

---
### `gcloud network-management connectivity-tests describe`

Describe a connectivity test

Show details of a connectivity test.

**Synopsis:**
```
gcloud network-management connectivity-tests describe CONNECTIVITY_TEST
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connectivity test resource - Name of the connectivity test you want to
describe. This represents a Cloud resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument connectivity_test on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTIVITY_TEST
     ID of the connectivity test or fully qualified identifier for the
     connectivity test.

     To set the connectivity_test attribute:
     + provide the argument connectivity_test on the command line.
```

**Examples:**
```bash
The following command prints of a connectivity test with the name my-test.

    $ gcloud network-management connectivity-tests describe my-test
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-management/connectivity-tests/describe)

---
### `gcloud network-management connectivity-tests list`

List connectivity tests

List all connectivity tests in the specified project.

You can specify the maximum number of connectivity tests to list using the
--limit flag.

**Synopsis:**
```
gcloud network-management connectivity-tests list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
The following command lists a maximum of five connectivity tests:

    $ gcloud network-management connectivity-tests list --limit=5
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-management/connectivity-tests/list)

---
### `gcloud network-management connectivity-tests rerun`

Rerun a connectivity test

Rerun the specified connectivity test.

**Synopsis:**
```
gcloud network-management connectivity-tests rerun CONNECTIVITY_TEST
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connectivity test resource - Name of the connectivity test you want to
rerun. This represents a Cloud resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument connectivity_test on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTIVITY_TEST
     ID of the connectivity test or fully qualified identifier for the
     connectivity test.

     To set the connectivity_test attribute:
     + provide the argument connectivity_test on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command reruns a connectivity test with the name my-test.

    $ gcloud network-management connectivity-tests rerun my-test
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-management/connectivity-tests/rerun)

---
### `gcloud network-management connectivity-tests update`

Update an existing connectivity test

Update an existing connectivity test with the given name.

**Synopsis:**
```
gcloud network-management connectivity-tests update CONNECTIVITY_TEST
    [--async] [--bypass-firewall-checks] [--description=DESCRIPTION]
    [--destination-fqdn=DESTINATION_FQDN]
    [--destination-network=DESTINATION_NETWORK]
    [--destination-port=DESTINATION_PORT]
    [--destination-project=DESTINATION_PROJECT] [--labels=[KEY=VALUE,...]]
    [--other-projects=[OTHER_PROJECTS,...]] [--protocol=PROTOCOL]
    [--round-trip] [--source-network=SOURCE_NETWORK]
    [--source-network-type=SOURCE_NETWORK_TYPE; default="gcp-network"]
    [--source-project=SOURCE_PROJECT]
    [--clear-destination-cloud-sql-instance
      | --destination-cloud-sql-instance=DESTINATION_CLOUD_SQL_INSTANCE]
    [--clear-destination-forwarding-rule
      | --destination-forwarding-rule=DESTINATION_FORWARDING_RULE]
    [--clear-destination-gke-master-cluster
      | --destination-gke-master-cluster=DESTINATION_GKE_MASTER_CLUSTER]
    [--clear-destination-instance
      | --destination-instance=DESTINATION_INSTANCE]
    [--clear-destination-ip-address
      | --destination-ip-address=DESTINATION_IP_ADDRESS]
    [--clear-destination-redis-cluster
      | --destination-redis-cluster=DESTINATION_REDIS_CLUSTER]
    [--clear-destination-redis-instance
      | --destination-redis-instance=DESTINATION_REDIS_INSTANCE]
    [--clear-source-app-engine-version
      | --source-app-engine-version=SOURCE_APP_ENGINE_VERSION]
    [--clear-source-cloud-function
      | --source-cloud-function=SOURCE_CLOUD_FUNCTION]
    [--clear-source-cloud-run-revision
      | --source-cloud-run-revision=SOURCE_CLOUD_RUN_REVISION]
    [--clear-source-cloud-sql-instance
      | --source-cloud-sql-instance=SOURCE_CLOUD_SQL_INSTANCE]
    [--clear-source-gke-master-cluster
      | --source-gke-master-cluster=SOURCE_GKE_MASTER_CLUSTER]
    [--clear-source-instance | --source-instance=SOURCE_INSTANCE]
    [--clear-source-ip-address | --source-ip-address=SOURCE_IP_ADDRESS]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connectivity test resource - Name of the connectivity test you want to
update. This represents a Cloud resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument connectivity_test on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTIVITY_TEST
     ID of the connectivity test or fully qualified identifier for the
     connectivity test.

     To set the connectivity_test attribute:
     + provide the argument connectivity_test on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--bypass-firewall-checks` |  |  | This boolean controls whether to skip firewall checking. Use --no-bypass-firewall-checks to disable. |
| `--description` | DESCRIPTION |  | The description of the connectivity test. |
| `--destination-fqdn` | DESTINATION_FQDN |  | A hostname as the destination endpoint. Only applicable for Google Kubernetes Engine. |
| `--destination-network` | DESTINATION_NETWORK |  | A VPC network URI where the destination is located. |
| `--destination-port` | DESTINATION_PORT |  | The IP protocol port of the destination. Only applicable when protocol is TCP or UDP. |
| `--destination-project` | DESTINATION_PROJECT |  | Project ID of the destination endpoint. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. |
| `--other-projects` | [OTHER_PROJECTS,...] |  | IDs of other projects involved in the connectivity test, besides the source and destination project. |
| `--protocol` | PROTOCOL |  | Type of protocol for the test. When not provided, "TCP" is assumed. |
| `--round-trip` |  |  | This boolean controls whether return traces (from the destination to the source) will be additionally calculated if packet successfully reaches the destination from the source. Use --no-round-trip to disable. |
| `--source-network` | SOURCE_NETWORK |  | A VPC network URI where the source is located. |
| `--source-network-type` | one of: gcp-network Network in Google Cloud Platform | gcp-network | Type of the network where the source is located. SOURCE_NETWORK_TYPE must be one of: gcp-network Network in Google Cloud Platform. non-gcp-network Network outside Google Cloud Platform. |
| `--source-project` | SOURCE_PROJECT |  | Project ID of the source endpoint. |


**Examples:**
```bash
The following command updates a connectivity test with the name my-test,
modifying the description and destination IP address.

    $ gcloud network-management connectivity-tests update my-test \
        --description='update dst addr' \
        --destination-ip-address='10.142.0.3'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-management/connectivity-tests/update)

---
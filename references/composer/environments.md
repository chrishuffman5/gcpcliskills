# gcloud composer environments

create and manage Cloud Composer environments

### `gcloud composer environments check-upgrade`

Check that upgrading a Cloud Composer environment does not result in PyPI module conflicts

Check that upgrading a Cloud Composer environment does not result in PyPI
module conflicts.

**Synopsis:**
```
gcloud composer environments check-upgrade
    (ENVIRONMENT : --location=LOCATION) [--async]
    [--airflow-version=AIRFLOW_VERSION | --image-version=IMAGE_VERSION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Environment resource - The environment to check upgrade for. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument environment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENVIRONMENT
     ID of the environment or fully qualified identifier for the
     environment.

     To set the environment attribute:
     + provide the argument environment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Region where Composer environment runs or in which to create the
     environment.

     To set the location attribute:
     + provide the argument environment on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property composer/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To check that upgrading to the 'composer-1.16.5-airflow-1.10.15' image        in a Cloud Composer environment named 'env-1' does not cause
    PyPI package conflicts,
    run:

    $ gcloud composer environments check-upgrade env-1 \
        --image-version=composer-1.16.5-airflow-1.10.15
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/environments/check-upgrade)

---
### `gcloud composer environments create`

Create and initialize a Cloud Composer environment

If run asynchronously with --async, exits after printing an operation that
can be used to poll the status of the creation operation via:

    gcloud composer operations describe

**Synopsis:**
```
gcloud composer environments create (ENVIRONMENT : --location=LOCATION)
    [--airflow-configs=[KEY=VALUE,...]]
    [--airflow-database-retention-days=AIRFLOW_DATABASE_RETENTION_DAYS]
    [--async] [--cloud-sql-machine-type=CLOUD_SQL_MACHINE_TYPE]
    [--cloud-sql-preferred-zone=CLOUD_SQL_PREFERRED_ZONE]
    [--composer-internal-ipv4-cidr-block=COMPOSER_INTERNAL_IPV4_CIDR_BLOCK]
    [--disable-logs-in-cloud-logging-only] [--disk-size=DISK_SIZE]
    [--enable-high-resilience] [--enable-logs-in-cloud-logging-only]
    [--env-variables=[NAME=VALUE,...]]
    [--environment-size=ENVIRONMENT_SIZE] [--labels=[KEY=VALUE,...]]
    [--machine-type=MACHINE_TYPE] [--network-attachment=NETWORK_ATTACHMENT]
    [--node-count=NODE_COUNT] [--oauth-scopes=[SCOPE,...]]
    [--python-version=PYTHON_VERSION] [--service-account=SERVICE_ACCOUNT]
    [--storage-bucket=STORAGE_BUCKET] [--support-web-server-plugins]
    [--tags=[TAG,...]] [--web-server-machine-type=WEB_SERVER_MACHINE_TYPE]
    [--zone=ZONE]
    [--airflow-version=AIRFLOW_VERSION | --image-version=IMAGE_VERSION]
    [--cloud-sql-ipv4-cidr=CLOUD_SQL_IPV4_CIDR
      --composer-network-ipv4-cidr=COMPOSER_NETWORK_IPV4_CIDR
      --connection-subnetwork=CONNECTION_SUBNETWORK
      --connection-type=CONNECTION_TYPE --disable-private-environment
      --enable-private-endpoint --enable-private-environment
      --enable-privately-used-public-ips
      --master-ipv4-cidr=MASTER_IPV4_CIDR
      --web-server-ipv4-cidr=WEB_SERVER_IPV4_CIDR]
    [--cluster-ipv4-cidr=CLUSTER_IPV4_CIDR
      --cluster-secondary-range-name=CLUSTER_SECONDARY_RANGE_NAME
      --enable-ip-alias --enable-ip-masq-agent
      --services-ipv4-cidr=SERVICES_IPV4_CIDR
      --services-secondary-range-name=SERVICES_SECONDARY_RANGE_NAME]
    [--dag-processor-count=DAG_PROCESSOR_COUNT
      --dag-processor-cpu=DAG_PROCESSOR_CPU
      --dag-processor-memory=DAG_PROCESSOR_MEMORY
      --dag-processor-storage=DAG_PROCESSOR_STORAGE]
    [--disable-cloud-data-lineage-integration
      | --enable-cloud-data-lineage-integration]
    [--disable-private-builds-only | --enable-private-builds-only]
    [--enable-master-authorized-networks
      --master-authorized-networks=[NETWORK,...]]
    [--enable-scheduled-snapshot-creation
      --snapshot-creation-schedule=SNAPSHOT_CREATION_SCHEDULE
      --snapshot-location=SNAPSHOT_LOCATION
      --snapshot-schedule-timezone=SNAPSHOT_SCHEDULE_TIMEZONE]
    [--enable-triggerer --triggerer-count=TRIGGERER_COUNT
      --triggerer-cpu=TRIGGERER_CPU --triggerer-memory=TRIGGERER_MEMORY]
    [--kms-key=KMS_KEY : --kms-keyring=KMS_KEYRING
      --kms-location=KMS_LOCATION --kms-project=KMS_PROJECT]
    [--maintenance-window-end=MAINTENANCE_WINDOW_END
      --maintenance-window-recurrence=MAINTENANCE_WINDOW_RECURRENCE
      --maintenance-window-start=MAINTENANCE_WINDOW_START]
    [--max-workers=MAX_WORKERS --min-workers=MIN_WORKERS
      --scheduler-count=SCHEDULER_COUNT --scheduler-cpu=SCHEDULER_CPU
      --scheduler-memory=SCHEDULER_MEMORY
      --scheduler-storage=SCHEDULER_STORAGE --web-server-cpu=WEB_SERVER_CPU
      --web-server-memory=WEB_SERVER_MEMORY
      --web-server-storage=WEB_SERVER_STORAGE --worker-cpu=WORKER_CPU
      --worker-memory=WORKER_MEMORY --worker-storage=WORKER_STORAGE]
    [--network=NETWORK : --subnetwork=SUBNETWORK]
    [--web-server-allow-all
      | --web-server-allow-ip=[description=DESCRIPTION],[ip_range=IP_RANGE]
      | --web-server-deny-all] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Environment resource - The environment to create. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument environment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENVIRONMENT
     ID of the environment or fully qualified identifier for the
     environment.

     To set the environment attribute:
     + provide the argument environment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Region where Composer environment runs or in which to create the
     environment.

     To set the location attribute:
     + provide the argument environment on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property composer/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--airflow-configs` | [KEY=VALUE,...] |  | A list of Airflow software configuration override KEY=VALUE pairs to set. For information on how to structure KEYs and VALUEs, run $ gcloud help composer environments update. |
| `--airflow-database-retention-days` | AIRFLOW_DATABASE_RETENTION_DAYS |  | The number of days for the Airflow database retention period. If set to 0, the Airflow database retention mechanism will be disabled. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--cloud-sql-machine-type` | CLOUD_SQL_MACHINE_TYPE |  | Cloud SQL machine type used by the Airflow database. The list of available machine types is available here: https://cloud.google.com/composer/pricing#db-machine-types. |
| `--cloud-sql-preferred-zone` | CLOUD_SQL_PREFERRED_ZONE |  | Select cloud sql preferred zone, supported for Composer 2 Environments. |
| `--composer-internal-ipv4-cidr-block` | COMPOSER_INTERNAL_IPV4_CIDR_BLOCK |  | The IP range in CIDR notation to use internally by Cloud Composer. This should have a netmask length of 20. Can be specified for Composer 3 or greater. |
| `--disable-logs-in-cloud-logging-only` |  |  | Disable logs in cloud logging only, supported for Composer 2 Environments. |
| `--disk-size` | DISK_SIZE |  | The disk size for each VM node in the environment. The minimum size is 20GB, and the maximum is 64TB. Specified value must be an integer multiple of gigabytes. Cannot be updated after the environment has been created. If units are not provided, defaults to GB. |
| `--enable-high-resilience` |  |  | Enable high resilience, supported for Composer 2 Environments. |
| `--enable-logs-in-cloud-logging-only` |  |  | Enable logs in cloud logging only, supported for Composer 2 Environments. |
| `--env-variables` | [NAME=VALUE,...] |  | A comma-delimited list of environment variable NAME=VALUE pairs to provide to the Airflow scheduler, worker, and webserver processes. NAME may contain upper and lowercase letters, digits, and underscores, but they may not begin with a digit. To include commas as part of a VALUE, see gcloud topic escaping for information about overriding the delimiter. |
| `--environment-size` | one of: extra-large, large, medium, small, unspecified |  | Size of the environment. Unspecified means that the default option will be chosen. ENVIRONMENT_SIZE must be one of: extra-large, large, medium, small, unspecified. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--machine-type` | MACHINE_TYPE |  | The Compute Engine machine type (https://cloud.google.com/compute/docs/machine-types) to use for nodes. For example --machine-type=n1-standard-1. |
| `--network-attachment` | NETWORK_ATTACHMENT |  | Cloud Composer Network Attachment, which provides connectivity with a user's VPC network, supported in Composer 3 environments or greater. |
| `--node-count` | NODE_COUNT |  | The number of nodes to create to run the environment. |
| `--oauth-scopes` | [SCOPE,...] |  | The set of Google API scopes to be made available on all of the node VMs. Defaults to ['https://www.googleapis.com/auth/cloud-platform']. Cannot be updated. |
| `--python-version` | PYTHON_VERSION |  | The Python version to be used within the created environment. Supplied value should represent the desired major Python version. Cannot be updated. PYTHON_VERSION must be one of: 2 Created environment will use Python 2 3 Created environment will use Python 3 |
| `--service-account` | SERVICE_ACCOUNT |  | The Google Cloud Platform service account to be used by the node VMs. You must explicitly specify a service account. Cannot be updated. |
| `--storage-bucket` | STORAGE_BUCKET |  | Name of an exisiting Cloud Storage bucket to be used by the environment. Supported only for Composer 2.4.X and above. |
| `--support-web-server-plugins` |  |  | Enable the support for web server plugins, supported in Composer 3 or greater. |
| `--tags` | [TAG,...] |  | The set of instance tags applied to all node VMs. Tags are used to identify valid sources or targets for network firewalls. Each tag within the list must comply with RFC 1035. Cannot be updated. |
| `--web-server-machine-type` | WEB_SERVER_MACHINE_TYPE |  | machine type used by the Airflow web server. The list of available machine types is available here: https://cloud.google.com/composer/pricing. |
| `--zone` | ZONE |  | The Compute Engine zone in which the environment will be created. For example --zone=us-central1-a. |


**Examples:**
```bash
To create an environment called env-1 with all the default values, run:

    $ gcloud composer environments create env-1

To create a new environment named env-1 with the Google Compute Engine
machine-type n1-standard-8, and the Google Compute Engine network
my-network, run:

    $ gcloud composer environments create env-1 \
        --machine-type=n1-standard-8 --network=my-network
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/environments/create)

---
### `gcloud composer environments database-failover`

Run a database failover operation

Run a database failover operation.

**Synopsis:**
```
gcloud composer environments database-failover
    (ENVIRONMENT : --location=LOCATION) [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Environment resource - The environment for which to trigger a database
failover. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument environment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENVIRONMENT
     ID of the environment or fully qualified identifier for the
     environment.

     To set the environment attribute:
     + provide the argument environment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Region where Composer environment runs or in which to create the
     environment.

     To set the location attribute:
     + provide the argument environment on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property composer/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To run a manual database failover on the environment named environment-1,
run:        $ gcloud composer environments database-failover environment-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/environments/database-failover)

---
### `gcloud composer environments delete`

Delete one or more Cloud Composer environments

Environments cannot be deleted unless they are in one of the RUNNING or
ERROR states. If run asynchronously with --async, exits after printing one
or more operation names that can be used to poll the status of the
deletion(s) via:

    gcloud composer operations describe

If any of the environments are already in the process of being deleted, the
original deletion operations are waited on (default) or printed (--async).

**Synopsis:**
```
gcloud composer environments delete
    (ENVIRONMENTS [ENVIRONMENTS ...] : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Environment resource - The environments to delete. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument environments on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENVIRONMENTS [ENVIRONMENTS ...]
     IDs of the environments or fully qualified identifiers for the
     environments.

     To set the environment attribute:
     + provide the argument environments on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Region where Composer environment runs or in which to create the
     environment.

     To set the location attribute:
     + provide the argument environments on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property composer/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete the environment named environment-1, run:

    $ gcloud composer environments delete environment-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/environments/delete)

---
### `gcloud composer environments describe`

Get details about a Cloud Composer environment

Get details about a Cloud Composer environment.

**Synopsis:**
```
gcloud composer environments describe (ENVIRONMENT : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Environment resource - The environment to describe. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument environment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENVIRONMENT
     ID of the environment or fully qualified identifier for the
     environment.

     To set the environment attribute:
     + provide the argument environment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Region where Composer environment runs or in which to create the
     environment.

     To set the location attribute:
     + provide the argument environment on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property composer/location.
```

**Examples:**
```bash
To get details about the Cloud Composer environment env-1, run:

    $ gcloud composer environments describe env-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/environments/describe)

---
### `gcloud composer environments fetch-database-properties`

Fetch database properties

Fetch database properties.

**Synopsis:**
```
gcloud composer environments fetch-database-properties
    (ENVIRONMENT : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Environment resource - The environment for which to fetch database
properties. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument environment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENVIRONMENT
     ID of the environment or fully qualified identifier for the
     environment.

     To set the environment attribute:
     + provide the argument environment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Region where Composer environment runs or in which to create the
     environment.

     To set the location attribute:
     + provide the argument environment on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property composer/location.
```

**Examples:**
```bash
To fetch database properties for the environment named environment-1, run:        $ gcloud composer environments fetch-database-properties \
        environment-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/environments/fetch-database-properties)

---
### `gcloud composer environments list`

List the Cloud Composer environments under a project and location

List environments that have not been successfully deleted. Prints a table
with the following columns:
  o name
  o location
  o status
  o creation timestamp

**Synopsis:**
```
gcloud composer environments list [--locations=[LOCATIONS,...]]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--locations` | [LOCATIONS,...] |  | _[* set the property core/project.]_ IDs of the locations or fully qualified identifiers for the locations. To set the location attribute: + provide the argument --locations on the command line. |


**Examples:**
```bash
To list the Cloud Composer environments under the project 'project-1' and
in location 'us-central1', run:

    $ gcloud composer environments list --project=project-1 \
        --locations=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/environments/list)

---
### `gcloud composer environments list-packages`

List all PyPI modules installed in an Airflow worker

List all PyPI modules installed in an Airflow worker.

**Synopsis:**
```
gcloud composer environments list-packages
    (ENVIRONMENT : --location=LOCATION) [--tree] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Environment resource - The environment in which to list PyPI modules. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument environment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENVIRONMENT
     ID of the environment or fully qualified identifier for the
     environment.

     To set the environment attribute:
     + provide the argument environment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Region where Composer environment runs or in which to create the
     environment.

     To set the location attribute:
     + provide the argument environment on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property composer/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--tree` |  |  | List PyPI packages, their versions and a dependency tree, as displayed by the "python -m pipdeptree --warn" command. |


**Examples:**
```bash
The following command:

    $ gcloud composer environments list-packages myenv

runs the "python -m pip list" command on a worker and returns the output.

The following command:

    $ gcloud composer environments list-packages myenv --tree

runs the "python -m pipdeptree --warn" command on a worker and returns the
output.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/environments/list-packages)

---
### `gcloud composer environments list-upgrades`

List the Cloud Composer image version upgrades for a specific environment

gcloud composer environments list-upgrades prints a table listing the
suggested image-version upgrades with the following columns:
  o Image Version ID
  o Composer 'default' flag
  o List of supported python versions

**Synopsis:**
```
gcloud composer environments list-upgrades
    (ENVIRONMENT : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Environment resource - The environment to list upgrades. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument environment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENVIRONMENT
     ID of the environment or fully qualified identifier for the
     environment.

     To set the environment attribute:
     + provide the argument environment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Region where Composer environment runs or in which to create the
     environment.

     To set the location attribute:
     + provide the argument environment on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property composer/location.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/environments/list-upgrades)

---
### `gcloud composer environments list-workloads`

List Composer workloads, supported in Composer 3 environments or greater

List Composer workloads, supported in Composer 3 environments or greater.

**Synopsis:**
```
gcloud composer environments list-workloads
    (ENVIRONMENT : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Environment resource - The environment for which to display workloads. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument environment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENVIRONMENT
     ID of the environment or fully qualified identifier for the
     environment.

     To set the environment attribute:
     + provide the argument environment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Region where Composer environment runs or in which to create the
     environment.

     To set the location attribute:
     + provide the argument environment on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property composer/location.
```

**Examples:**
```bash
To display Composer workloads for the environment named environment-1, run:        $ gcloud composer environments list-workloads environment-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/environments/list-workloads)

---
### `gcloud composer environments restart-web-server`

Restart web server for a Cloud Composer environment

Restart web server for a Cloud Composer environment.

**Synopsis:**
```
gcloud composer environments restart-web-server
    (ENVIRONMENT : --location=LOCATION) [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Environment resource - The environment to restart web server for. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument environment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENVIRONMENT
     ID of the environment or fully qualified identifier for the
     environment.

     To set the environment attribute:
     + provide the argument environment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Region where Composer environment runs or in which to create the
     environment.

     To set the location attribute:
     + provide the argument environment on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property composer/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To restart the Cloud Composer web server in an environment named env-1,
run:

    $ gcloud composer environments restart-web-server env-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/environments/restart-web-server)

---
### `gcloud composer environments run`

Run an Airflow sub-command remotely in a Cloud Composer environment

Executes an Airflow CLI sub-command remotely in an environment. If the
sub-command takes flags, separate the environment name from the sub-command
and its flags with ``--''. This command waits for the sub-command to
complete; its exit code will match the sub-command's exit code.

Note: Airflow CLI sub-command syntax differs between Airflow 1 and Airflow
2. Refer to the Airflow CLI reference documentation for more details.

**Synopsis:**
```
gcloud composer environments run (ENVIRONMENT : --location=LOCATION)
    SUBCOMMAND [SUBCOMMAND_NESTED] [GCLOUD_WIDE_FLAG ...] [-- CMD_ARGS ...]
```

**Positional arguments:**
```
Environment resource - The environment in which to run an Airflow command.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument environment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENVIRONMENT
     ID of the environment or fully qualified identifier for the
     environment.

     To set the environment attribute:
     + provide the argument environment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Region where Composer environment runs or in which to create the
     environment.

     To set the location attribute:
     + provide the argument environment on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property composer/location.

SUBCOMMAND
   The Airflow CLI subcommand to run. Available subcommands include
   (listed with Airflow versions that support): backfill [**, 2.0.0),
   clear [**, 2.0.0), connections [**, 3.2.0), dag_state [**, 2.0.0), dags
   [1.10.14, 3.2.0), db [2.3.0, 3.0.0), delete_dag [1.10.1, 2.0.0),
   kerberos [**, 3.2.0), kubernetes [2.1.4, 3.2.0), list-import-errors
   [**, 3.0.0), list_dag_runs [1.10.2, 2.0.0), list_dags [**, 2.0.0),
   list_tasks [**, 2.0.0), next_execution [1.10.2, 2.0.0), pause [**,
   2.0.0), pool [**, 2.0.0), pools [1.10.14, 3.2.0), render [**, 2.0.0),
   roles [2.0.0, 3.2.0), run [**, 2.0.0), sync-perm [1.10.14, 3.2.0),
   sync_perm [1.10.2, 2.0.0), task_failed_deps [**, 2.0.0), task_state
   [**, 2.0.0), tasks [1.10.14, 3.2.0), test [**, 2.0.0), trigger_dag [**,
   2.0.0), unpause [**, 2.0.0), upgrade_check [1.10.15, 2.0.0), users
   [1.10.14, 3.2.0), variables [**, 3.2.0), version [**, 3.2.0) (see
   https://airflow.apache.org/docs/apache-airflow/stable/cli-and-env-variables-ref.html
   for more info).

[SUBCOMMAND_NESTED]
   Additional subcommand in case it is nested. The following is a list of
   allowed nested subcommands:
   * db: check, trim
   * all other subcommands: all nested subcommands are allowed

[-- CMD_ARGS ...]
   Command line arguments to the subcommand.

   The '--' argument must be specified between gcloud specific args on the
   left and CMD_ARGS on the right. Example:

   gcloud composer environments run myenv trigger_dag -- some_dag
   --run_id=foo
```

**Examples:**
```bash
The following command in environments with Airflow 2:

    gcloud composer environments run myenv dags trigger -- some_dag --run_id=foo

is equivalent to running the following command from a shell inside the
my-environment environment:

    airflow dags trigger --run_id=foo some_dag

The same command, but for environments with Airflow 1.10.14+:

    gcloud composer environments run myenv trigger_dag -- some_dag --run_id=foo

is equivalent to running the following command from a shell inside the
my-environment environment:

    airflow trigger_dag some_dag --run_id=foo

The following command (for environments with Airflow 1.10.14+):

    gcloud composer environments run myenv dags list

is equivalent to running the following command from a shell inside the
my-environment environment:

    airflow dags list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/environments/run)

---
### `gcloud composer environments update`

Update properties of a Cloud Composer environment

Update properties of a Cloud Composer environment.

**Synopsis:**
```
gcloud composer environments update (ENVIRONMENT : --location=LOCATION)
    (--airflow-database-retention-days=AIRFLOW_DATABASE_RETENTION_DAYS
      | --cloud-sql-machine-type=CLOUD_SQL_MACHINE_TYPE
      | --disable-high-resilience | --disable-logs-in-cloud-logging-only
      | --disable-private-environment | --enable-high-resilience
      | --enable-logs-in-cloud-logging-only | --enable-private-environment
      | --environment-size=ENVIRONMENT_SIZE | --node-count=NODE_COUNT
      | --support-web-server-plugins
      | --web-server-machine-type=WEB_SERVER_MACHINE_TYPE
      | --airflow-version=AIRFLOW_VERSION | --image-version=IMAGE_VERSION
      | --clear-maintenance-window
      | --maintenance-window-end=MAINTENANCE_WINDOW_END
      --maintenance-window-recurrence=MAINTENANCE_WINDOW_RECURRENCE
      --maintenance-window-start=MAINTENANCE_WINDOW_START
      | --disable-cloud-data-lineage-integration
      | --enable-cloud-data-lineage-integration
      | --disable-master-authorized-networks
      --enable-master-authorized-networks
      --master-authorized-networks=[NETWORK,...]
      | --disable-private-builds-only | --enable-private-builds-only
      | --disable-scheduled-snapshot-creation
      | --enable-scheduled-snapshot-creation
      --snapshot-creation-schedule=SNAPSHOT_CREATION_SCHEDULE
      --snapshot-location=SNAPSHOT_LOCATION
      --snapshot-schedule-timezone=SNAPSHOT_SCHEDULE_TIMEZONE
      | --disable-vpc-connectivity
      | --network-attachment=NETWORK_ATTACHMENT
      | [--network=NETWORK : --subnetwork=SUBNETWORK]
      | --max-workers=MAX_WORKERS --min-workers=MIN_WORKERS
      --scheduler-count=SCHEDULER_COUNT --scheduler-cpu=SCHEDULER_CPU
      --scheduler-memory=SCHEDULER_MEMORY
      --scheduler-storage=SCHEDULER_STORAGE --web-server-cpu=WEB_SERVER_CPU
      --web-server-memory=WEB_SERVER_MEMORY
      --web-server-storage=WEB_SERVER_STORAGE --worker-cpu=WORKER_CPU
      --worker-memory=WORKER_MEMORY --worker-storage=WORKER_STORAGE
      --dag-processor-count=DAG_PROCESSOR_COUNT
      --dag-processor-cpu=DAG_PROCESSOR_CPU
      --dag-processor-memory=DAG_PROCESSOR_MEMORY
      --dag-processor-storage=DAG_PROCESSOR_STORAGE --disable-triggerer
      | --enable-triggerer --triggerer-count=TRIGGERER_COUNT
      --triggerer-cpu=TRIGGERER_CPU --triggerer-memory=TRIGGERER_MEMORY
      | --update-airflow-configs=[KEY=VALUE,...] --clear-airflow-configs
      | --remove-airflow-configs=[KEY,...]
      | --update-env-variables=[NAME=VALUE,...] --clear-env-variables
      | --remove-env-variables=[NAME,...]
      | --update-labels=[KEY=VALUE,...] --clear-labels
      | --remove-labels=[KEY,...]
      | --update-pypi-packages-from-file=UPDATE_PYPI_PACKAGES_FROM_FILE
      | --update-pypi-package=PACKAGE[EXTRAS_LIST]VERSION_SPECIFIER
      --clear-pypi-packages | --remove-pypi-packages=[PACKAGE,...]
      | --update-web-server-allow-ip=[description=DESCRIPTION],
      [ip_range=IP_RANGE] | --web-server-allow-all | --web-server-deny-all)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Environment resource - The environment to update. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument environment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENVIRONMENT
     ID of the environment or fully qualified identifier for the
     environment.

     To set the environment attribute:
     + provide the argument environment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Region where Composer environment runs or in which to create the
     environment.

     To set the location attribute:
     + provide the argument environment on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property composer/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--airflow-database-retention-days` | AIRFLOW_DATABASE_RETENTION_DAYS |  | _[Exactly one of these must be specified:]_ The number of days for the Airflow database retention period. If set to 0, the Airflow database retention mechanism will be disabled. |
| `--cloud-sql-machine-type` | CLOUD_SQL_MACHINE_TYPE |  | _[Exactly one of these must be specified:]_ Cloud SQL machine type used by the Airflow database. The list of available machine types is available here: https://cloud.google.com/composer/pricing#db-machine-types. |
| `--disable-high-resilience` |  |  | _[Exactly one of these must be specified:]_ Disable high resilience, supported for Composer 2 Environments. |
| `--disable-logs-in-cloud-logging-only` |  |  | _[Exactly one of these must be specified:]_ Disable logs in cloud logging only, supported for Composer 2 Environments. |
| `--disable-private-environment` |  |  | _[Exactly one of these must be specified:]_ Enable internet connection from any Composer component, supported in Composer 3 environments or greater. |
| `--enable-high-resilience` |  |  | _[Exactly one of these must be specified:]_ Enable high resilience, supported for Composer 2 Environments. |
| `--enable-logs-in-cloud-logging-only` |  |  | _[Exactly one of these must be specified:]_ Enable logs in cloud logging only, supported for Composer 2 Environments. |
| `--enable-private-environment` |  |  | _[Exactly one of these must be specified:]_ Disable internet connection from any Composer component, supported in Composer 3 environments or greater. |
| `--environment-size` | one of: extra-large, large, medium, small, unspecified |  | _[Exactly one of these must be specified:]_ Size of the environment. Unspecified means that the default option will be chosen. ENVIRONMENT_SIZE must be one of: extra-large, large, medium, small, unspecified. |
| `--node-count` | NODE_COUNT |  | _[Exactly one of these must be specified:]_ The new number of nodes running the environment. Must be >= 3. |
| `--support-web-server-plugins` |  |  | _[Exactly one of these must be specified:]_ Enable the support for web server plugins, supported in Composer 3 or greater. |
| `--web-server-machine-type` | WEB_SERVER_MACHINE_TYPE |  | _[Exactly one of these must be specified:]_ machine type used by the Airflow web server. The list of available machine types is available here: https://cloud.google.com/composer/pricing. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To update the Cloud Composer environment named env-1 to have 8 Airflow
workers, and not have the production label, run:

    $ gcloud composer environments update env-1 --node-count=8 \
        --remove-labels=production
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/environments/update)

---

## `gcloud composer environments snapshots` — save and load snapshots of environment
### `gcloud composer environments snapshots load`

Load a snapshot into the environment

Load a snapshot into the environment.

**Synopsis:**
```
gcloud composer environments snapshots load
    (ENVIRONMENT : --location=LOCATION) --snapshot-path=SNAPSHOT_PATH
    [--async] [--skip-airflow-overrides-setting]
    [--skip-environment-variables-setting] [--skip-gcs-data-copying]
    [--skip-pypi-packages-installation] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Environment resource - The environment where to load a snapshot. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument environment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENVIRONMENT
     ID of the environment or fully qualified identifier for the
     environment.

     To set the environment attribute:
     + provide the argument environment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Region where Composer environment runs or in which to create the
     environment.

     To set the location attribute:
     + provide the argument environment on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property composer/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--snapshot-path` | SNAPSHOT_PATH |  | The Cloud Storage path to load the snapshot from. It must start with prefix gs:// and one needs to specify a single snapshot that should be loaded. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--skip-airflow-overrides-setting` |  |  | When specified, skips setting Airflow overrides from the snapshot. |
| `--skip-environment-variables-setting` |  |  | When specified, skips setting environment variables from the snapshot. |
| `--skip-gcs-data-copying` |  |  | When specified, skips copying dags, plugins and data folders from the snapshot. |
| `--skip-pypi-packages-installation` |  |  | When specified, skips the installation of custom PyPI packages from the snapshot. |


**Examples:**
```bash
To load a snapshot into the environment named env-1, run:

    $ gcloud composer environments snapshots load env-1 \
        --snapshot-path=gs://my-bucket/path-to-the-specific-snapshot
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/environments/snapshots/load)

---
### `gcloud composer environments snapshots save`

Save a snapshot of the environment

Save a snapshot of the environment.

**Synopsis:**
```
gcloud composer environments snapshots save
    (ENVIRONMENT : --location=LOCATION) [--async]
    [--snapshot-location=SNAPSHOT_LOCATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Environment resource - The environment where the snapshot must be saved.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument environment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENVIRONMENT
     ID of the environment or fully qualified identifier for the
     environment.

     To set the environment attribute:
     + provide the argument environment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Region where Composer environment runs or in which to create the
     environment.

     To set the location attribute:
     + provide the argument environment on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property composer/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--snapshot-location` | SNAPSHOT_LOCATION |  | The Cloud Storage location where to save the snapshot. It must start with the prefix gs://. Default value is /snapshots directory in the Cloud Storage bucket of the environment. |


**Examples:**
```bash
To save a snapshot of the environment named env-1, run:

    $ gcloud composer environments snapshots save env-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/environments/snapshots/save)

---

## `gcloud composer environments storage` — manage Cloud Storage objects stored as part of Cloud Composer environments

## `gcloud composer environments storage dags` — manage DAGs for Cloud Composer environments
### `gcloud composer environments storage dags delete`

Delete DAG files from an Cloud Composer environment's Cloud Storage bucket

Delete DAG files from an Cloud Composer environment's Cloud Storage bucket.

**Synopsis:**
```
gcloud composer environments storage dags delete [TARGET]
    (--environment=ENVIRONMENT : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[TARGET]
   A relative path to a file or subdirectory to delete within the dags
   Cloud Storage subdirectory. If not specified, the entire contents of
   the dags subdirectory will be deleted.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--environment` | ENVIRONMENT |  | _[This must be specified.]_ ID of the environment or fully qualified identifier for the environment. To set the environment attribute: + provide the argument --environment on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Region where Composer environment runs or in which to create the environment. To set the location attribute: + provide the argument --environment on the command line with a fully specified name; + provide the argument --location on the command line; + set the property composer/location. |


**Examples:**
```bash
To delete the dags in the path path/to/dags, for the environment named
environment-1 in the location us-east1, run:

    $ gcloud composer environments storage dags delete path/to/dags \
        --environment=environment-1 --location=us-east1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/environments/storage/dags/delete)

---
### `gcloud composer environments storage dags export`

Export DAGs from an environment into local storage or Cloud Storage

If the SOURCE is a directory, it and its contents are are exported
recursively. If no SOURCE is provided, the entire contents of the
environment's DAGs directory will be exported. Colliding files in the
DESTINATION will be overwritten. If a file exists in the DESTINATION but
there is no corresponding file to overwrite it, it is untouched.

**Synopsis:**
```
gcloud composer environments storage dags export --destination=DESTINATION
    (--environment=ENVIRONMENT : --location=LOCATION) [--source=SOURCE]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | The path to an existing local directory or a Cloud Storage bucket/directory into which to export files. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source` | SOURCE |  | An optional relative path to a file or directory to be exported from the dags/ subdirectory in the environment's Cloud Storage bucket. |


**Examples:**
```bash
Suppose the environment myenv's Cloud Storage bucket has the following
structure:

    gs://the-bucket
    |
    +-- dags
    |   |
    |   +-- file1.py
    |   +-- file2.py
    |   |
    |   +-- subdir1
    |   |   |
    |   |   +-- file3.py
    |   |   +-- file4.py

And the local directory '/foo' has the following structure:

    /foo
    |
    +-- file1.py
    +-- fileX.py
    |   |
    |   +-- subdir1
    |   |   |
    |   |   +-- file3.py
    |   |   +-- fileY.py

The following command:

    gcloud composer environments storage dags export myenv --destination=/foo

would result in the following structure in the local '/foo' directory:

    /foo
    |
    +-- file1.py
    +-- file2.py
    +-- fileX.py
    |   |
    |   +-- subdir1
    |   |   |
    |   |   +-- file3.py
    |   |   +-- file4.py
    |   |   +-- fileY.py

The local files '/foo/file1.py' and '/foo/subdir1/file3.py' will be
overwritten with the contents of the corresponding files in the Cloud
Storage bucket.

If instead we had run

    gcloud composer environments storage dags export myenv --source=subdir1/file3.py --destination=/foo

the resulting local directory structure would be the following:

    /foo
    |
    +-- file1.py
    +-- file3.py
    +-- fileX.py
    |   |
    |   +-- subdir1
    |   |   |
    |   |   +-- file3.py
    |   |   +-- fileY.py

No local files would be overwritten since
'gs://the-bucket/dags/subdir1/file3.py' was written to '/foo/file3.py'
instead of 'foo/subdir1/file3.py'.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/environments/storage/dags/export)

---
### `gcloud composer environments storage dags import`

Import DAGs from local storage or Cloud Storage into an environment

If the SOURCE is a directory, it and its contents are imported recursively.
Colliding files in the environment's Cloud Storage bucket will be
overwritten. If a file exists in the bucket but is not present in the
SOURCE, it is not removed.

**Synopsis:**
```
gcloud composer environments storage dags import --source=SOURCE
    (--environment=ENVIRONMENT : --location=LOCATION)
    [--destination=DESTINATION] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source` | SOURCE |  | Path to a local directory/file or Cloud Storage bucket/object to be imported into the dags/ subdirectory in the environment's Cloud Storage bucket. Cloud Storage paths must begin with 'gs://'. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | An optional subdirectory under the dags/ directory in the environment's Cloud Storage bucket into which to import files. May contain forward slashes to delimit multiple levels of subdirectory nesting, but should not contain leading or trailing slashes. If the DESTINATION does not exist, it will be created. |


**Examples:**
```bash
Suppose the '/foo' directory in the local filesystem has the following
structure:

    foo
    |
    +-- subdir1
    |   |
    |   +-- file1.txt
    |   +-- file2.txt
    |
    +-- subdir2
    |   |
    |   +-- file3.txt
    |   +-- file4.txt

And the environment myenv's Cloud Storage bucket has the following
structure:

    gs://the-bucket
    |
    +-- dags
    |   |
    |   +-- foo
    |   |   |
    |   |   +-- subdir1
    |   |   |   |
    |   |   |   +-- bar.txt

The following command:

    gcloud composer environments storage dags import myenv --source=/foo

would result in the following structure in myenv's Cloud Storage bucket:

    gs://the-bucket
    |
    +-- dags
    |   |
    |   +-- foo
    |   |   |
    |   |   +-- subdir1
    |   |   |   |
    |   |   |   +-- bar.txt
    |   |   |   +-- file1.txt
    |   |   |   +-- file2.txt
    |   |   |
    |   |   +-- subdir2
    |   |   |   |
    |   |   |   +-- file3.txt
    |   |   |   +-- file4.txt

If instead we had run

    gcloud composer environments storage dags import myenv --source=/foo --destination=bar

the resulting bucket structure would be the following:

    gs://the-bucket
    |
    +-- dags
    |   |
    |   +-- foo
    |   |   |
    |   |   +-- subdir1
    |   |   |   |
    |   |   |   +-- bar.txt
    |   |
    |   +-- bar
    |   |   |
    |   |   +-- foo
    |   |   |   |
    |   |   |   +-- subdir1
    |   |   |   |   |
    |   |   |   |   +-- file1.txt
    |   |   |   |   +-- file2.txt
    |   |   |   |
    |   |   |   +-- subdir2
    |   |   |   |   |
    |   |   |   |   +-- file3.txt
    |   |   |   |   +-- file4.txt
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/environments/storage/dags/import)

---
### `gcloud composer environments storage dags list`

List the DAG files for a Cloud Composer environment

List the DAG files for a Cloud Composer environment.

**Synopsis:**
```
gcloud composer environments storage dags list
    (--environment=ENVIRONMENT : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--environment` | ENVIRONMENT |  | _[This must be specified.]_ ID of the environment or fully qualified identifier for the environment. To set the environment attribute: + provide the argument --environment on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Region where Composer environment runs or in which to create the environment. To set the location attribute: + provide the argument --environment on the command line with a fully specified name; + provide the argument --location on the command line; + set the property composer/location. |


**Examples:**
```bash
To list the dags for the Cloud Composer environment environment-1 and
location us-central1, run:

    $ gcloud composer environments storage dags list \
        --environment=environment-1 --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/environments/storage/dags/list)

---

## `gcloud composer environments storage data` — manage data for Cloud Composer environments
### `gcloud composer environments storage data delete`

Delete data from an Cloud Composer environment's Cloud Storage bucket

Delete data from an Cloud Composer environment's Cloud Storage bucket.

**Synopsis:**
```
gcloud composer environments storage data delete [TARGET]
    (--environment=ENVIRONMENT : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[TARGET]
   A relative path to a file or subdirectory to delete within the data
   Cloud Storage subdirectory. If not specified, the entire contents of
   the data subdirectory will be deleted.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--environment` | ENVIRONMENT |  | _[This must be specified.]_ ID of the environment or fully qualified identifier for the environment. To set the environment attribute: + provide the argument --environment on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Region where Composer environment runs or in which to create the environment. To set the location attribute: + provide the argument --environment on the command line with a fully specified name; + provide the argument --location on the command line; + set the property composer/location. |


**Examples:**
```bash
To delete the data from the path path/to/data, for the environment named
environment-1 in the location us-east1, run:

    $ gcloud composer environments storage data delete path/to/data \
        --environment=environment-1 --location=us-east1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/environments/storage/data/delete)

---
### `gcloud composer environments storage data export`

Export data from an environment into local storage or Cloud Storage

If the SOURCE is a directory, it and its contents are are exported
recursively. If no SOURCE is provided, the entire contents of the
environment's data directory will be exported. Colliding files in the
DESTINATION will be overwritten. If a file exists in the DESTINATION but
there is no corresponding file to overwrite it, it is untouched.

**Synopsis:**
```
gcloud composer environments storage data export --destination=DESTINATION
    (--environment=ENVIRONMENT : --location=LOCATION) [--source=SOURCE]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | The path to an existing local directory or a Cloud Storage bucket/directory into which to export files. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source` | SOURCE |  | An optional relative path to a file or directory to be exported from the data/ subdirectory in the environment's Cloud Storage bucket. |


**Examples:**
```bash
Suppose the environment myenv's Cloud Storage bucket has the following
structure:

    gs://the-bucket
    |
    +-- data
    |   |
    |   +-- file1.txt
    |   +-- file2.txt
    |   |
    |   +-- subdir1
    |   |   |
    |   |   +-- file3.txt
    |   |   +-- file4.txt

And the local directory '/foo' has the following structure:

    /foo
    |
    +-- file1.txt
    +-- fileX.txt
    |   |
    |   +-- subdir1
    |   |   |
    |   |   +-- file3.txt
    |   |   +-- fileY.txt

The following command:

    gcloud composer environments storage data export myenv --destination=/foo

would result in the following structure in the local '/foo' directory:

    /foo
    |
    +-- file1.txt
    +-- file2.txt
    +-- fileX.txt
    |   |
    |   +-- subdir1
    |   |   |
    |   |   +-- file3.txt
    |   |   +-- file4.txt
    |   |   +-- fileY.txt

The local files '/foo/file1.txt' and '/foo/subdir1/file3.txt' will be
overwritten with the contents of the corresponding files in the Cloud
Storage bucket.

If instead we had run

    gcloud composer environments storage data export myenv --source=subdir1/file3.txt --destination=/foo

the resulting local directory structure would be the following:

    /foo
    |
    +-- file1.txt
    +-- file3.txt
    +-- fileX.txt
    |   |
    |   +-- subdir1
    |   |   |
    |   |   +-- file3.txt
    |   |   +-- fileY.txt

No local files would be overwritten since
'gs://the-bucket/dags/subdir1/file3.txt' was written to '/foo/file3.txt'
instead of 'foo/subdir1/file3.txt'.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/environments/storage/data/export)

---
### `gcloud composer environments storage data import`

Import data from local storage or Cloud Storage into an environment

If the SOURCE is a directory, it and its contents are imported recursively.
Colliding files in the environment's Cloud Storage bucket will be
overwritten. If a file exists in the bucket but is not present in the
SOURCE, it is not removed.

**Synopsis:**
```
gcloud composer environments storage data import --source=SOURCE
    (--environment=ENVIRONMENT : --location=LOCATION)
    [--destination=DESTINATION] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source` | SOURCE |  | Path to a local directory/file or Cloud Storage bucket/object to be imported into the data/ subdirectory in the environment's Cloud Storage bucket. Cloud Storage paths must begin with 'gs://'. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | An optional subdirectory under the data/ directory in the environment's Cloud Storage bucket into which to import files. May contain forward slashes to delimit multiple levels of subdirectory nesting, but should not contain leading or trailing slashes. If the DESTINATION does not exist, it will be created. |


**Examples:**
```bash
Suppose the '/foo' directory in the local filesystem has the following
structure:

    foo
    |
    +-- subdir1
    |   |
    |   +-- file1.txt
    |   +-- file2.txt
    |
    +-- subdir2
    |   |
    |   +-- file3.txt
    |   +-- file4.txt

And the environment myenv's Cloud Storage bucket has the following
structure:

    gs://the-bucket
    |
    +-- data
    |   |
    |   +-- foo
    |   |   |
    |   |   +-- subdir1
    |   |   |   |
    |   |   |   +-- bar.txt

The following command:

    gcloud composer environments storage data import myenv --source=/foo

would result in the following structure in myenv's Cloud Storage bucket:

    gs://the-bucket
    |
    +-- data
    |   |
    |   +-- foo
    |   |   |
    |   |   +-- subdir1
    |   |   |   |
    |   |   |   +-- bar.txt
    |   |   |   +-- file1.txt
    |   |   |   +-- file2.txt
    |   |   |
    |   |   +-- subdir2
    |   |   |   |
    |   |   |   +-- file3.txt
    |   |   |   +-- file4.txt

If instead we had run

    gcloud composer environments storage data import myenv --source=/foo --destination=bar

the resulting bucket structure would be the following:

    gs://the-bucket
    |
    +-- data
    |   |
    |   +-- foo
    |   |   |
    |   |   +-- subdir1
    |   |   |   |
    |   |   |   +-- bar.txt
    |   |
    |   +-- bar
    |   |   |
    |   |   +-- foo
    |   |   |   |
    |   |   |   +-- subdir1
    |   |   |   |   |
    |   |   |   |   +-- file1.txt
    |   |   |   |   +-- file2.txt
    |   |   |   |
    |   |   |   +-- subdir2
    |   |   |   |   |
    |   |   |   |   +-- file3.txt
    |   |   |   |   +-- file4.txt
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/environments/storage/data/import)

---
### `gcloud composer environments storage data list`

List the data for a Cloud Composer environment

List the data for a Cloud Composer environment.

**Synopsis:**
```
gcloud composer environments storage data list
    (--environment=ENVIRONMENT : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--environment` | ENVIRONMENT |  | _[This must be specified.]_ ID of the environment or fully qualified identifier for the environment. To set the environment attribute: + provide the argument --environment on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Region where Composer environment runs or in which to create the environment. To set the location attribute: + provide the argument --environment on the command line with a fully specified name; + provide the argument --location on the command line; + set the property composer/location. |


**Examples:**
```bash
To list the data from the Cloud Composer environment environment-1 and
location us-central1, run:

    $ gcloud composer environments storage data list \
        --environment=environment-1 --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/environments/storage/data/list)

---

## `gcloud composer environments storage plugins` — manage plugins for Cloud Composer environments
### `gcloud composer environments storage plugins delete`

Delete plugins from an Cloud Composer environment's Cloud Storage bucket

Delete plugins from an Cloud Composer environment's Cloud Storage bucket.

**Synopsis:**
```
gcloud composer environments storage plugins delete [TARGET]
    (--environment=ENVIRONMENT : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[TARGET]
   A relative path to a file or subdirectory to delete within the plugins
   Cloud Storage subdirectory. If not specified, the entire contents of
   the plugins subdirectory will be deleted.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--environment` | ENVIRONMENT |  | _[This must be specified.]_ ID of the environment or fully qualified identifier for the environment. To set the environment attribute: + provide the argument --environment on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Region where Composer environment runs or in which to create the environment. To set the location attribute: + provide the argument --environment on the command line with a fully specified name; + provide the argument --location on the command line; + set the property composer/location. |


**Examples:**
```bash
To delete the plugins in the path path/to/plugins, for the environment
named environment-1 in the location us-east1, run:

    $ gcloud composer environments storage plugins delete \
        path/to/plugins --environment=environment-1 --location=us-east1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/environments/storage/plugins/delete)

---
### `gcloud composer environments storage plugins export`

Export plugins from an environment into local storage or Cloud Storage

If the SOURCE is a directory, it and its contents are are exported
recursively. If no SOURCE is provided, the entire contents of the
environment's plugins directory will be exported. Colliding files in the
DESTINATION will be overwritten. If a file exists in the DESTINATION but
there is no corresponding file to overwrite it, it is untouched.

**Synopsis:**
```
gcloud composer environments storage plugins export
    --destination=DESTINATION
    (--environment=ENVIRONMENT : --location=LOCATION) [--source=SOURCE]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | The path to an existing local directory or a Cloud Storage bucket/directory into which to export files. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source` | SOURCE |  | An optional relative path to a file or directory to be exported from the plugins/ subdirectory in the environment's Cloud Storage bucket. |


**Examples:**
```bash
Suppose the environment myenv's Cloud Storage bucket has the following
structure:

    gs://the-bucket
    |
    +-- plugins
    |   |
    |   +-- file1.py
    |   +-- file2.py
    |   |
    |   +-- subdir1
    |   |   |
    |   |   +-- file3.py
    |   |   +-- file4.py

And the local directory '/foo' has the following structure:

    /foo
    |
    +-- file1.py
    +-- fileX.py
    |   |
    |   +-- subdir1
    |   |   |
    |   |   +-- file3.py
    |   |   +-- fileY.py

The following command:

    gcloud composer environments storage plugins export myenv --destination=/foo

would result in the following structure in the local '/foo' directory:

    /foo
    |
    +-- file1.py
    +-- file2.py
    +-- fileX.py
    |   |
    |   +-- subdir1
    |   |   |
    |   |   +-- file3.py
    |   |   +-- file4.py
    |   |   +-- fileY.py

The local files '/foo/file1.py' and '/foo/subdir1/file3.py' will be
overwritten with the contents of the corresponding files in the Cloud
Storage bucket.

If instead we had run

    gcloud composer environments storage plugins export myenv file2.py subdir1/file3.py --destination=/foo

the resulting local directory structure would be the following:

    /foo
    |
    +-- file1.py
    +-- file3.py
    +-- fileX.py
    |   |
    |   +-- subdir1
    |   |   |
    |   |   +-- file3.py
    |   |   +-- fileY.py

No local files would be overwritten since
'gs://the-bucket/dags/subdir1/file3.py' was written to '/foo/file3.py'
instead of 'foo/subdir1/file3.py'.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/environments/storage/plugins/export)

---
### `gcloud composer environments storage plugins import`

Import plugins from local storage or Cloud Storage into an environment

If the SOURCE is a directory, it and its contents are imported recursively.
Colliding files in the environment's Cloud Storage bucket will be
overwritten. If a file exists in the bucket but is not present in the
SOURCE, it is not removed.

**Synopsis:**
```
gcloud composer environments storage plugins import --source=SOURCE
    (--environment=ENVIRONMENT : --location=LOCATION)
    [--destination=DESTINATION] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source` | SOURCE |  | Path to a local directory/file or Cloud Storage bucket/object to be imported into the plugins/ subdirectory in the environment's Cloud Storage bucket. Cloud Storage paths must begin with 'gs://'. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | An optional subdirectory under the plugins/ directory in the environment's Cloud Storage bucket into which to import files. May contain forward slashes to delimit multiple levels of subdirectory nesting, but should not contain leading or trailing slashes. If the DESTINATION does not exist, it will be created. |


**Examples:**
```bash
Suppose the '/foo' directory in the local filesystem has the following
structure:

    foo
    |
    +-- subdir1
    |   |
    |   +-- file1.txt
    |   +-- file2.txt
    |
    +-- subdir2
    |   |
    |   +-- file3.txt
    |   +-- file4.txt

And the environment myenv's Cloud Storage bucket has the following
structure:

    gs://the-bucket
    |
    +-- plugins
    |   |
    |   +-- foo
    |   |   |
    |   |   +-- subdir1
    |   |   |   |
    |   |   |   +-- bar.txt

The following command:

    gcloud composer environments storage plugins import myenv --source=/foo

would result in the following structure in myenv's Cloud Storage bucket:

    gs://the-bucket
    |
    +-- plugins
    |   |
    |   +-- foo
    |   |   |
    |   |   +-- subdir1
    |   |   |   |
    |   |   |   +-- bar.txt
    |   |   |   +-- file1.txt
    |   |   |   +-- file2.txt
    |   |   |
    |   |   +-- subdir2
    |   |   |   |
    |   |   |   +-- file3.txt
    |   |   |   +-- file4.txt

If instead we had run

    gcloud composer environments storage plugins import myenv --source=/foo --destination=bar

the resulting bucket structure would be the following:

    gs://the-bucket
    |
    +-- plugins
    |   |
    |   +-- foo
    |   |   |
    |   |   +-- subdir1
    |   |   |   |
    |   |   |   +-- bar.txt
    |   |
    |   +-- bar
    |   |   |
    |   |   +-- foo
    |   |   |   |
    |   |   |   +-- subdir1
    |   |   |   |   |
    |   |   |   |   +-- file1.txt
    |   |   |   |   +-- file2.txt
    |   |   |   |
    |   |   |   +-- subdir2
    |   |   |   |   |
    |   |   |   |   +-- file3.txt
    |   |   |   |   +-- file4.txt
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/environments/storage/plugins/import)

---
### `gcloud composer environments storage plugins list`

List the plugins for a Cloud Composer environment

List the plugins for a Cloud Composer environment.

**Synopsis:**
```
gcloud composer environments storage plugins list
    (--environment=ENVIRONMENT : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--environment` | ENVIRONMENT |  | _[This must be specified.]_ ID of the environment or fully qualified identifier for the environment. To set the environment attribute: + provide the argument --environment on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Region where Composer environment runs or in which to create the environment. To set the location attribute: + provide the argument --environment on the command line with a fully specified name; + provide the argument --location on the command line; + set the property composer/location. |


**Examples:**
```bash
To list the plugins for the Cloud Composer environment environment-1 and
location us-central1, run:

    $ gcloud composer environments storage plugins list \
        --environment=environment-1 --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/environments/storage/plugins/list)

---

## `gcloud composer environments user-workloads-config-maps` — create and manage user workloads ConfigMaps of environment
### `gcloud composer environments user-workloads-config-maps create`

Create a user workloads ConfigMap

Create a user workloads ConfigMap.

**Synopsis:**
```
gcloud composer environments user-workloads-config-maps create
    --config-map-file-path=CONFIG_MAP_FILE_PATH
    (--environment=ENVIRONMENT : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--config-map-file-path` | CONFIG_MAP_FILE_PATH |  | Path to a local file with a single Kubernetes ConfigMap in YAML format. |


**Examples:**
```bash
To create a user workloads ConfigMap of the environment named env-1, run:

    $ gcloud composer environments user-workloads-config-maps create \
        --environment=env-1 --config-map-file-path=config_map.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/environments/user-workloads-config-maps/create)

---
### `gcloud composer environments user-workloads-config-maps delete`

Delete a user workloads ConfigMap

Delete a user workloads ConfigMap.

**Synopsis:**
```
gcloud composer environments user-workloads-config-maps delete
    [CONFIG_MAP_NAME] (--environment=ENVIRONMENT : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[CONFIG_MAP_NAME]
   Name of the ConfigMap.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--environment` | ENVIRONMENT |  | _[This must be specified.]_ ID of the environment or fully qualified identifier for the environment. To set the environment attribute: + provide the argument --environment on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Region where Composer environment runs or in which to create the environment. To set the location attribute: + provide the argument --environment on the command line with a fully specified name; + provide the argument --location on the command line; + set the property composer/location. |


**Examples:**
```bash
To delete a user workloads ConfigMap of the environment named env-1, run:

    $ gcloud composer environments user-workloads-config-maps delete \
        config-map-1 --environment=env-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/environments/user-workloads-config-maps/delete)

---
### `gcloud composer environments user-workloads-config-maps describe`

Get details about a user workloads ConfigMap

Get details about a user workloads ConfigMap.

**Synopsis:**
```
gcloud composer environments user-workloads-config-maps describe
    [CONFIG_MAP_NAME] (--environment=ENVIRONMENT : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[CONFIG_MAP_NAME]
   Name of the ConfigMap.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--environment` | ENVIRONMENT |  | _[This must be specified.]_ ID of the environment or fully qualified identifier for the environment. To set the environment attribute: + provide the argument --environment on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Region where Composer environment runs or in which to create the environment. To set the location attribute: + provide the argument --environment on the command line with a fully specified name; + provide the argument --location on the command line; + set the property composer/location. |


**Examples:**
```bash
To get details about a user workloads ConfigMap of the environment named
env-1, run:

    $ gcloud composer environments user-workloads-config-maps describe \
        config-map-1 --environment=env-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/environments/user-workloads-config-maps/describe)

---
### `gcloud composer environments user-workloads-config-maps list`

List user workloads ConfigMaps

List user workloads ConfigMaps.

**Synopsis:**
```
gcloud composer environments user-workloads-config-maps list
    (--environment=ENVIRONMENT : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--environment` | ENVIRONMENT |  | _[This must be specified.]_ ID of the environment or fully qualified identifier for the environment. To set the environment attribute: + provide the argument --environment on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Region where Composer environment runs or in which to create the environment. To set the location attribute: + provide the argument --environment on the command line with a fully specified name; + provide the argument --location on the command line; + set the property composer/location. |


**Examples:**
```bash
To list user workloads ConfigMaps of the environment named env-1, run:

    $ gcloud composer environments user-workloads-config-maps list \
        --environment=env-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/environments/user-workloads-config-maps/list)

---
### `gcloud composer environments user-workloads-config-maps update`

Update a user workloads ConfigMap

Update a user workloads ConfigMap.

**Synopsis:**
```
gcloud composer environments user-workloads-config-maps update
    --config-map-file-path=CONFIG_MAP_FILE_PATH
    (--environment=ENVIRONMENT : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--config-map-file-path` | CONFIG_MAP_FILE_PATH |  | Path to a local file with a single Kubernetes ConfigMap in YAML format. |


**Examples:**
```bash
To update a user workloads ConfigMap of the environment named env-1, run:

    $ gcloud composer environments user-workloads-config-maps update \
        --environment=env-1 --config-map-file-path=config_map.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/environments/user-workloads-config-maps/update)

---

## `gcloud composer environments user-workloads-secrets` — create and manage user workloads Secrets of environment
### `gcloud composer environments user-workloads-secrets create`

Create a user workloads Secret

Create a user workloads Secret.

**Synopsis:**
```
gcloud composer environments user-workloads-secrets create
    --secret-file-path=SECRET_FILE_PATH
    (--environment=ENVIRONMENT : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--secret-file-path` | SECRET_FILE_PATH |  | Path to a local file with a single Kubernetes Secret in YAML format. |


**Examples:**
```bash
To create a user workloads Secret of the environment named env-1, run:

    $ gcloud composer environments user-workloads-secrets create \
        --environment=env-1 --secret-file-path=secret.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/environments/user-workloads-secrets/create)

---
### `gcloud composer environments user-workloads-secrets delete`

Delete a user workloads Secret

Delete a user workloads Secret.

**Synopsis:**
```
gcloud composer environments user-workloads-secrets delete [SECRET_NAME]
    (--environment=ENVIRONMENT : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[SECRET_NAME]
   Name of the Secret.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--environment` | ENVIRONMENT |  | _[This must be specified.]_ ID of the environment or fully qualified identifier for the environment. To set the environment attribute: + provide the argument --environment on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Region where Composer environment runs or in which to create the environment. To set the location attribute: + provide the argument --environment on the command line with a fully specified name; + provide the argument --location on the command line; + set the property composer/location. |


**Examples:**
```bash
To delete a user workloads Secret of the environment named env-1, run:

    $ gcloud composer environments user-workloads-secrets delete \
        secret-1 --environment=env-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/environments/user-workloads-secrets/delete)

---
### `gcloud composer environments user-workloads-secrets describe`

Get details about a user workloads Secret

Get details about a user workloads Secret.

**Synopsis:**
```
gcloud composer environments user-workloads-secrets describe [SECRET_NAME]
    (--environment=ENVIRONMENT : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[SECRET_NAME]
   Name of the Secret.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--environment` | ENVIRONMENT |  | _[This must be specified.]_ ID of the environment or fully qualified identifier for the environment. To set the environment attribute: + provide the argument --environment on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Region where Composer environment runs or in which to create the environment. To set the location attribute: + provide the argument --environment on the command line with a fully specified name; + provide the argument --location on the command line; + set the property composer/location. |


**Examples:**
```bash
To get details about a user workloads Secret of the environment named
env-1, run:

    $ gcloud composer environments user-workloads-secrets describe \
        secret-1 --environment=env-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/environments/user-workloads-secrets/describe)

---
### `gcloud composer environments user-workloads-secrets list`

List user workloads Secrets

List user workloads Secrets.

**Synopsis:**
```
gcloud composer environments user-workloads-secrets list
    (--environment=ENVIRONMENT : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--environment` | ENVIRONMENT |  | _[This must be specified.]_ ID of the environment or fully qualified identifier for the environment. To set the environment attribute: + provide the argument --environment on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Region where Composer environment runs or in which to create the environment. To set the location attribute: + provide the argument --environment on the command line with a fully specified name; + provide the argument --location on the command line; + set the property composer/location. |


**Examples:**
```bash
To list user workloads Secrets of the environment named env-1, run:

    $ gcloud composer environments user-workloads-secrets list \
        --environment=env-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/environments/user-workloads-secrets/list)

---
### `gcloud composer environments user-workloads-secrets update`

Update a user workloads Secret

Update a user workloads Secret.

**Synopsis:**
```
gcloud composer environments user-workloads-secrets update
    --secret-file-path=SECRET_FILE_PATH
    (--environment=ENVIRONMENT : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--secret-file-path` | SECRET_FILE_PATH |  | Path to a local file with a single Kubernetes Secret in YAML format. |


**Examples:**
```bash
To update a user workloads Secret of the environment named env-1, run:

    $ gcloud composer environments user-workloads-secrets update \
        --environment=env-1 --secret-file-path=secret.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/environments/user-workloads-secrets/update)

---
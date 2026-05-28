# gcloud managed-kafka connectors

administer Managed Service for Apache Kafka connectors

### `gcloud managed-kafka connectors create`

Create a Managed Service for Apache Kafka connector

Create a Managed Service for Apache Kafka connector.

**Synopsis:**
```
gcloud managed-kafka connectors create
    (CONNECTOR : --connect-cluster=CONNECT_CLUSTER --location=LOCATION)
    (--config-file=JSON|YAML|FILE | --configs=[KEY=VALUE,...])
    [--task-retry-disabled]
    [--task-restart-max-backoff=TASK_RESTART_MAX_BACKOFF
      --task-restart-min-backoff=TASK_RESTART_MIN_BACKOFF]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connector resource - Identifies the connector for which the command runs.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument connector on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTOR
     ID of the connector or fully qualified identifier for the connector.

     To set the connector attribute:
     + provide the argument connector on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --connect-cluster=CONNECT_CLUSTER
     The connect cluster name.

     To set the connect-cluster attribute:
     + provide the argument connector on the command line with a fully
       specified name;
     + provide the argument --connect-cluster on the command line.

  --location=LOCATION
     ID of the location of the Managed Service for Apache Kafka resource.
     See
     https://cloud.google.com/managed-service-for-apache-kafka/docs/locations
     for a list of supported locations.

     To set the location attribute:
     + provide the argument connector on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--config-file` | JSON\|YAML\|FILE |  | _[Exactly one of these must be specified:]_ The path to the JSON or YAML file containing the configuration that are overridden from the connector defaults. This also supports inline JSON or YAML. Sets config_file value. Input Example: --config-file=string File Example: --config-file=path_to_file.(yaml\|json) |
| `--configs` | [KEY=VALUE,...] |  | _[Exactly one of these must be specified:]_ Configuration for the connector that are overridden from the connector defaults. The key of the map is a Kafka topic property name, for example: cleanup.policy=compact,compression.type=producer. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--task-retry-disabled` |  |  | Disable default task retry policy. |
| `--task-restart-max-backoff` | TASK_RESTART_MAX_BACKOFF |  | The maximum amount of time to wait before retrying a failed task in seconds. This sets an upper bound for the backoff delay. The default value is 1800s (30 minutes). See $ gcloud topic datetimes for information on duration formats. |
| `--task-restart-min-backoff` | TASK_RESTART_MIN_BACKOFF |  | The minimum amount of time to wait before retrying a failed task in seconds. This sets a lower bound for the backoff delay. The default value is 60s. See $ gcloud topic datetimes for information on duration formats. |


**Examples:**
```bash
To create a connector, run the following:

    $ gcloud managed-kafka connectors create myconnector \
        --location=us-central1 --connect-cluster=mycluster \
        --configs=connector.class="com.google.pubsub.kafka.source.CloudP\
    ubSubSourceConnector",cps.subscription="my-subscription",... \
        [--task-restart-min-backoff=60s] \
        [--task-restart-max-backoff=30m] [--task-retry-disabled=true] OR
    $ gcloud managed-kafka connectors create myconnector \
        --location=us-central1 --connect-cluster=mycluster \
        --config-file=my-config-file.yaml \
        [--task-restart-min-backoff=60s] \
        [--task-restart-max-backoff=30m] [--task-retry-disabled=true]
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/managed-kafka/connectors/create)

---
### `gcloud managed-kafka connectors delete`

Delete a Managed Service for Apache Kafka connector

Delete a Managed Service for Apache Kafka connector.

**Synopsis:**
```
gcloud managed-kafka connectors delete
    (CONNECTOR : --connect-cluster=CONNECT_CLUSTER --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connector resource - Identifies the cluster for deletion. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument connector on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTOR
     ID of the connector or fully qualified identifier for the connector.

     To set the connector attribute:
     + provide the argument connector on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --connect-cluster=CONNECT_CLUSTER
     The connect cluster name.

     To set the connect-cluster attribute:
     + provide the argument connector on the command line with a fully
       specified name;
     + provide the argument --connect-cluster on the command line.

  --location=LOCATION
     ID of the location of the Managed Service for Apache Kafka resource.
     See
     https://cloud.google.com/managed-service-for-apache-kafka/docs/locations
     for a list of supported locations.

     To set the location attribute:
     + provide the argument connector on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To delete a connector named myconnector located in us-central1, run the
following:

    $ gcloud managed-kafka connectors delete myconnector \
        --location=us-central1 --connect-cluster=mycluster
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/managed-kafka/connectors/delete)

---
### `gcloud managed-kafka connectors describe`

Describe a Managed Service for Apache Kafka connector

Describe a Managed Service for Apache Kafka connector.

**Synopsis:**
```
gcloud managed-kafka connectors describe
    (CONNECTOR : --connect-cluster=CONNECT_CLUSTER --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connector resource - Identifies the connector for details to be displayed.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument connector on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTOR
     ID of the connector or fully qualified identifier for the connector.

     To set the connector attribute:
     + provide the argument connector on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --connect-cluster=CONNECT_CLUSTER
     The connect cluster name.

     To set the connect-cluster attribute:
     + provide the argument connector on the command line with a fully
       specified name;
     + provide the argument --connect-cluster on the command line.

  --location=LOCATION
     ID of the location of the Managed Service for Apache Kafka resource.
     See
     https://cloud.google.com/managed-service-for-apache-kafka/docs/locations
     for a list of supported locations.

     To set the location attribute:
     + provide the argument connector on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe a connector named myconnector located in us-central1, run the
following:

    $ gcloud managed-kafka connectors describe myconnector \
        --location=us-central1 --connect-cluster=mycluster
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/managed-kafka/connectors/describe)

---
### `gcloud managed-kafka connectors list`

List all Managed Service for Apache Kafka connectors for a given connect cluster

List all Managed Service for Apache Kafka connectors for a given connect
cluster. To specify the maximum number of connectors to list, use the
--limit flag.

**Synopsis:**
```
gcloud managed-kafka connectors list
    (CONNECT_CLUSTER : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connect cluster resource - Identifies the cluster which contains all the
connectors to be listed. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument connect_cluster on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECT_CLUSTER
     ID of the connect_cluster or fully qualified identifier for the
     connect_cluster.

     To set the connect_cluster attribute:
     + provide the argument connect_cluster on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     ID of the location of the Managed Service for Apache Kafka resource.
     See
     https://cloud.google.com/managed-service-for-apache-kafka/docs/locations
     for a list of supported locations.

     To set the location attribute:
     + provide the argument connect_cluster on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To list all Managed Service for Apache Kafka connectors belonging to the
"mycluster" connect cluster in us-central1, run the following:

    $ gcloud managed-kafka connectors list mycluster \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/managed-kafka/connectors/list)

---
### `gcloud managed-kafka connectors pause`

Pauses operation of a Managed Service for Apache Kafka connector

Pauses operation of a Managed Service for Apache Kafka connector.

**Synopsis:**
```
gcloud managed-kafka connectors pause
    (CONNECTOR : --connect-cluster=CONNECT_CLUSTER --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connector resource - Identifies the connector to pause. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument connector on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTOR
     ID of the connector or fully qualified identifier for the connector.

     To set the connector attribute:
     + provide the argument connector on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --connect-cluster=CONNECT_CLUSTER
     The connect cluster name.

     To set the connect-cluster attribute:
     + provide the argument connector on the command line with a fully
       specified name;
     + provide the argument --connect-cluster on the command line.

  --location=LOCATION
     ID of the location of the Managed Service for Apache Kafka resource.
     See
     https://cloud.google.com/managed-service-for-apache-kafka/docs/locations
     for a list of supported locations.

     To set the location attribute:
     + provide the argument connector on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To pause a connector named myconnector located in us-central1, run the
following:

    $ gcloud managed-kafka connectors pause myconnector \
        --location=us-central1 --connect-cluster=mycluster
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/managed-kafka/connectors/pause)

---
### `gcloud managed-kafka connectors restart`

Restarts a Managed Service for Apache Kafka connector

Restarts a Managed Service for Apache Kafka connector.

**Synopsis:**
```
gcloud managed-kafka connectors restart
    (CONNECTOR : --connect-cluster=CONNECT_CLUSTER --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connector resource - Identifies the connector to restart. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument connector on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTOR
     ID of the connector or fully qualified identifier for the connector.

     To set the connector attribute:
     + provide the argument connector on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --connect-cluster=CONNECT_CLUSTER
     The connect cluster name.

     To set the connect-cluster attribute:
     + provide the argument connector on the command line with a fully
       specified name;
     + provide the argument --connect-cluster on the command line.

  --location=LOCATION
     ID of the location of the Managed Service for Apache Kafka resource.
     See
     https://cloud.google.com/managed-service-for-apache-kafka/docs/locations
     for a list of supported locations.

     To set the location attribute:
     + provide the argument connector on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To restart a connector named myconnector located in us-central1, run the
following:

    $ gcloud managed-kafka connectors restart myconnector \
        --location=us-central1 --connect-cluster=mycluster
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/managed-kafka/connectors/restart)

---
### `gcloud managed-kafka connectors resume`

Resumes operation of a stopped Managed Service for Apache Kafka connector

Resumes operation of a stopped Managed Service for Apache Kafka connector.

**Synopsis:**
```
gcloud managed-kafka connectors resume
    (CONNECTOR : --connect-cluster=CONNECT_CLUSTER --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connector resource - Identifies the connector to resume. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument connector on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTOR
     ID of the connector or fully qualified identifier for the connector.

     To set the connector attribute:
     + provide the argument connector on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --connect-cluster=CONNECT_CLUSTER
     The connect cluster name.

     To set the connect-cluster attribute:
     + provide the argument connector on the command line with a fully
       specified name;
     + provide the argument --connect-cluster on the command line.

  --location=LOCATION
     ID of the location of the Managed Service for Apache Kafka resource.
     See
     https://cloud.google.com/managed-service-for-apache-kafka/docs/locations
     for a list of supported locations.

     To set the location attribute:
     + provide the argument connector on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To resume a connector named myconnector located in us-central1, run the
following:

    $ gcloud managed-kafka connectors resume myconnector \
        --location=us-central1 --connect-cluster=mycluster
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/managed-kafka/connectors/resume)

---
### `gcloud managed-kafka connectors stop`

Stops operation of a Managed Service for Apache Kafka connector

Stops operation of a Managed Service for Apache Kafka connector.

**Synopsis:**
```
gcloud managed-kafka connectors stop
    (CONNECTOR : --connect-cluster=CONNECT_CLUSTER --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connector resource - Identifies the connector to resume. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument connector on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTOR
     ID of the connector or fully qualified identifier for the connector.

     To set the connector attribute:
     + provide the argument connector on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --connect-cluster=CONNECT_CLUSTER
     The connect cluster name.

     To set the connect-cluster attribute:
     + provide the argument connector on the command line with a fully
       specified name;
     + provide the argument --connect-cluster on the command line.

  --location=LOCATION
     ID of the location of the Managed Service for Apache Kafka resource.
     See
     https://cloud.google.com/managed-service-for-apache-kafka/docs/locations
     for a list of supported locations.

     To set the location attribute:
     + provide the argument connector on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To stop a connector named myconnector located in us-central1, run the
following:

    $ gcloud managed-kafka connectors stop myconnector \
        --location=us-central1 --connect-cluster=mycluster
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/managed-kafka/connectors/stop)

---
### `gcloud managed-kafka connectors update`

Update a Managed Service for Apache Kafka connector

Update a Managed Service for Apache Kafka connector.

**Synopsis:**
```
gcloud managed-kafka connectors update
    (CONNECTOR : --connect-cluster=CONNECT_CLUSTER --location=LOCATION)
    [--task-retry-disabled]
    [--config-file=JSON|YAML|FILE | --configs=[KEY=VALUE,...]]
    [--task-restart-max-backoff=TASK_RESTART_MAX_BACKOFF
      --task-restart-min-backoff=TASK_RESTART_MIN_BACKOFF]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connector resource - Identifies the connector for which the command runs.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument connector on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTOR
     ID of the connector or fully qualified identifier for the connector.

     To set the connector attribute:
     + provide the argument connector on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --connect-cluster=CONNECT_CLUSTER
     The connect cluster name.

     To set the connect-cluster attribute:
     + provide the argument connector on the command line with a fully
       specified name;
     + provide the argument --connect-cluster on the command line.

  --location=LOCATION
     ID of the location of the Managed Service for Apache Kafka resource.
     See
     https://cloud.google.com/managed-service-for-apache-kafka/docs/locations
     for a list of supported locations.

     To set the location attribute:
     + provide the argument connector on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--task-retry-disabled` |  |  | Disable default task retry policy. |
| `--task-restart-max-backoff` | TASK_RESTART_MAX_BACKOFF |  | _[name, for example: cleanup.policy=compact,compression.type=producer.]_ The maximum amount of time to wait before retrying a failed task in seconds. This sets an upper bound for the backoff delay. The default value is 1800s (30 minutes). See $ gcloud topic datetimes for information on duration formats. |
| `--task-restart-min-backoff` | TASK_RESTART_MIN_BACKOFF |  | _[name, for example: cleanup.policy=compact,compression.type=producer.]_ The minimum amount of time to wait before retrying a failed task in seconds. This sets a lower bound for the backoff delay. The default value is 60s. See $ gcloud topic datetimes for information on duration formats. |


**Examples:**
```bash
To update a connector name myconnector, run the following:

    $ gcloud managed-kafka connectors update myconnector \
        --location=us-central1 --configs=KEY1=VALUE1,KEY2=VALUE2... \
        --connect-cluster=mycluster [--task-restart-min-backoff=60s] \
        [--task-restart-max-backoff=30m] [--task-retry-disabled=true] OR
    $ gcloud managed-kafka connectors update myconnector \
        --location=us-central1 --config-file=my-config-file.yaml \
        --connect-cluster=mycluster [--task-restart-min-backoff=60s] \
        [--task-restart-max-backoff=30m] [--task-retry-disabled=true]
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/managed-kafka/connectors/update)

---
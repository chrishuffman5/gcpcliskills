# gcloud managed-kafka acls

administer Managed Service for Apache Kafka acls

### `gcloud managed-kafka acls add-acl-entry`

Add an acl entry to a Managed Service for Apache Kafka acl

Add an acl entry to a Managed Service for Apache Kafka acl.

**Synopsis:**
```
gcloud managed-kafka acls add-acl-entry
    (ACL : --cluster=CLUSTER --location=LOCATION) --operation=OPERATION
    --principal=PRINCIPAL [--host=HOST; default="*"]
    [--permission-type=PERMISSION_TYPE; default="ALLOW"]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Acl resource - Identifies the acl that this command updates.

The structure of the acl ID defines the Resource Pattern for which the acl
entries apply in the Kafka cluster. The acl ID must be structured like one
of the following:

    For acls on the cluster:
      cluster

    For acls on a single resource within the cluster:
      topic/{resource_name}
      consumerGroup/{resource_name}
      transactionalId/{resource_name}

    For acls on all resources that match a prefix:
      topicPrefixed/{resource_name}
      consumerGroupPrefixed/{resource_name}
      transactionalIdPrefixed/{resource_name}

    For acls on all resources of a given type (i.e. the wildcard literal "*"):
      allTopics (represents topic/*)
      allConsumerGroups (represents consumerGroup/*)
      allTransactionalIds (represents transactionalId/*)
    The arguments in this group can be used to specify the attributes of this resource. (NOTE) Some attributes are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument acl on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ACL
     ID of the acl or fully qualified identifier for the acl.

     To set the acl attribute:
     + provide the argument acl on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     The cluster name.

     To set the cluster attribute:
     + provide the argument acl on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line.

  --location=LOCATION
     ID of the location of the Managed Service for Apache Kafka resource.
     See
     https://cloud.google.com/managed-service-for-apache-kafka/docs/locations
     for a list of supported locations.

     To set the location attribute:
     + provide the argument acl on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--operation` | OPERATION |  | The operation type. Allowed values are: ALL, READ, WRITE, CREATE, DELETE, ALTER, DESCRIBE, CLUSTER_ACTION, DESCRIBE_CONFIGS, ALTER_CONFIGS, IDEMPOTENT_WRITE. See https://kafka.apache.org/documentation/#operations_resources_and_protocols for the mapping of operations to Kafka protocols. |
| `--principal` | PRINCIPAL |  | The principal. Specified as Google Cloud account, with the Kafka StandardAuthorizer prefix "User:". For example: "User:admin@project.iam.gserviceaccount.com". Can be the wildcard "User:*" to refer to all users. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--host` | HOST | * | The host. Must be set to "*" for Managed Service for Apache Kafka. |
| `--permission-type` | PERMISSION_TYPE | ALLOW | The permission type. Allowed values are: ALLOW, DENY. |


**Examples:**
```bash
To add an acl entry for the Kafka cluster resource pattern (acl ID =
cluster), in a cluster named mycluster located in us-central1, run the
following:

    $ gcloud managed-kafka acls add-acl-entry cluster \
        --cluster=mycluster --location=us-central1 \
        --principal='User:admin@project.iam.gserviceaccount.com' \
        --operation=ALL --permission-type=ALLOW --host='*'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/managed-kafka/acls/add-acl-entry)

---
### `gcloud managed-kafka acls create`

Create a Managed Service for Apache Kafka acl

Create a Managed Service for Apache Kafka acl.

**Synopsis:**
```
gcloud managed-kafka acls create
    (ACL : --cluster=CLUSTER --location=LOCATION)
    (--acl-entries-from-file=PATH_TO_FILE
      | --acl-entry=[host=HOST],[operation=OPERATION],
      [permission-type=PERMISSION-TYPE],[principal=PRINCIPAL])
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Acl resource - Identifies the name of the acl that this command creates.

The structure of the acl ID defines the Resource Pattern for which the acl
entries apply in the Kafka cluster. The acl ID must be structured like one
of the following:

    For acls on the cluster:
      cluster

    For acls on a single resource within the cluster:
      topic/{resource_name}
      consumerGroup/{resource_name}
      transactionalId/{resource_name}

    For acls on all resources that match a prefix:
      topicPrefixed/{resource_name}
      consumerGroupPrefixed/{resource_name}
      transactionalIdPrefixed/{resource_name}

    For acls on all resources of a given type (i.e. the wildcard literal "*"):
      allTopics (represents topic/*)
      allConsumerGroups (represents consumerGroup/*)
      allTransactionalIds (represents transactionalId/*)
    The arguments in this group can be used to specify the attributes of this resource. (NOTE) Some attributes are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument acl on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ACL
     ID of the acl or fully qualified identifier for the acl.

     To set the acl attribute:
     + provide the argument acl on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     The cluster name.

     To set the cluster attribute:
     + provide the argument acl on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line.

  --location=LOCATION
     ID of the location of the Managed Service for Apache Kafka resource.
     See
     https://cloud.google.com/managed-service-for-apache-kafka/docs/locations
     for a list of supported locations.

     To set the location attribute:
     + provide the argument acl on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--acl-entries-from-file` | PATH_TO_FILE |  | _[Exactly one of these must be specified:]_ Path to a JSON or YAML file containing the acl entries to use in the acl. Use a full or relative path to a local file containing the value of acl_entries. |
| `--acl-entry` | [host=HOST],[operation=OPERATION],[permission-type=PERMISSION-TYPE],[principal=PRINCIPAL] |  | _[Exactly one of these must be specified:]_ An acl entry that configures access for a principal, for a specific operation on the acl's resource pattern. This flag can be repeated. PRINCIPAL is the principal. Specified as Google Cloud account, with the Kafka StandardAuthorizer prefix "User:". For example: "User:admin@project.iam.gserviceaccount.com". Can be the wildcard "User:*" to refer to all users. OPERATION is the operation type. Allowed values are: ALL, READ, WRITE, CREATE, DELETE, ALTER, DESCRIBE, CLUSTER_ACTION, DESCRIBE_CONFIGS, ALTER_CONFIGS, IDEMPOTENT_WRITE. PERMISSION-TYPE is the permission type. Allowed values are: ALLOW, DENY. HOST is the host. Must be set to "*" for Managed Service for Apache Kafka. Example acl-entry: "principal=User:admin@project.iam.gserviceaccount.com,operation=ALL,permission-type=ALLOW,host=*" |


**Examples:**
```bash
To create an acl for the Kafka cluster resource pattern (acl ID = cluster),
in a cluster named mycluster located in us-central1, run the following:

    $ gcloud managed-kafka acls create cluster --cluster=mycluster \
      --location=us-central1 \
      --acl-entry=principal='User:admin@project.iam.gserviceaccount.co\
    m',operation=ALL,permission-type=ALLOW,host='*' \
        --acl-entry=principal='User:reader@project.iam.gserviceaccount.c\
    om',operation=DESCRIBE,permission-type=ALLOW,host='*' \
        --acl-entry=principal='User:reader@project.iam.gserviceaccount.c\
    om',operation=DESCRIBE_CONFIGS,permission-type=ALLOW,host='*'

This acl grants an "admin" service account access to ALL cluster-level
operations, and grants a "reader" service account access to cluster-level
DESCRIBE and DESCRIBE_CONFIGS operations.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/managed-kafka/acls/create)

---
### `gcloud managed-kafka acls delete`

Delete a Managed Service for Apache Kafka ACL

Delete a Managed Service for Apache Kafka ACL.

**Synopsis:**
```
gcloud managed-kafka acls delete
    (ACL : --cluster=CLUSTER --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Acl resource - Identifies the acl for deletion.

The structure of the acl ID defines the Resource Pattern for which the acl
entries apply in the Kafka cluster. The acl ID must be structured like one
of the following:

    For acls on the cluster:
      cluster

    For acls on a single resource within the cluster:
      topic/{resource_name}
      consumerGroup/{resource_name}
      transactionalId/{resource_name}

    For acls on all resources that match a prefix:
      topicPrefixed/{resource_name}
      consumerGroupPrefixed/{resource_name}
      transactionalIdPrefixed/{resource_name}

    For acls on all resources of a given type (i.e. the wildcard literal "*"):
      allTopics (represents topic/*)
      allConsumerGroups (represents consumerGroup/*)
      allTransactionalIds (represents transactionalId/*)
    The arguments in this group can be used to specify the attributes of this resource. (NOTE) Some attributes are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument acl on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ACL
     ID of the acl or fully qualified identifier for the acl.

     To set the acl attribute:
     + provide the argument acl on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     The cluster name.

     To set the cluster attribute:
     + provide the argument acl on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line.

  --location=LOCATION
     ID of the location of the Managed Service for Apache Kafka resource.
     See
     https://cloud.google.com/managed-service-for-apache-kafka/docs/locations
     for a list of supported locations.

     To set the location attribute:
     + provide the argument acl on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To delete an acl for all topics, in a cluster named mycluster located in
us-central1, run the following:

    $ gcloud managed-kafka acls delete allTopics --cluster=mycluster \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/managed-kafka/acls/delete)

---
### `gcloud managed-kafka acls describe`

Describe a Managed Service for Apache Kafka acl

Describe a Managed Service for Apache Kafka acl.

**Synopsis:**
```
gcloud managed-kafka acls describe
    (ACL : --cluster=CLUSTER --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Acl resource - The describe command displays properties of the acl
specified by this parameter. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument acl on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ACL
     ID of the acl or fully qualified identifier for the acl.

     To set the acl attribute:
     + provide the argument acl on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     The cluster name.

     To set the cluster attribute:
     + provide the argument acl on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line.

  --location=LOCATION
     ID of the location of the Managed Service for Apache Kafka resource.
     See
     https://cloud.google.com/managed-service-for-apache-kafka/docs/locations
     for a list of supported locations.

     To set the location attribute:
     + provide the argument acl on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe an acl for the consumer group mygroup, in a cluster named
mycluster located in us-central1, run the following:

    $ gcloud managed-kafka acls describe consumerGroup/mygroup \
        --cluster=mycluster --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/managed-kafka/acls/describe)

---
### `gcloud managed-kafka acls list`

List all Managed Service for Apache Kafka acls in a given cluster

List all Managed Service for Apache Kafka acls in a given cluster. To
specify the maximum number of acls to list, use the --limit flag.

**Synopsis:**
```
gcloud managed-kafka acls list (CLUSTER : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - Identifies the cluster which contains all the acls to
be listed. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument cluster on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CLUSTER
     ID of the cluster or fully qualified identifier for the cluster.

     To set the cluster attribute:
     + provide the argument cluster on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     ID of the location of the Managed Service for Apache Kafka resource.
     See
     https://cloud.google.com/managed-service-for-apache-kafka/docs/locations
     for a list of supported locations.

     To set the location attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To list acls in a cluster named mycluster located in us-central1, run the
following:

    $ gcloud managed-kafka acls list mycluster --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/managed-kafka/acls/list)

---
### `gcloud managed-kafka acls remove-acl-entry`

Remove an acl entry from a Managed Service for Apache Kafka acl

Remove an acl entry from a Managed Service for Apache Kafka acl.

**Synopsis:**
```
gcloud managed-kafka acls remove-acl-entry
    (ACL : --cluster=CLUSTER --location=LOCATION) --operation=OPERATION
    --principal=PRINCIPAL [--host=HOST; default="*"]
    [--permission-type=PERMISSION_TYPE; default="ALLOW"]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Acl resource - Identifies the name of the acl that this command updates.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument acl on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ACL
     ID of the acl or fully qualified identifier for the acl.

     To set the acl attribute:
     + provide the argument acl on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     The cluster name.

     To set the cluster attribute:
     + provide the argument acl on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line.

  --location=LOCATION
     ID of the location of the Managed Service for Apache Kafka resource.
     See
     https://cloud.google.com/managed-service-for-apache-kafka/docs/locations
     for a list of supported locations.

     To set the location attribute:
     + provide the argument acl on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--operation` | OPERATION |  | The operation type. Allowed values are: ALL, READ, WRITE, CREATE, DELETE, ALTER, DESCRIBE, CLUSTER_ACTION, DESCRIBE_CONFIGS, ALTER_CONFIGS, IDEMPOTENT_WRITE. See https://kafka.apache.org/documentation/#operations_resources_and_protocols for the mapping of operations to Kafka protocols. |
| `--principal` | PRINCIPAL |  | The principal. Specified as Google Cloud account, with the Kafka StandardAuthorizer prefix "User:". For example: "User:admin@project.iam.gserviceaccount.com". Can be the wildcard "User:*" to refer to all users. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--host` | HOST | * | The host. Must be set to "*" for Managed Service for Apache Kafka. |
| `--permission-type` | PERMISSION_TYPE | ALLOW | The permission type. Allowed values are: ALLOW, DENY. |


**Examples:**
```bash
To remove an acl entry for the Kafka cluster resource pattern
(acl_id=cluster), in a cluster named mycluster located in us-central1, run
the following:

    $ gcloud managed-kafka acls remove-acl-entry cluster \
        --cluster=mycluster --location=us-central1 \
        --principal='User:admin@project.iam.gserviceaccount.com' \
        --operation=ALL --permission-type=ALLOW --host='*'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/managed-kafka/acls/remove-acl-entry)

---
### `gcloud managed-kafka acls update`

Update a Managed Service for Apache Kafka acl

Update a Managed Service for Apache Kafka acl.

NOTE: update performs a FULL REPLACEMENT of acl entries. For incremental
updates, use add-acl-entry and remove-acl-entry commands.

**Synopsis:**
```
gcloud managed-kafka acls update
    (ACL : --cluster=CLUSTER --location=LOCATION) --etag=ETAG
    (--acl-entries-from-file=PATH_TO_FILE
      | --acl-entry=[host=HOST],[operation=OPERATION],
      [permission-type=PERMISSION-TYPE],[principal=PRINCIPAL])
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Acl resource - Identifies the name of the acl that this command updates.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument acl on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ACL
     ID of the acl or fully qualified identifier for the acl.

     To set the acl attribute:
     + provide the argument acl on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     The cluster name.

     To set the cluster attribute:
     + provide the argument acl on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line.

  --location=LOCATION
     ID of the location of the Managed Service for Apache Kafka resource.
     See
     https://cloud.google.com/managed-service-for-apache-kafka/docs/locations
     for a list of supported locations.

     To set the location attribute:
     + provide the argument acl on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--etag` | ETAG |  | etag returned in the response to a previous create or describe command. The etag is used for concurrency control, to ensure that the client and server agree on the current set of acl entries in the Kafka cluster, before full replacement in the update command. |


**Examples:**
```bash
To update an acl for the Kafka cluster resource pattern, with etag W/XYZ123
returned from a previous create or describe command, in a cluster named
mycluster located in us-central1, run the following:

    $ gcloud managed-kafka acls update cluster --cluster=mycluster \
        --location=us-central1 \
        --acl-entry=principal='User:admin@project.iam.gserviceaccount.co\
    m',operation=ALL,permission-type=ALLOW,host='*' --etag=W/XYZ123
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/managed-kafka/acls/update)

---
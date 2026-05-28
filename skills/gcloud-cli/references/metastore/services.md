# gcloud metastore services

manage Dataproc Metastore services

### `gcloud metastore services add-iam-policy-binding`

Add an IAM policy binding to a service

Add an IAM policy binding to a service.

**Synopsis:**
```
gcloud metastore services add-iam-policy-binding
    (SERVICE : --location=LOCATION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - Service for which to add the IAM policy to. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataproc Metastore service.

     If not specified, will use default metastore/location.

     To set the location attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property metastore/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Examples:**
```bash
To add an IAM policy binding for the role of 'roles/metastore.admin' for
the user 'test-user@gmail.com', run:

    $ gcloud metastore services add-iam-policy-binding my-service \
        --member='user:test-user@gmail.com' \
        --role='roles/metastore.admin'

See https://cloud.google.com/dataproc-metastore/docs/iam-and-access-control
for details of policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/services/add-iam-policy-binding)

---
### `gcloud metastore services alter-metadata-resource-location`

Alter metadata resource location

Alter metadata resource location from a Dataproc Metastore service's
underlying metadata store.

If run asynchronously with --async, exits after printing one operation name
that can be used to poll the status of the creation via:

    gcloud metastore operations describe

**Synopsis:**
```
gcloud metastore services alter-metadata-resource-location
    (SERVICE : --location=LOCATION) --location_uri=LOCATION_URI
    --resource_name=RESOURCE_NAME [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - Arguments and flags that specify the resource and the
location you want to alter. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataproc Metastore service.

     If not specified, will use default metastore/location.

     To set the location attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property metastore/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION_URI |  | The new location URI for the metadata resource. |
| `--resource` | RESOURCE_NAME |  | The relative metadata resource name in the following format. databases/{database_id} or databases/{database_id}/tables/{table_id} or databases/{database_id}/tables/{table_id}/partitions/{partition_id} |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To alter metadata resource location with the resource_name
databases/{database_id} or databases/{database_id}/tables/{table_id} or and
location_uri in location us-central, run:

    $ gcloud metastore services alter-metadata-resource-location \
      my-metastore-service --location=us-central1 \
      --resource_name=databases/my-db \
      --location_uri=gs://destination_bucket/destination_object
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/services/alter-metadata-resource-location)

---
### `gcloud metastore services alter-table-properties`

Alter metadata table properties

Alter metadata table properties from a Dataproc Metastore service's
underlying metadata store.

If run asynchronously with --async, exits after printing one operation name
that can be used to poll the status of the creation via:

    gcloud metastore operations describe

**Synopsis:**
```
gcloud metastore services alter-table-properties
    (SERVICE : --location=LOCATION) --properties=[KEY=VALUE,...]
    --table-name=TABLE_NAME --update-mask=UPDATE_MASK [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - Arguments and flags that specify the table you want to
alter. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataproc Metastore service.

     If not specified, will use default metastore/location.

     To set the location attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property metastore/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--properties` | [KEY=VALUE,...] |  | A string where field names are separated by a comma. Describes the desired values to mutate. If update-mask is empty, the properties will not update. Otherwise, the properties only alter the values whose associated paths exist in the update mask. For example, the desired key-value pairs. a=2,b=3,c=4 |
| `--table-name` | TABLE_NAME |  | The name of the table containing the properties you're altering in the following format. databases/{database_id}/tables/{table_id} |
| `--update-mask` | UPDATE_MASK |  | A string where field names are separated by a comma. Specifies the metadata table properties fields that are overwritten by the update. Fields specified in the update-mask are relative to the resource (not to the full request). A field is overwritten if it is in the mask. For example, given the target properties: properties { a: 1 b: 2 } And an update properties: properties { a: 2 b: 3 c: 4 } then if the field mask is: properties.b,properties.c then the updated result will be: properties { a: 1 b: 3 c: 4 } |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To alter metadata table properties a and b on table-name
databases/{database_id}/tables/{table_id} , use the update-mask
properties.a,properties.b , and run:

    $ gcloud metastore services alter-table-properties \
      my-metastore-service --location=us-central1 \
      --table-name=databases/my-database/tables/my-table \
      --update-mask=properties.a,properties.b --properties=a=1,b=2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/services/alter-table-properties)

---
### `gcloud metastore services create`

Create a Dataproc Metastore service

Create a new Dataproc Metastore service with the given name and
configurations.

If run asynchronously with --async, exits after printing one operation name
that can be used to poll the status of the creation via:

    gcloud metastore operations describe

**Synopsis:**
```
gcloud metastore services create (SERVICE : --location=LOCATION) [--async]
    [--autoscaling-enabled] [--data-catalog-sync]
    [--database-type=DATABASE_TYPE; default="mysql"]
    [--deletion-protection] [--encryption-kms-key=ENCRYPTION_KMS_KEY]
    [--endpoint-protocol=ENDPOINT_PROTOCOL; default="thrift"]
    [--hive-metastore-version=HIVE_METASTORE_VERSION]
    [--labels=[KEY=VALUE,...]] [--port=PORT; default=9083]
    [--release-channel=RELEASE_CHANNEL; default="stable"]
    [--tags=[KEY=VALUE,...]]
    [--auxiliary-versions=[AUXILIARY_VERSIONS,...]
      | --auxiliary-versions-from-file=AUXILIARY_VERSIONS_FROM_FILE]
    [--consumer-subnetworks=[CONSUMER_SUBNETWORKS,...] | --network=NETWORK
      | --network-config-from-file=NETWORK_CONFIG_FROM_FILE]
    [--hive-metastore-configs=[KEY=VALUE,...]
      | --hive-metastore-configs-from-file=PATH_TO_FILE]
    [--instance-size=INSTANCE_SIZE | --scaling-factor=SCALING_FACTOR
      | --tier=TIER | --max-scaling-factor=MAX_SCALING_FACTOR
      --min-scaling-factor=MIN_SCALING_FACTOR]
    [--kerberos-principal=KERBEROS_PRINCIPAL
      --keytab=KEYTAB --krb5-config=KRB5_CONFIG]
    [--maintenance-window-day=MAINTENANCE_WINDOW_DAY
      --maintenance-window-hour=MAINTENANCE_WINDOW_HOUR]
    [--scheduled-backup-configs-from-file=PATH_TO_FILE
      | --enable-scheduled-backup
      --scheduled-backup-cron=SCHEDULED_BACKUP_CRON
      --scheduled-backup-location=SCHEDULED_BACKUP_LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - Arguments and flags that specify the Dataproc Metastore
service you want to create. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataproc Metastore service.

     If not specified, will use default metastore/location.

     To set the location attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property metastore/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--autoscaling-enabled` |  |  | A boolean flag to determine whether Dataproc Metastore autoscaling should be enabled, false if unspecified. The default minimum and maximum scaling factors are 0.1 and 6.0, respectively. The minimum and maximum scaling factors can be specified using --min-scaling-factor and --max-scaling-factor. |
| `--data-catalog-sync` |  |  | A boolean flag to determine whether Dataproc Metastore metadata sync to Data Catalog should be enabled, false if unspecified. Mutually exclusive with flag --encryption-kms-key. |
| `--database-type` | one of: mysql MYSQL database type is a Dataproc Metastore service backed by MySQL CloudSQL | mysql | The type of database the Dataproc Metastore service will store data in. DATABASE_TYPE must be one of: mysql MYSQL database type is a Dataproc Metastore service backed by MySQL CloudSQL. spanner SPANNER database type is a Dataproc Metastore service backed by Cloud Spanner. |
| `--deletion-protection` |  |  | Flag that enables delete protection on Dataproc Metastore instance to prevent accidental deletions of the instance. Use --deletion-protection to enable. |
| `--endpoint-protocol` | one of: grpc The modernized GRPC protocol | thrift | _[projects/{project_id}/locations/{location}/keyRings/{key_ring_id}/cryptoKeys/{crypto_key_id}.]_ The protocol to use for the metastore service endpoint. If unspecified, defaults to THRIFT. ENDPOINT_PROTOCOL must be one of: grpc The modernized GRPC protocol. thrift The legacy Apache THRIFT protocol. |
| `--hive-metastore-version` | HIVE_METASTORE_VERSION |  | _[projects/{project_id}/locations/{location}/keyRings/{key_ring_id}/cryptoKeys/{crypto_key_id}.]_ The Hive metastore schema version. The supported versions of a location are listed via: gcloud metastore locations describe If unspecified, the default version chosen by the server will be used. |
| `--labels` | [KEY=VALUE,...] |  | _[projects/{project_id}/locations/{location}/keyRings/{key_ring_id}/cryptoKeys/{crypto_key_id}.]_ List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--port` | PORT | 9083 | _[projects/{project_id}/locations/{location}/keyRings/{key_ring_id}/cryptoKeys/{crypto_key_id}.]_ The TCP port on which the Metastore service will listen. If unspecified, the default port 9083 will be used. |
| `--release-channel` | one of: canary The CANARY release channel contains the newest features, which may be unstable and subject to unresolved issues with no known workarounds | stable | _[projects/{project_id}/locations/{location}/keyRings/{key_ring_id}/cryptoKeys/{crypto_key_id}.]_ The release channel of the service. RELEASE_CHANNEL must be one of: canary The CANARY release channel contains the newest features, which may be unstable and subject to unresolved issues with no known workarounds. Services using the CANARY release channel are not subject to any SLAs. stable The STABLE release channel contains features that are considered stable and have been validated for production use. |
| `--tags` | [KEY=VALUE,...] |  | _[projects/{project_id}/locations/{location}/keyRings/{key_ring_id}/cryptoKeys/{crypto_key_id}.]_ List of tag KEY=VALUE pairs to add. |


**Examples:**
```bash
To create a Dataproc Metastore service with the name my-metastore-service
in location us-central using a non default port 9090, run:

    $ gcloud metastore services create my-metastore-service \
      --location=us-central1 --port=9090

To create a Dataproc Metastore service with the name my-metastore-service
in location us-central using a non default network foo, run:

    $ gcloud metastore services create my-metastore-service \
      --location=us-central1 --network=foo
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/services/create)

---
### `gcloud metastore services delete`

Delete one or more Dataproc Metastore services

If run asynchronously with --async, exits after printing one or more
operation names that can be used to poll the status of the deletion(s) via:

    gcloud metastore operations describe

**Synopsis:**
```
gcloud metastore services delete
    (SERVICES [SERVICES ...] : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - The services to delete. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument services on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICES [SERVICES ...]
     IDs of the services or fully qualified identifiers for the services.

     To set the service attribute:
     + provide the argument services on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location to which the services belongs.

     To set the location attribute:
     + provide the argument services on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property metastore/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a Dataproc Metastore service with the name my-metastore-service
in location us-central1, run:

    $ gcloud metastore services delete my-metastore-service \
        --location=us-central1

To delete multiple Dataproc Metastore services with the name service-1 and
service-2 in the same location us-central1, run:

    $ gcloud metastore services delete service-1 service-2 \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/services/delete)

---
### `gcloud metastore services describe`

Describe a Dataproc Metastore service

Describe a Dataproc Metastore service.

Displays all details of a Dataproc Metastore service given a valid service
ID.

**Synopsis:**
```
gcloud metastore services describe (SERVICE : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - Arguments and flags that specify the Metastore service
you want to describe. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataproc Metastore service.

     If not specified, will use default metastore/location.

     To set the location attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property metastore/location.
```

**Examples:**
```bash
To describe a Dataproc Metastore service with the ID my-metastore-service
in us-central1, run:

    $ gcloud metastore services describe my-metastore-service \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/services/describe)

---
### `gcloud metastore services get-iam-policy`

Get the IAM policy for the service

gcloud metastore services get-iam-policy displays the IAM policy associated
with the service. If formatted as JSON, the output can be edited and used
as a policy file for set-iam-policy. The output includes an "etag" field
identifying the version emitted and allowing detection of concurrent policy
updates. The "etag" field should be removed to be used as set-iam-policy
input; see gcloud metastore services set-iam-policy for additional details.

**Synopsis:**
```
gcloud metastore services get-iam-policy (SERVICE : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - Service for which to display the IAM policy. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataproc Metastore service.

     If not specified, will use default metastore/location.

     To set the location attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property metastore/location.
```

**Examples:**
```bash
To print the IAM policy for a given service, run:

    $ gcloud metastore services get-iam-policy my-service
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/services/get-iam-policy)

---
### `gcloud metastore services list`

List Dataproc Metastore services

Lists all Services under the specified project and location.

**Synopsis:**
```
gcloud metastore services list [--location=LOCATION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property metastore/location. |


**Examples:**
```bash
To list all Dataproc Metastore services in location us-central1, run:

    $ gcloud metastore services list --location=us-central1

To list all Dataproc Metastore services in all locations, run:

    $ gcloud metastore services list --location=-
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/services/list)

---
### `gcloud metastore services move-table-to-database`

Move table to another database

Move table to another database from a Dataproc Metastore service's
underlying metadata store.

If run asynchronously with --async, exits after printing one operation name
that can be used to poll the status of the creation via:

    gcloud metastore operations describe

**Synopsis:**
```
gcloud metastore services move-table-to-database
    (SERVICE : --location=LOCATION)
    --destination_db_name=DESTINATION_DB_NAME
    --source_db_name=SOURCE_DB_NAME --table_name=TABLE_NAME [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - Arguments and flags that specify the table and the
destination database you want to move to. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataproc Metastore service.

     If not specified, will use default metastore/location.

     To set the location attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property metastore/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION_DB_NAME |  | The name of the database where the table should be moved. |
| `--source` | SOURCE_DB_NAME |  | The name of the database where the table resides. |
| `--table` | TABLE_NAME |  | The name of the table to be moved. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To move table to database with the table_name, source_db_name, and
destination_db_name in location us-central, run:

    $ gcloud metastore services move-table-to-database \
      my-metastore-service --location=us-central1 \
      --table_name=table_name_to_move \
      --source_db_name=database_name_to_move \
      --destination_db_name=destination_database_name
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/services/move-table-to-database)

---
### `gcloud metastore services query-metadata`

Execute a SQL query against a Dataproc Metastore Service's metadata

Execute a SQL query against a Dataproc Metastore Service's metadata.

**Synopsis:**
```
gcloud metastore services query-metadata (SERVICE : --location=LOCATION)
    --query=QUERY [--format=FORMAT] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - The service to query metadata. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location to which the service belongs.

     To set the location attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property metastore/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--query` | QUERY |  | Use Google Standard SQL query for Cloud Spanner and MySQL query syntax for Cloud SQL. Cloud Spanner SQL is described at https://cloud.google.com/spanner/docs/query-syntax)" |


**Examples:**
```bash
To query metadata against a Dataproc Metastore service with the name
my-metastore-service in location us-central1, and the sql query "show
tables;", run:

    $ gcloud metastore services query-metadata my-metastore-service \
        --location=us-central1 --query="show tables;"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/services/query-metadata)

---
### `gcloud metastore services remove-iam-policy-binding`

Remove an IAM policy binding from a service

Remove an IAM policy binding from a service.

**Synopsis:**
```
gcloud metastore services remove-iam-policy-binding
    (SERVICE : --location=LOCATION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - Service for which to remove the IAM policy from. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataproc Metastore service.

     If not specified, will use default metastore/location.

     To set the location attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property metastore/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Examples:**
```bash
To remove an IAM policy binding for the role of 'roles/metastore.admin' for
the user 'test-user@gmail.com', run:

    $ gcloud metastore services remove-iam-policy-binding my-service \
        --member='user:test-user@gmail.com' \
        --role='roles/metastore.admin'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/services/remove-iam-policy-binding)

---
### `gcloud metastore services restore`

Restore a Dataproc Metastore service

Restore a Dataproc Metastore service from the given backup or
backup-location

If run asynchronously with --async, exits after printing an operation name
that can be used to poll the status of the creation via:

    gcloud metastore operations describe

**Synopsis:**
```
gcloud metastore services restore (SERVICE : --location=LOCATION)
    (--backup=BACKUP | --backup-location=BACKUP_LOCATION) [--async]
    [--restore-type=RESTORE_TYPE; default="metadata-only"]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - Arguments and flags that specify the Dataproc Metastore
service you want to restore. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataproc Metastore service.

     If not specified, will use default metastore/location.

     To set the location attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property metastore/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--backup` | BACKUP |  | _[Exactly one of these must be specified:]_ The backup resource to restore from. This can be the backup's ID, fully-qualified URL, or relative name in the form projects/{project_id}/locations/{location_id}/services/{service_id}/backups/{backup_id}. |
| `--backup-location` | BACKUP_LOCATION |  | _[Exactly one of these must be specified:]_ The location of the backup artifacts to restore from. This should be a Cloud Storage URI, contains backup avro files under "avro/", backup_metastore.json and service.json, in the form gs://<path_to_backup>. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--restore-type` | one of: full The service's metadata and configuration are restored | metadata-only | The type of restore to perform. RESTORE_TYPE must be one of: full The service's metadata and configuration are restored. metadata-only Only the service's metadata is restored. |


**Examples:**
```bash
To restore a Dataproc Metastore service with the name my-service from the
backup my-backup with a FULL restore type, run:

    $ gcloud metastore services restore my-service --backup=my-backup \
      --restore-type=full

To restore a Dataproc Metastore service with the name my-service from the
backup-location gs://gcs_bucket with a FULL restore type, run:

    $ gcloud metastore services restore my-service \
      --backup-location=gs://gcs_bucket --restore-type=full
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/services/restore)

---
### `gcloud metastore services set-iam-policy`

Set the IAM policy for the service

Sets the IAM policy for the given service as defined in a JSON or YAML
file.

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud metastore services set-iam-policy (SERVICE : --location=LOCATION)
    POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - Service for which to display the IAM policy. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataproc Metastore service.

     If not specified, will use default metastore/location.

     To set the location attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property metastore/location.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command will read an IAM policy defined in a JSON file
'policy.json' and set it for the service 'my-service':

    $ gcloud metastore services set-iam-policy my-service policy.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/services/set-iam-policy)

---
### `gcloud metastore services update`

Update a Dataproc Metastore service

Update the metadata and/or configuration parameters of a Dataproc Metastore
service.

If run asynchronously with --async, exits after printing one operation name
that can be used to poll the status of the update via:

    gcloud metastore operations describe

**Synopsis:**
```
gcloud metastore services update (SERVICE : --location=LOCATION) [--async]
    [--autoscaling-enabled] [--data-catalog-sync] [--deletion-protection]
    [--endpoint-protocol=ENDPOINT_PROTOCOL] [--port=PORT]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]]
    [--instance-size=INSTANCE_SIZE | --scaling-factor=SCALING_FACTOR
      | --tier=TIER | --max-scaling-factor=MAX_SCALING_FACTOR
      --min-scaling-factor=MIN_SCALING_FACTOR]
    [--kerberos-principal=KERBEROS_PRINCIPAL
      --keytab=KEYTAB --krb5-config=KRB5_CONFIG]
    [--maintenance-window-day=MAINTENANCE_WINDOW_DAY
      --maintenance-window-hour=MAINTENANCE_WINDOW_HOUR]
    [--scheduled-backup-configs-from-file=PATH_TO_FILE
      | --enable-scheduled-backup
      --scheduled-backup-cron=SCHEDULED_BACKUP_CRON
      --scheduled-backup-location=SCHEDULED_BACKUP_LOCATION]
    [--update-auxiliary-versions-from-file=UPDATE_AUXILIARY_VERSIONS_FROM_FILE | --add-auxiliary-versions=[ADD_AUXILIARY_VERSIONS,
      ...] --clear-auxiliary-versions]
    [--update-hive-metastore-configs-from-file=PATH_TO_FILE
      | --update-hive-metastore-configs=[KEY=VALUE,...]
      --clear-hive-metastore-configs
      | --remove-hive-metastore-configs=[REMOVE_HIVE_METASTORE_CONFIGS,
      ...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - Arguments and flags that specify the Dataproc Metastore
service you want to update. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataproc Metastore service.

     If not specified, will use default metastore/location.

     To set the location attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property metastore/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--autoscaling-enabled` |  |  | A boolean flag to determine whether Dataproc Metastore autoscaling should be enabled, false if unspecified. The default minimum and maximum scaling factors are 0.1 and 6.0, respectively. The minimum and maximum scaling factors can be specified using --min-scaling-factor and --max-scaling-factor. |
| `--data-catalog-sync` |  |  | Boolean flag to determine whether or not Dataproc Metastore metadata sync to Data Catalog is enabled, false if unspecified. Mutually exclusive with flag --encryption-kms-key. Cannot be updated if the service uses customer-managed encryption keys. |
| `--deletion-protection` |  |  | Flag that enables delete protection on Dataproc Metastore instance to prevent accidental deletions of the instance. Use --deletion-protection to enable and --no-deletion-protection to disable. |
| `--endpoint-protocol` | one of: grpc The modernized GRPC protocol |  | The protocol to use for the metastore service endpoint. ENDPOINT_PROTOCOL must be one of: grpc The modernized GRPC protocol. thrift The legacy Apache THRIFT protocol. |
| `--port` | PORT |  | The TCP port on which the Metastore service will listen. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update a Dataproc Metastore service with the name my-metastore-service
to have the port number 8080, and add the two labels, env and foo, run:

    $ gcloud metastore services update my-metastore-service \
      --port=8080 --update-labels=env=test,foo=bar
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/services/update)

---

## `gcloud metastore services backups` — manage backups under Dataproc Metastore services
### `gcloud metastore services backups add-iam-policy-binding`

Add an IAM policy binding to a backup

Add an IAM policy binding to a backup.

**Synopsis:**
```
gcloud metastore services backups add-iam-policy-binding
    (BACKUP : --location=LOCATION --service=SERVICE) --member=PRINCIPAL
    --role=ROLE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - Backup for which to add the IAM policy to. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP
     ID of the backup or fully qualified identifier for the backup.

     To set the backup attribute:
     + provide the argument backup on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataproc Metastore service.

     If not specified, will use default metastore/location.

     To set the location attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property metastore/location.

  --service=SERVICE
     The identifier of the Dataproc Metastore service

     To set the service attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --service on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Examples:**
```bash
To add an IAM policy binding for the role of 'roles/metastore.admin' for
the user 'test-user@gmail.com', run:

    $ gcloud metastore services backups add-iam-policy-binding \
        my-backup --member='user:test-user@gmail.com' \
        --role='roles/metastore.admin'

See https://cloud.google.com/dataproc-metastore/docs/iam-and-access-control
for details of policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/services/backups/add-iam-policy-binding)

---
### `gcloud metastore services backups create`

Backup a service

Backup metadata and the resource configuration of a service.

**Synopsis:**
```
gcloud metastore services backups create
    (BACKUP : --location=LOCATION --service=SERVICE) [--async]
    [--description=DESCRIPTION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - Arguments and flags that specify the backup you want to
create. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP
     ID of the backup or fully qualified identifier for the backup.

     To set the backup attribute:
     + provide the argument backup on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataproc Metastore service.

     If not specified, will use default metastore/location.

     To set the location attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property metastore/location.

  --service=SERVICE
     The identifier of the Dataproc Metastore service

     To set the service attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --service on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | The description of this backup. |


**Examples:**
```bash
To make a backup named my-backup and description test description of the
service my-service, run:

    $ gcloud metastore services backups create my-backup \
      --service=my-service --description='test description'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/services/backups/create)

---
### `gcloud metastore services backups delete`

Delete a service backup

Delete a backup.

If run asynchronously with --async, exits after printing an operation name
that can be used to poll the status of the deletion via:

    gcloud metastore operations describe

**Synopsis:**
```
gcloud metastore services backups delete
    (BACKUP : --location=LOCATION --service=SERVICE) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - Backup to delete. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP
     ID of the backup or fully qualified identifier for the backup.

     To set the backup attribute:
     + provide the argument backup on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataproc Metastore service.

     If not specified, will use default metastore/location.

     To set the location attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property metastore/location.

  --service=SERVICE
     The identifier of the Dataproc Metastore service

     To set the service attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --service on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a backup named my-backup from the service my-service, run:

    $ gcloud metastore services backups delete my-backup \
      --service=my-service
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/services/backups/delete)

---
### `gcloud metastore services backups describe`

Describe a backup

Describe a backup.

Displays all details of a backup given a valid backup ID.

**Synopsis:**
```
gcloud metastore services backups describe
    (BACKUP : --location=LOCATION --service=SERVICE) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - Arguments and flags that specify the backup you want to
describe. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP
     ID of the backup or fully qualified identifier for the backup.

     To set the backup attribute:
     + provide the argument backup on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataproc Metastore service.

     If not specified, will use default metastore/location.

     To set the location attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property metastore/location.

  --service=SERVICE
     The identifier of the Dataproc Metastore service

     To set the service attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --service on the command line.
```

**Examples:**
```bash
To describe a backup with the ID my-backup under service my-service, run:

    $ gcloud metastore services backups describe my-backup \
        --service=my-service
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/services/backups/describe)

---
### `gcloud metastore services backups get-iam-policy`

Get the IAM policy for the backup

gcloud metastore services backups get-iam-policy displays the IAM policy
associated with the backup. If formatted as JSON, the output can be edited
and used as a policy file for set-iam-policy. The output includes an "etag"
field identifying the version emitted and allowing detection of concurrent
policy updates. The "etag" field should be removed to be used as
set-iam-policy input; see gcloud metastore services backups set-iam-policy
for additional details.

**Synopsis:**
```
gcloud metastore services backups get-iam-policy
    (BACKUP : --location=LOCATION --service=SERVICE) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - Backup for which to display the IAM policy. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP
     ID of the backup or fully qualified identifier for the backup.

     To set the backup attribute:
     + provide the argument backup on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataproc Metastore service.

     If not specified, will use default metastore/location.

     To set the location attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property metastore/location.

  --service=SERVICE
     The identifier of the Dataproc Metastore service

     To set the service attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --service on the command line.
```

**Examples:**
```bash
To print the IAM policy for a given backup, run:

    $ gcloud metastore services backups get-iam-policy my-backup
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/services/backups/get-iam-policy)

---
### `gcloud metastore services backups list`

List backups under a Dataproc Metastore service

Lists all backups under the specified Dataproc Metastore service.

**Synopsis:**
```
gcloud metastore services backups list
    (--service=SERVICE : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--service` | SERVICE |  | _[This must be specified.]_ ID of the service or fully qualified identifier for the service. To set the service attribute: + provide the argument --service on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The location of the Dataproc Metastore service. If not specified, will use default metastore/location. To set the location attribute: + provide the argument --service on the command line with a fully specified name; + provide the argument --location on the command line; + set the property metastore/location. |


**Examples:**
```bash
To list all backups under service my-service, run:

    $ gcloud metastore services backups list --service=my-service

To list all backups under all services and all locations, run:

    $ gcloud metastore services backups list --service=- --location=-
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/services/backups/list)

---
### `gcloud metastore services backups remove-iam-policy-binding`

Remove an IAM policy binding from a backup

Remove an IAM policy binding from a backup.

**Synopsis:**
```
gcloud metastore services backups remove-iam-policy-binding
    (BACKUP : --location=LOCATION --service=SERVICE) --member=PRINCIPAL
    --role=ROLE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - Backup for which to remove the IAM policy from. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP
     ID of the backup or fully qualified identifier for the backup.

     To set the backup attribute:
     + provide the argument backup on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataproc Metastore service.

     If not specified, will use default metastore/location.

     To set the location attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property metastore/location.

  --service=SERVICE
     The identifier of the Dataproc Metastore service

     To set the service attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --service on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Examples:**
```bash
To remove an IAM policy binding for the role of 'roles/metastore.admin' for
the user 'test-user@gmail.com', run:

    $ gcloud metastore services backups remove-iam-policy-binding \
        my-backup --member='user:test-user@gmail.com' \
        --role='roles/metastore.admin'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/services/backups/remove-iam-policy-binding)

---
### `gcloud metastore services backups set-iam-policy`

Set the IAM policy for a backup

Sets the IAM policy for the given backup as defined in a JSON or YAML file.

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud metastore services backups set-iam-policy
    (BACKUP : --location=LOCATION --service=SERVICE) POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - Backup for which to display the IAM policy. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP
     ID of the backup or fully qualified identifier for the backup.

     To set the backup attribute:
     + provide the argument backup on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataproc Metastore service.

     If not specified, will use default metastore/location.

     To set the location attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property metastore/location.

  --service=SERVICE
     The identifier of the Dataproc Metastore service

     To set the service attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --service on the command line.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command will read an IAM policy defined in a JSON file
'policy.json' and set it for the backup 'my-backup':

    $ gcloud metastore services backups set-iam-policy my-backup \
        policy.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/services/backups/set-iam-policy)

---

## `gcloud metastore services export` — export metadata from a Dataproc Metastore service
### `gcloud metastore services export gcs`

Export metadata from a Dataproc Metastore service to Google Cloud Storage

Export metadata from a Dataproc Metastore service to Google Cloud Storage.

If run asynchronously with --async, exits after printing the operation name
that can be used to poll the status of the export via:

    gcloud metastore operations describe

**Synopsis:**
```
gcloud metastore services export gcs (SERVICE : --location=LOCATION)
    --destination-folder=DESTINATION_FOLDER [--async]
    [--dump-type=DUMP_TYPE; default="mysql"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - Arguments and flags that specify the Dataproc Metastore
service you want to export. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataproc Metastore service.

     If not specified, will use default metastore/location.

     To set the location attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property metastore/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination-folder` | DESTINATION_FOLDER |  | A Cloud Storage URI of a folder that metadata is exported to, in the format gs://<bucket_name>/<path_inside_bukcet>. A sub-folder containing exported files will be created below it. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--dump-type` | one of: avro Database dump contains AVRO files | mysql | The type of the database dump. If unspecified, defaults to mysql. DUMP_TYPE must be one of: avro Database dump contains AVRO files. mysql Database dump is a MYSQL dump file. |


**Examples:**
```bash
To export metadata from a Dataproc Metastore service with the name
my-metastore-service in location us-central1 to the destination folder
gs://my-bucket/destination-folder, run:

    $ gcloud metastore services export gcs my-metastore-service \
        --location=us-central1 \
        --destination-folder=gs://my-bucket/destination-folder
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/services/export/gcs)

---

## `gcloud metastore services import` — import metadata into a Dataproc Metastore service
### `gcloud metastore services import gcs`

Import metadata into a Dataproc Metastore service from Google Cloud Storage

Import metadata into a Dataproc Metastore service from Google Cloud
Storage.

If run asynchronously with --async, exits after printing the operation name
that can be used to poll the status of the export via:

    gcloud metastore operations describe

**Synopsis:**
```
gcloud metastore services import gcs (SERVICE : --location=LOCATION)
    --database-dump=DATABASE_DUMP --import-id=IMPORT_ID [--async]
    [--description=DESCRIPTION] [--dump-type=DUMP_TYPE; default="mysql"]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - Arguments and flags that specify the Dataproc Metastore
service you want to import. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataproc Metastore service.

     If not specified, will use default metastore/location.

     To set the location attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property metastore/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--database-dump` | DATABASE_DUMP |  | A Cloud Storage object URI that specifies a database dump from which to import metadata. It must begin with gs://. |
| `--import-id` | IMPORT_ID |  | The ID of this metadata import. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | The description of this metadata import. |
| `--dump-type` | one of: avro Database dump contains AVRO files | mysql | The type of the database dump;. If unspecified, defaults to mysql. DUMP_TYPE must be one of: avro Database dump contains AVRO files. mysql Database dump is a MYSQL dump file. |


**Examples:**
```bash
To import metadata with the name my-import and description testing
description into service my-service from a database dump with uri
gs://database-dump and database type mysql, run:

    $ gcloud metastore services import gcs my-service \
      --import-id=my-import --description='testing description' \
      --dump-type=mysql --database-dump=gs://database-dump
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/services/import/gcs)

---
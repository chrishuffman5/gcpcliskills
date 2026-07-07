# gcloud datastream connection-profiles

manage Datastream connection profiles

### `gcloud datastream connection-profiles create`

Create a Datastream connection profile

**Synopsis:**
```
gcloud datastream connection-profiles create
    (CONNECTION_PROFILE : --location=LOCATION) --display-name=DISPLAY_NAME
    --type=TYPE [--force] [--labels=[KEY=VALUE,...]]
    [[--bucket=BUCKET : --root-path=ROOT_PATH]
      | [--database-service=DATABASE_SERVICE
      --oracle-hostname=ORACLE_HOSTNAME --oracle-port=ORACLE_PORT
      --oracle-username=ORACLE_USERNAME (--oracle-password=ORACLE_PASSWORD
      | --oracle-prompt-for-password
      | --oracle-secret-manager-stored-password=ORACLE_SECRET_MANAGER_STORED_PASSWORD) : --oracle-ca-certificate=ORACLE_CA_CERTIFICATE --oracle-server-certificate-distinguished-name=ORACLE_SERVER_CERTIFICATE_DISTINGUISHED_NAME] | [--mongodb-host-addresses=IPv4_ADDRESS_OR_HOSTNAME:PORT,
      [...] --mongodb-username=MONGODB_USERNAME
      (--mongodb-password=MONGODB_PASSWORD | --mongodb-prompt-for-password
      | --mongodb-secret-manager-stored-password=MONGODB_SECRET_MANAGER_STORED_PASSWORD) (--mongodb-srv-connection-format | --mongodb-standard-connection-format) : --mongodb-additional-options=[MONGODB_PROFILE_ADDITIONAL_OPTIONS,
      ...] --mongodb-direct-connection
      --mongodb-replica-set=MONGODB_REPLICA_SET
      --mongodb-ca-certificate=MONGODB_CA_CERTIFICATE --mongodb-tls]
      | [--mysql-hostname=MYSQL_HOSTNAME --mysql-port=MYSQL_PORT
      --mysql-username=MYSQL_USERNAME (--mysql-password=MYSQL_PASSWORD
      | --mysql-prompt-for-password
      | --mysql-secret-manager-stored-password=MYSQL_SECRET_MANAGER_STORED_PASSWORD) : --ca-certificate=CA_CERTIFICATE --client-certificate=CLIENT_CERTIFICATE --client-key=CLIENT_KEY] | [--postgresql-database=POSTGRESQL_DATABASE --postgresql-hostname=POSTGRESQL_HOSTNAME --postgresql-port=POSTGRESQL_PORT --postgresql-username=POSTGRESQL_USERNAME (--postgresql-password=POSTGRESQL_PASSWORD | --postgresql-prompt-for-password | --postgresql-secret-manager-stored-password=POSTGRESQL_SECRET_MANAGER_STORED_PASSWORD) : [--postgresql-ca-certificate=POSTGRESQL_CA_CERTIFICATE : --postgresql-server-certificate-hostname=POSTGRESQL_SERVER_CERTIFICATE_HOSTNAME --postgresql-client-certificate=POSTGRESQL_CLIENT_CERTIFICATE --postgresql-client-key=POSTGRESQL_CLIENT_KEY]] | --salesforce-domain=SALESFORCE_DOMAIN (--salesforce-oauth2-client-id=SALESFORCE_OAUTH2_CLIENT_ID (--salesforce-oauth2-client-secret=SALESFORCE_OAUTH2_CLIENT_SECRET | --salesforce-prompt-for-oauth2-client-secret | --salesforce-secret-manager-stored-oauth2-client-secret=SALESFORCE_SECRET_MANAGER_STORED_OAUTH2_CLIENT_SECRET) | --salesforce-username=SALESFORCE_USERNAME (--salesforce-password=SALESFORCE_PASSWORD | --salesforce-prompt-for-password | --salesforce-secret-manager-stored-password=SALESFORCE_SECRET_MANAGER_STORED_PASSWORD) (--salesforce-prompt-for-security-token | --salesforce-secret-manager-stored-security-token=SALESFORCE_SECRET_MANAGER_STORED_SECURITY_TOKEN | --salesforce-security-token=SALESFORCE_SECURITY_TOKEN)) | --sqlserver-database=SQLSERVER_DATABASE --sqlserver-hostname=SQLSERVER_HOSTNAME --sqlserver-port=SQLSERVER_PORT --sqlserver-username=SQLSERVER_USERNAME (--sqlserver-password=SQLSERVER_PASSWORD | --sqlserver-prompt-for-password | --sqlserver-secret-manager-stored-password=SQLSERVER_SECRET_MANAGER_STORED_PASSWORD)]
    [--private-connection=PRIVATE_CONNECTION | --static-ip-connectivity
      | [--forward-ssh-hostname=FORWARD_SSH_HOSTNAME
      --forward-ssh-username=FORWARD_SSH_USERNAME
      (--forward-ssh-password=FORWARD_SSH_PASSWORD
      | --forward-ssh-private-key=FORWARD_SSH_PRIVATE_KEY)
      : --forward-ssh-port=FORWARD_SSH_PORT; default=22]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connection profile resource - The connection profile to create. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument connection_profile on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTION_PROFILE
     ID of the connection_profile or fully qualified identifier for the
     connection_profile.

     To set the connection_profile attribute:
     + provide the argument connection_profile on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the connection_profile.

     To set the location attribute:
     + provide the argument connection_profile on the command line with
       a fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | Friendly name for the connection profile. |
| `--type` | TYPE |  | Type can be MYSQL, ORACLE, POSTGRESQL, SQLSERVER, SALESFORCE, GOOGLE-CLOUD-STORAGE or BIGQUERY |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--force` |  |  | Create the connection profile without validating it. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To create a connection profile for Oracle:

    $ gcloud datastream connection-profiles create CONNECTION_PROFILE \
      --location=us-central1 --type=oracle \
      --oracle-password=fakepassword --oracle-username=fakeuser \
      --display-name=my-profile --oracle-hostname=35.188.150.50 \
      --oracle-port=1521 --database-service=ORCL \
      --static-ip-connectivity

To create a connection profile for MySQL:

    $ gcloud datastream connection-profiles create CONNECTION_PROFILE \
      --location=us-central1 --type=mysql \
      --mysql-password=fakepassword --mysql-username=fakeuser \
      --display-name=my-profile --mysql-hostname=35.188.150.50 \
      --mysql-port=3306 --static-ip-connectivity

To create a connection profile for PostgreSQL:

    $ gcloud datastream connection-profiles create CONNECTION_PROFILE \
      --location=us-central1 --type=postgresql \
      --postgresql-password=fakepassword \
      --postgresql-username=fakeuser --display-name=my-profile \
      --postgresql-hostname=35.188.150.50 --postgresql-port=5432 \
      --postgresql-database=db --static-ip-connectivity

To create a connection profile for SQL Server:

    $ gcloud datastream connection-profiles create CONNECTION_PROFILE \
      --location=us-central1 --type=sqlserver \
      --sqlserver-password=fakepassword \
      --sqlserver-username=fakeuser --display-name=my-profile \
      --sqlserver-hostname=35.188.150.50 --sqlserver-port=1433 \
      --sqlserver-database=db --static-ip-connectivity

To create a connection profile for Salesforce using Username, Password and
Security Token:

    $ gcloud datastream connection-profiles create CONNECTION_PROFILE \
      --location=us-central1 --type=salesforce \
      --salesforce-password=fakepassword \
      --salesforce-username=fakeuser \
      --salesforce-security-token=fakesecuritytoken \
      --display-name=my-profile --salesforce-hostname=35.188.150.50 \
      --salesforce-port=1433 --salesforce-database=db \
      --static-ip-connectivity

To create a connection profile for Salesforce using OAuth:

    $ gcloud datastream connection-profiles create CONNECTION_PROFILE \
      --location=us-central1 --type=salesforce \
      --salesforce-client-secret=fakesecret \
      --salesforce-client-id=fake-client-id \
      --display-name=my-profile \
      --salesforce-domain=fakecompany.my.salesforce.com \
      --static-ip-connectivity

To create a connection profile for Google Cloud Storage:

    $ gcloud datastream connection-profiles create CONNECTION_PROFILE \
      --location=us-central1 --type=google-cloud-storage \
      --bucket=fake-bucket --root-path=/root/path \
      --display-name=my-profile

To create a connection profile for BigQuery:

    $ gcloud datastream connection-profiles create CONNECTION_PROFILE \
      --location=us-central1 --type=bigquery --display-name=my-profile

To create a connection profile for MongoDB:

    $ gcloud datastream connection-profiles create CONNECTION_PROFILE \
      --location=us-central1 --type=mongodb \
      --mongodb-password=fakepassword --mongodb-username=fakeuser \
      --display-name=my-profile \
      --mongodb-host-addresses=35.188.150.50:27017
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastream/connection-profiles/create)

---
### `gcloud datastream connection-profiles delete`

Delete a Datastream connection profile

Deletes a connection profile.

**Synopsis:**
```
gcloud datastream connection-profiles delete
    (CONNECTION_PROFILE : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connection profile resource - Connection profile resource - Connection
profile to delete. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument connection_profile on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTION_PROFILE
     ID of the connection_profile or fully qualified identifier for the
     connection_profile.

     To set the connection_profile attribute:
     + provide the argument connection_profile on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the resources.

     To set the location attribute:
     + provide the argument connection_profile on the command line with
       a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To delete a connection profile:

    $ gcloud datastream connection-profiles delete CONNECTION_PROFILE \
      --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastream/connection-profiles/delete)

---
### `gcloud datastream connection-profiles describe`

Show details about a Datastream connection profile

Show details about a connection profile.

**Synopsis:**
```
gcloud datastream connection-profiles describe
    (CONNECTION_PROFILE : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connection profile resource - The connection profile you want to get the
details of. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument connection_profile on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTION_PROFILE
     ID of the connection_profile or fully qualified identifier for the
     connection_profile.

     To set the connection_profile attribute:
     + provide the argument connection_profile on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the resources.

     To set the location attribute:
     + provide the argument connection_profile on the command line with
       a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To show details about a connection profile, run:

    $ gcloud datastream connection-profiles describe \
        my-connection-profile --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastream/connection-profiles/describe)

---
### `gcloud datastream connection-profiles discover`

Discover a Datastream connection profile

Discover data objects accessible from a Datastream connection profile

**Synopsis:**
```
gcloud datastream connection-profiles discover --location=LOCATION
    (--connection-profile-name=CONNECTION_PROFILE_NAME
      | --connection-profile-object-file=CONNECTION_PROFILE_OBJECT_FILE)
    [--full-hierarchy | --hierarchy-depth=HIERARCHY_DEPTH]
    [--mysql-rdbms-file=MYSQL_RDBMS_FILE
      | --oracle-rdbms-file=ORACLE_RDBMS_FILE
      | --postgresql-rdbms-file=POSTGRESQL_RDBMS_FILE
      | --sqlserver-rdbms-file=SQLSERVER_RDBMS_FILE]
    [--recursive | --recursive-depth=RECURSIVE_DEPTH]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |
| `--connection-profile-object-file` | CONNECTION_PROFILE_OBJECT_FILE |  | _[line.]_ Path to a YAML (or JSON) file containing the configuration for a connection profile object. If you pass - as the value of the flag the file content will be read from stdin. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--full-hierarchy` |  |  | _[At most one of these can be specified:]_ Whether to retrieve the full hierarchy of data objects (TRUE) or only the current level (FALSE). |
| `--hierarchy-depth` | HIERARCHY_DEPTH |  | _[At most one of these can be specified:]_ The number of hierarchy levels below the current level to be retrieved. |
| `--mysql-rdbms-file` | MYSQL_RDBMS_FILE |  | _[At most one of these can be specified:]_ Path to a YAML (or JSON) file containing the MySQL RDBMS to enrich with child data objects and metadata. If you pass - as the value of the flag the file content will be read from stdin. |
| `--oracle-rdbms-file` | ORACLE_RDBMS_FILE |  | _[At most one of these can be specified:]_ Path to a YAML (or JSON) file containing the Oracle RDBMS to enrich with child data objects and metadata. If you pass - as the value of the flag the file content will be read from stdin. |
| `--postgresql-rdbms-file` | POSTGRESQL_RDBMS_FILE |  | _[At most one of these can be specified:]_ Path to a YAML (or JSON) file containing the PostgreSQL RDBMS to enrich with child data objects and metadata. If you pass - as the value of the flag the file content will be read from stdin. |
| `--sqlserver-rdbms-file` | SQLSERVER_RDBMS_FILE |  | _[At most one of these can be specified:]_ Path to a YAML (or JSON) file containing the SQL Server RDBMS to enrich with child data objects and metadata. If you pass - as the value of the flag the file content will be read from stdin. |
| `--recursive` |  |  | _[At most one of these can be specified:]_ (DEPRECATED) Whether to retrieve the full hierarchy of data objects (TRUE) or only the current level (FALSE). The --recursive option is deprecated; use --full-hierarchy instead. |
| `--recursive-depth` | RECURSIVE_DEPTH |  | _[At most one of these can be specified:]_ (DEPRECATED) The number of hierarchy levels below the current level to be retrieved. The --recursive-depth option is deprecated; use --hierarchy-depth instead. |


**Examples:**
```bash
To discover an existing connection profile:

    $ gcloud datastream connection-profiles discover \
      CONNECTION_PROFILE --location=us-central1 \
      --connection-profile-name=some-cp --recursive=true

To discover a non-existing connection profile:

    $ gcloud datastream connection-profiles discover \
      CONNECTION_PROFILE --location=us-central1 \
      --connection-profile-object-file=path/to/yaml/or/json/file
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastream/connection-profiles/discover)

---
### `gcloud datastream connection-profiles list`

List Datastream connection profiles

List connection profiles.

**Synopsis:**
```
gcloud datastream connection-profiles list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all connection profiles in a project and location 'us-central1',
run:

    $ gcloud datastream connection-profiles list --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastream/connection-profiles/list)

---
### `gcloud datastream connection-profiles update`

Update a Datastream connection profile

Updates a Datastream connection profile

**Synopsis:**
```
gcloud datastream connection-profiles update
    (CONNECTION_PROFILE : --location=LOCATION) --type=TYPE
    [--display-name=DISPLAY_NAME] [--force]
    [--update-labels=[KEY=VALUE,...]]
    [--bucket=BUCKET --root-path=ROOT_PATH
      | --database-service=DATABASE_SERVICE
      --oracle-hostname=ORACLE_HOSTNAME --oracle-port=ORACLE_PORT
      --oracle-username=ORACLE_USERNAME
      --oracle-ca-certificate=ORACLE_CA_CERTIFICATE
      --oracle-server-certificate-distinguished-name=ORACLE_SERVER_CERTIFICATE_DISTINGUISHED_NAME --oracle-password=ORACLE_PASSWORD | --oracle-prompt-for-password | --oracle-secret-manager-stored-password=ORACLE_SECRET_MANAGER_STORED_PASSWORD | --mongodb-additional-options=[MONGODB_PROFILE_ADDITIONAL_OPTIONS,
      ...] --mongodb-direct-connection
      --mongodb-host-addresses=IPv4_ADDRESS_OR_HOSTNAME:PORT,[...]
      --mongodb-replica-set=MONGODB_REPLICA_SET
      --mongodb-username=MONGODB_USERNAME
      --mongodb-ca-certificate=MONGODB_CA_CERTIFICATE
      --mongodb-tls --mongodb-password=MONGODB_PASSWORD
      | --mongodb-prompt-for-password
      | --mongodb-secret-manager-stored-password=MONGODB_SECRET_MANAGER_STORED_PASSWORD --mongodb-srv-connection-format | --mongodb-standard-connection-format | --mysql-hostname=MYSQL_HOSTNAME --mysql-port=MYSQL_PORT --mysql-username=MYSQL_USERNAME --ca-certificate=CA_CERTIFICATE --client-certificate=CLIENT_CERTIFICATE --client-key=CLIENT_KEY --mysql-password=MYSQL_PASSWORD | --mysql-prompt-for-password | --mysql-secret-manager-stored-password=MYSQL_SECRET_MANAGER_STORED_PASSWORD | --postgresql-database=POSTGRESQL_DATABASE --postgresql-hostname=POSTGRESQL_HOSTNAME --postgresql-port=POSTGRESQL_PORT --postgresql-username=POSTGRESQL_USERNAME --postgresql-ca-certificate=POSTGRESQL_CA_CERTIFICATE --postgresql-server-certificate-hostname=POSTGRESQL_SERVER_CERTIFICATE_HOSTNAME --postgresql-client-certificate=POSTGRESQL_CLIENT_CERTIFICATE --postgresql-client-key=POSTGRESQL_CLIENT_KEY --postgresql-password=POSTGRESQL_PASSWORD | --postgresql-prompt-for-password | --postgresql-secret-manager-stored-password=POSTGRESQL_SECRET_MANAGER_STORED_PASSWORD | --salesforce-domain=SALESFORCE_DOMAIN --salesforce-oauth2-client-id=SALESFORCE_OAUTH2_CLIENT_ID --salesforce-oauth2-client-secret=SALESFORCE_OAUTH2_CLIENT_SECRET | --salesforce-prompt-for-oauth2-client-secret | --salesforce-secret-manager-stored-oauth2-client-secret=SALESFORCE_SECRET_MANAGER_STORED_OAUTH2_CLIENT_SECRET | --salesforce-username=SALESFORCE_USERNAME --salesforce-password=SALESFORCE_PASSWORD | --salesforce-prompt-for-password | --salesforce-secret-manager-stored-password=SALESFORCE_SECRET_MANAGER_STORED_PASSWORD --salesforce-prompt-for-security-token | --salesforce-secret-manager-stored-security-token=SALESFORCE_SECRET_MANAGER_STORED_SECURITY_TOKEN | --salesforce-security-token=SALESFORCE_SECURITY_TOKEN | --sqlserver-database=SQLSERVER_DATABASE --sqlserver-hostname=SQLSERVER_HOSTNAME --sqlserver-port=SQLSERVER_PORT --sqlserver-username=SQLSERVER_USERNAME --sqlserver-password=SQLSERVER_PASSWORD | --sqlserver-prompt-for-password | --sqlserver-secret-manager-stored-password=SQLSERVER_SECRET_MANAGER_STORED_PASSWORD]
    [--clear-labels | --remove-labels=[KEY,...]]
    [--private-connection=PRIVATE_CONNECTION | --static-ip-connectivity
      | --forward-ssh-hostname=FORWARD_SSH_HOSTNAME
      --forward-ssh-port=FORWARD_SSH_PORT; default=22
      --forward-ssh-username=FORWARD_SSH_USERNAME
      --forward-ssh-password=FORWARD_SSH_PASSWORD
      | --forward-ssh-private-key=FORWARD_SSH_PRIVATE_KEY]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connection profile resource - The connection profile to update. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument connection_profile on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTION_PROFILE
     ID of the connection_profile or fully qualified identifier for the
     connection_profile.

     To set the connection_profile attribute:
     + provide the argument connection_profile on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the connection_profile.

     To set the location attribute:
     + provide the argument connection_profile on the command line with
       a fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--type` | TYPE |  | Type can be MYSQL, ORACLE, POSTGRESQL, SQLSERVER, SALESFORCE, GOOGLE-CLOUD-STORAGE or BIGQUERY |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | Friendly name for the connection profile. |
| `--force` |  |  | Update the connection profile without validating it. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update a connection profile for Oracle:

    $ gcloud datastream connection-profiles update CONNECTION_PROFILE \
      --location=us-central1 --type=oracle \
      --oracle-password=fakepassword --oracle-username=fakeuser \
      --display-name=my-profile --oracle-hostname=35.188.150.50 \
      --oracle-port=1521 --database-service=ORCL \
      --static-ip-connectivity

To update a connection profile for MySQL:

    $ gcloud datastream connection-profiles update CONNECTION_PROFILE \
      --location=us-central1 --type=mysql \
      --mysql-password=fakepassword --mysql-username=fakeuser \
      --display-name=my-profile --mysql-hostname=35.188.150.50 \
      --mysql-port=3306 --static-ip-connectivity

To update a connection profile for PostgreSQL:

    $ gcloud datastream connection-profiles update CONNECTION_PROFILE \
      --location=us-central1 --type=postgresql \
      --postgresql-password=fakepassword \
      --postgresql-username=fakeuser --display-name=my-profile \
      --postgresql-hostname=35.188.150.50 --postgresql-port=5432 \
      --postgresql-database=db --static-ip-connectivity

To update a connection profile for SQL Server:

    $ gcloud datastream connection-profiles update CONNECTION_PROFILE \
      --location=us-central1 --type=sqlserver \
      --sqlserver-password=fakepassword \
      --sqlserver-username=fakeuser --display-name=my-profile \
      --sqlserver-hostname=35.188.150.50 --sqlserver-port=1433 \
      --sqlserver-database=db --static-ip-connectivity

To update a connection profile for Salesforce:

    $ gcloud datastream connection-profiles update CONNECTION_PROFILE \
      --location=us-central1 --type=salesforce \
      --salesforce-password=fakepassword \
      --salesforce-username=fakeuser --display-name=my-profile \
      --salesforce-domain=fakecompany.my.salesforce.com \
      --static-ip-connectivity

To update a connection profile for Google Cloud Storage:

    $ gcloud datastream connection-profiles update CONNECTION_PROFILE \
      --location=us-central1 --type=google-cloud-storage \
      --bucket=fake-bucket --root-path=/root/path \
      --display-name=my-profile

To update a connection profile for BigQuery:

    $ gcloud datastream connection-profiles update CONNECTION_PROFILE \
      --location=us-central1 --type=bigquery --display-name=my-profile

To update a connection profile for MongoDB:

    $ gcloud datastream connection-profiles update CONNECTION_PROFILE \
      --location=us-central1 --type=mongodb \
      --mongodb-password=fakepassword --mongodb-username=fakeuser \
      --display-name=my-profile \
      --mongodb-host-addresses=35.188.150.50:27017 \
      --static-ip-connectivity
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastream/connection-profiles/update)

---
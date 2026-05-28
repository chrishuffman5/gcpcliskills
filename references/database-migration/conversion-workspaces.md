# gcloud database-migration conversion-workspaces

manage Database Migration Service conversion workspaces

### `gcloud database-migration conversion-workspaces apply`

Apply a Database Migration Service conversion workspace

Apply Database Migration Service conversion workspace onto the destination
database.

**Synopsis:**
```
gcloud database-migration conversion-workspaces apply
    (CONVERSION_WORKSPACE : --region=REGION)
    --destination-connection-profile=DESTINATION_CONNECTION_PROFILE
    [--no-async] [--filter=FILTER] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Conversion workspace resource - The conversion workspace to apply. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument conversion_workspace on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONVERSION_WORKSPACE
     ID of the conversion_workspace or fully qualified identifier for the
     conversion_workspace.

     To set the conversion_workspace attribute:
     + provide the argument conversion_workspace on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the conversion_workspace.

     To set the region attribute:
     + provide the argument conversion_workspace on the command line
       with a fully specified name;
     + provide the argument --region on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination-connection-profile` | DESTINATION_CONNECTION_PROFILE |  | _[This must be specified.]_ ID of the connection_profile or fully qualified identifier for the connection_profile. To set the connection_profile attribute: + provide the argument --destination-connection-profile on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--no-async` |  |  | Waits for the operation in progress to complete before returning. |
| `--filter` | FILTER |  | Filter the entities based on AIP-160 (https://google.aip.dev/160) standard. Example: to filter all tables whose name start with "Employee" and are present under schema "Company", use filter as "Company.Employee* AND type=TABLE" |


**Examples:**
```bash
To apply a conversion workspace:

    $ gcloud database-migration conversion-workspaces apply \
      my-conversion-workspace --region=us-central1 \
      --destination-connection-profile=projects/1234/locations/\
    us-central1/connectionProfiles/destination-connection-profile-name
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/conversion-workspaces/apply)

---
### `gcloud database-migration conversion-workspaces commit`

Commit a Database Migration Service conversion workspace

Commit a Database Migration Service conversion workspace.

**Synopsis:**
```
gcloud database-migration conversion-workspaces commit
    (CONVERSION_WORKSPACE : --region=REGION) [--no-async]
    [--commit-name=COMMIT_NAME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Conversion workspace resource - The conversion workspace to commit. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument conversion_workspace on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONVERSION_WORKSPACE
     ID of the conversion_workspace or fully qualified identifier for the
     conversion_workspace.

     To set the conversion_workspace attribute:
     + provide the argument conversion_workspace on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the conversion_workspace.

     To set the region attribute:
     + provide the argument conversion_workspace on the command line
       with a fully specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--no-async` |  |  | Waits for the operation in progress to complete before returning. |
| `--commit-name` | COMMIT_NAME |  | A user-friendly name for the conversion workspace commit. The commit name can include letters, numbers, spaces, and hyphens, and must start with a letter. |


**Examples:**
```bash
To commit a version of conversion workspace called my-conversion-workspace:

    $ gcloud database-migration conversion-workspaces commit \
      my-conversion-workspace --region=us-central1 \
      --commit-name=my-commit
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/conversion-workspaces/commit)

---
### `gcloud database-migration conversion-workspaces convert`

Convert a Database Migration Service conversion workspace

Convert a Database Migration Service conversion workspace.

**Synopsis:**
```
gcloud database-migration conversion-workspaces convert
    (CONVERSION_WORKSPACE : --region=REGION) [--no-async] [--auto-commit]
    [--filter=FILTER] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Conversion workspace resource - The conversion workspace to convert. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument conversion_workspace on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONVERSION_WORKSPACE
     ID of the conversion_workspace or fully qualified identifier for the
     conversion_workspace.

     To set the conversion_workspace attribute:
     + provide the argument conversion_workspace on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the conversion_workspace.

     To set the region attribute:
     + provide the argument conversion_workspace on the command line
       with a fully specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--no-async` |  |  | Waits for the operation in progress to complete before returning. |
| `--auto-commit` |  |  | Auto commits the conversion workspace. |
| `--filter` | FILTER |  | Filter the entities based on AIP-160 (https://google.aip.dev/160) standard. Example: to filter all tables whose name start with "Employee" and are present under schema "Company", use filter as "Company.Employee* AND type=TABLE" |


**Examples:**
```bash
To convert a conversion workspace:

    $ gcloud database-migration conversion-workspaces convert \
      my-conversion-workspace --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/conversion-workspaces/convert)

---
### `gcloud database-migration conversion-workspaces create`

Create a Database Migration Service conversion workspace

Create a Database Migration Service conversion workspace.

**Synopsis:**
```
gcloud database-migration conversion-workspaces create
    (CONVERSION_WORKSPACE : --region=REGION)
    --destination-database-engine=DESTINATION_DATABASE_ENGINE
    --source-database-engine=SOURCE_DATABASE_ENGINE [--no-async]
    [--destination-database-provider=DESTINATION_DATABASE_PROVIDER;
      default="CLOUDSQL"]
    [--destination-database-version=DESTINATION_DATABASE_VERSION;
      default="unspecified"] [--display-name=DISPLAY_NAME]
    [--global-settings=[KEY=VALUE,...]]
    [--source-database-provider=SOURCE_DATABASE_PROVIDER;
      default="UNSPECIFIED"]
    [--source-database-version=SOURCE_DATABASE_VERSION;
      default="unspecified"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Conversion workspace resource - The conversion workspace to create. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument conversion_workspace on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONVERSION_WORKSPACE
     ID of the conversion_workspace or fully qualified identifier for the
     conversion_workspace.

     To set the conversion_workspace attribute:
     + provide the argument conversion_workspace on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the conversion_workspace.

     To set the region attribute:
     + provide the argument conversion_workspace on the command line
       with a fully specified name;
     + provide the argument --region on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination-database-engine` | DESTINATION_DATABASE_ENGINE |  | Destination database engine type. DESTINATION_DATABASE_ENGINE must be (only one value is supported): POSTGRESQL. |
| `--source-database-engine` | one of: ORACLE, SQL_SERVER |  | Source database engine type. SOURCE_DATABASE_ENGINE must be one of: ORACLE, SQL_SERVER. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--no-async` |  |  | Waits for the operation in progress to complete before returning. |
| `--destination-database-provider` | one of: ALLOYDB, CLOUDSQL | CLOUDSQL | Destination database provider. DESTINATION_DATABASE_PROVIDER must be one of: ALLOYDB, CLOUDSQL. |
| `--destination-database-version` | DESTINATION_DATABASE_VERSION | unspecified | Version number for the database engine. The version number must contain numbers and letters only. Example for PostgreSQL 17.0, version number will be 17.0. |
| `--display-name` | DISPLAY_NAME |  | A user-friendly name for the conversion workspace. The display name can include letters, numbers, spaces, and hyphens, and must start with a letter. The maximum length allowed is 60 characters. |
| `--global-settings` | [KEY=VALUE,...] |  | A generic list of settings for the workspace. The settings are database pair dependant and can indicate default behavior for the mapping rules engine or turn on or off specific features. An object containing a list of "key": "value" pairs. |
| `--source-database-provider` | one of: AMAZON_RDS, AZURE_MANAGED_INSTANCE, AZURE_SQL_DATABASE, CLOUDSQL, UNSPECIFIED | UNSPECIFIED | Source database provider. SOURCE_DATABASE_PROVIDER must be one of: AMAZON_RDS, AZURE_MANAGED_INSTANCE, AZURE_SQL_DATABASE, CLOUDSQL, UNSPECIFIED. |
| `--source-database-version` | SOURCE_DATABASE_VERSION | unspecified | Version number for the database engine. The version number must contain numbers and letters only. Example for Oracle 21c, version number will be 21c. |


**Examples:**
```bash
To create a conversion workspace:

    $ gcloud database-migration conversion-workspaces create \
      my-conversion-workspace --region=us-central1 \
      --display-name=cw1 --source-database-engine=ORACLE \
      --source-database-version=11 \
      --destination-database-engine=POSTGRESQL \
      --destination-database-version=15
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/conversion-workspaces/create)

---
### `gcloud database-migration conversion-workspaces delete`

Delete a Database Migration conversion workspace

Delete a Database Migration conversion workspace.

**Synopsis:**
```
gcloud database-migration conversion-workspaces delete
    (CONVERSION_WORKSPACE : --region=REGION) [--no-async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Conversion workspace resource - The conversion workspace to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument conversion_workspace on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONVERSION_WORKSPACE
     ID of the conversion_workspace or fully qualified identifier for the
     conversion_workspace.

     To set the conversion_workspace attribute:
     + provide the argument conversion_workspace on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the conversion_workspace.

     To set the region attribute:
     + provide the argument conversion_workspace on the command line
       with a fully specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--no-async` |  |  | Waits for the operation in progress to complete before returning. |


**Examples:**
```bash
To delete a conversion workspace called 'my-conversion-workspace', run:

    $ gcloud database-migration conversion-workspaces delete \
      my-conversion-workspace --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/conversion-workspaces/delete)

---
### `gcloud database-migration conversion-workspaces describe`

Show details about a database migration conversion workspace

Show details about a conversion workspace.

**Synopsis:**
```
gcloud database-migration conversion-workspaces describe
    (CONVERSION_WORKSPACE : --region=REGION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Conversion workspace resource - The conversion workspace you want to get
the details of. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument conversion_workspace on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONVERSION_WORKSPACE
     ID of the conversion_workspace or fully qualified identifier for the
     conversion_workspace.

     To set the conversion_workspace attribute:
     + provide the argument conversion_workspace on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the region.

     To set the region attribute:
     + provide the argument conversion_workspace on the command line
       with a fully specified name;
     + provide the argument --region on the command line.
```

**Examples:**
```bash
To show details about a conversion workspace, run:

    $ gcloud database-migration conversion-workspaces describe \
        my-conversion-workspace --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/conversion-workspaces/describe)

---
### `gcloud database-migration conversion-workspaces describe-ddls`

Describe DDLs in a Database Migration Service conversion workspace

Describe DDLs in a Database Migration Service conversion workspace.

**Synopsis:**
```
gcloud database-migration conversion-workspaces describe-ddls
    (CONVERSION_WORKSPACE : --region=REGION) [--commit-id=COMMIT_ID]
    [--tree-type=TREE_TYPE; default="DRAFT"] [--uncommitted]
    [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE; default=100] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Conversion workspace resource - The conversion workspace to describe DDLs.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument conversion_workspace on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONVERSION_WORKSPACE
     ID of the conversion_workspace or fully qualified identifier for the
     conversion_workspace.

     To set the conversion_workspace attribute:
     + provide the argument conversion_workspace on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the conversion_workspace.

     To set the region attribute:
     + provide the argument conversion_workspace on the command line
       with a fully specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--commit-id` | COMMIT_ID |  | Request a specific commit id. If not specified, the entities from the latest commit are returned. |
| `--tree-type` | one of: SOURCE, DRAFT | DRAFT | Tree type for database entities. TREE_TYPE must be one of: SOURCE, DRAFT. |
| `--uncommitted` |  |  | Whether to retrieve the latest committed version of the entities or the latest version. This field is ignored if a specific commit_id is specified. |


**Examples:**
```bash
To describe the DDLs of the draft tree in my-conversion-workspace in a
project and location us-central1, run:

    $ gcloud database-migration conversion-workspaces describe-ddls \
      my-conversion-workspace --region=us-central1

To describe the DDLs of the source tree in a conversion workspace in a
project and location us-central1, run:

    $ gcloud database-migration conversion-workspaces describe-ddls \
      my-conversion-workspace --region=us-central1 --tree-type=SOURCE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/conversion-workspaces/describe-ddls)

---
### `gcloud database-migration conversion-workspaces describe-entities`

Describe database entities in a Database Migration conversion workspace

Describe database entities in a Database Migration conversion workspace.

**Synopsis:**
```
gcloud database-migration conversion-workspaces describe-entities
    (CONVERSION_WORKSPACE : --region=REGION) --tree-type=TREE_TYPE
    [--commit-id=COMMIT_ID] [--uncommitted] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE; default=100]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Conversion workspace resource - The conversion workspace describe
entities. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument conversion_workspace on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONVERSION_WORKSPACE
     ID of the conversion_workspace or fully qualified identifier for the
     conversion_workspace.

     To set the conversion_workspace attribute:
     + provide the argument conversion_workspace on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the conversion_workspace.

     To set the region attribute:
     + provide the argument conversion_workspace on the command line
       with a fully specified name;
     + provide the argument --region on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--tree-type` | one of: SOURCE, DRAFT |  | Tree type for database entities. TREE_TYPE must be one of: SOURCE, DRAFT. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--commit-id` | COMMIT_ID |  | Request a specific commit id. If not specified, the entities from the latest commit are returned. |
| `--uncommitted` |  |  | Whether to retrieve the latest committed version of the entities or the latest version. This field is ignored if a specific commit_id is specified. |


**Examples:**
```bash
To describe the database entities of the source tree in a conversion
workspace in a project and location us-central1, run:

    $ gcloud database-migration conversion-workspaces \
      describe-entities my-conversion-workspace --region=us-central1 \
      --tree-type=SOURCE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/conversion-workspaces/describe-entities)

---
### `gcloud database-migration conversion-workspaces describe-issues`

Describe issues in a Database Migration Service conversion workspace

Describe database entity issues in a Database Migration Services conversion
workspace.

**Synopsis:**
```
gcloud database-migration conversion-workspaces describe-issues
    (CONVERSION_WORKSPACE : --region=REGION) [--commit-id=COMMIT_ID]
    [--uncommitted] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE; default=100] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Conversion workspace resource - The conversion workspace to describe
issues. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument conversion_workspace on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONVERSION_WORKSPACE
     ID of the conversion_workspace or fully qualified identifier for the
     conversion_workspace.

     To set the conversion_workspace attribute:
     + provide the argument conversion_workspace on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the conversion_workspace.

     To set the region attribute:
     + provide the argument conversion_workspace on the command line
       with a fully specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--commit-id` | COMMIT_ID |  | Request a specific commit id. If not specified, the entities from the latest commit are returned. |
| `--uncommitted` |  |  | Whether to retrieve the latest committed version of the entities or the latest version. This field is ignored if a specific commit_id is specified. |


**Examples:**
```bash
To describe the database entity issues in a conversion workspace in a
project and location us-central1, run:

    $ gcloud database-migration conversion-workspaces describe-issues \
      my-conversion-workspace --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/conversion-workspaces/describe-issues)

---
### `gcloud database-migration conversion-workspaces import-rules`

Import mapping rules in a Database Migration Service conversion workspace

Import mapping rules in a Database Migration Service conversion workspace
from a configuration file. For example, for Oracle to PostgreSQL migrations
that could be an Ora2Pg config file.

**Synopsis:**
```
gcloud database-migration conversion-workspaces import-rules
    (CONVERSION_WORKSPACE : --region=REGION)
    --config-files=CONFIG_FILE,[CONFIG_FILE,...] [--auto-commit]
    [--file-format=FILE_FORMAT; default="ORA2PG"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Conversion workspace resource - The conversion workspace to import rules.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument conversion_workspace on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONVERSION_WORKSPACE
     ID of the conversion_workspace or fully qualified identifier for the
     conversion_workspace.

     To set the conversion_workspace attribute:
     + provide the argument conversion_workspace on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the conversion_workspace.

     To set the region attribute:
     + provide the argument conversion_workspace on the command line
       with a fully specified name;
     + provide the argument --region on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--config-files` | CONFIG_FILE,[CONFIG_FILE,...] |  | A list of files to import rules from. Either provide a single file path or if multiple files are to be provided, each file should correspond to one schema. Provide file paths as a comma separated list. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--auto-commit` |  |  | Auto commits the conversion workspace. |
| `--file-format` | FILE_FORMAT | ORA2PG | File format type to import rules from. FILE_FORMAT must be (only one value is supported): ORA2PG. |


**Examples:**
```bash
To import rules in a conversion workspace:

    $ gcloud database-migration conversion-workspaces import-rules \
      my-conversion-workspace --region=us-central1 \
      --file-format=ORA2PG \
      --config-files=PATH1/config1.conf,PATH2/config2.conf
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/conversion-workspaces/import-rules)

---
### `gcloud database-migration conversion-workspaces list`

List conversion workspaces

List conversion workspaces.

**Synopsis:**
```
gcloud database-migration conversion-workspaces list --region=REGION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[This must be specified.]_ ID of the region or fully qualified identifier for the region. To set the region attribute: + provide the argument --region on the command line. |


**Examples:**
```bash
To list all conversion workspaces in a project and location us-central1,
run:

    $ gcloud database-migration conversion-workspaces list \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/conversion-workspaces/list)

---
### `gcloud database-migration conversion-workspaces list-background-jobs`

List background jobs in the conversion workspaces

List background jobs in the conversion workspaces.

**Synopsis:**
```
gcloud database-migration conversion-workspaces list-background-jobs
    (CONVERSION_WORKSPACE : --region=REGION) [--max-size=MAX_SIZE]
    [--most-recent-per-job-type] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Conversion workspace resource - The conversion workspace you want to get
the details of. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument conversion_workspace on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONVERSION_WORKSPACE
     ID of the conversion_workspace or fully qualified identifier for the
     conversion_workspace.

     To set the conversion_workspace attribute:
     + provide the argument conversion_workspace on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the region.

     To set the region attribute:
     + provide the argument conversion_workspace on the command line
       with a fully specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--max-size` | MAX_SIZE |  | The maximum number of jobs to return. The service may return fewer than this value. If unspecified, at most 100 jobs will be returned. The maximum value is 100; values above 100 will be coerced to 100. |
| `--most-recent-per-job-type` |  |  | Returns only the most recent job per job type. |


**Examples:**
```bash
To list the background jobs in a conversion workspaces in a project and
location us-central1, run:

    $ gcloud database-migration conversion-workspaces \
        list-background-jobs my-conversion-workspace \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/conversion-workspaces/list-background-jobs)

---
### `gcloud database-migration conversion-workspaces rollback`

Rollback a Database Migration Service conversion workspace

Rollback a Database Migration Service conversion workspace to the last
committed snapshot.

**Synopsis:**
```
gcloud database-migration conversion-workspaces rollback
    (CONVERSION_WORKSPACE : --region=REGION) [--no-async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Conversion workspace resource - The conversion workspace to rollback. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument conversion_workspace on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONVERSION_WORKSPACE
     ID of the conversion_workspace or fully qualified identifier for the
     conversion_workspace.

     To set the conversion_workspace attribute:
     + provide the argument conversion_workspace on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the conversion_workspace.

     To set the region attribute:
     + provide the argument conversion_workspace on the command line
       with a fully specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--no-async` |  |  | Waits for the operation in progress to complete before returning. |


**Examples:**
```bash
To rollback a conversion workspace to the last committed snapshot:

    $ gcloud database-migration conversion-workspaces rollback \
      my-conversion-workspace --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/conversion-workspaces/rollback)

---
### `gcloud database-migration conversion-workspaces seed`

Seed a Database Migration Service conversion workspace

Seed a Database Migration Service conversion workspace.

**Synopsis:**
```
gcloud database-migration conversion-workspaces seed
    (CONVERSION_WORKSPACE : --region=REGION)
    (--destination-connection-profile=DESTINATION_CONNECTION_PROFILE
      | --source-connection-profile=SOURCE_CONNECTION_PROFILE) [--no-async]
    [--auto-commit] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Conversion workspace resource - The conversion workspace to seed. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument conversion_workspace on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONVERSION_WORKSPACE
     ID of the conversion_workspace or fully qualified identifier for the
     conversion_workspace.

     To set the conversion_workspace attribute:
     + provide the argument conversion_workspace on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the conversion_workspace.

     To set the region attribute:
     + provide the argument conversion_workspace on the command line
       with a fully specified name;
     + provide the argument --region on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination-connection-profile` | DESTINATION_CONNECTION_PROFILE |  | _[+ provide the argument --region on the command line.]_ ID of the connection_profile or fully qualified identifier for the connection_profile. To set the connection_profile attribute: - provide the argument --destination-connection-profile on the command line. |
| `--source-connection-profile` | SOURCE_CONNECTION_PROFILE |  | _[+ provide the argument --region on the command line.]_ ID of the connection_profile or fully qualified identifier for the connection_profile. To set the connection_profile attribute: - provide the argument --source-connection-profile on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--no-async` |  |  | Waits for the operation in progress to complete before returning. |
| `--auto-commit` |  |  | Auto commits the conversion workspace. |


**Examples:**
```bash
To seed a conversion workspace:

    $ gcloud database-migration conversion-workspaces seed \
      my-conversion-workspace --region=us-central1 \
      --source-connection-profile=cp1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/conversion-workspaces/seed)

---
### `gcloud database-migration conversion-workspaces update`

Update a Database Migration Service conversion workspace

Update a Database Migration Service conversion workspace.

**Synopsis:**
```
gcloud database-migration conversion-workspaces update
    (CONVERSION_WORKSPACE : --region=REGION) [--no-async]
    [--display-name=DISPLAY_NAME] [--global-filter=GLOBAL_FILTER]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Conversion workspace resource - The conversion workspace to update. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument conversion_workspace on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONVERSION_WORKSPACE
     ID of the conversion_workspace or fully qualified identifier for the
     conversion_workspace.

     To set the conversion_workspace attribute:
     + provide the argument conversion_workspace on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the conversion_workspace.

     To set the region attribute:
     + provide the argument conversion_workspace on the command line
       with a fully specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--no-async` |  |  | Waits for the operation in progress to complete before returning. |
| `--display-name` | DISPLAY_NAME |  | A user-friendly name for the conversion workspace. The display name can include letters, numbers, spaces, and hyphens, and must start with a letter. The maximum length allowed is 60 characters. |
| `--global-filter` | GLOBAL_FILTER |  | Filter the source entities based on AIP-160 (https://google.aip.dev/160) standard. This filter will be applied to all subsequent operations on the source entities, such as convert and describe-entities. |


**Examples:**
```bash
To update a conversion workspace:

    $ gcloud database-migration conversion-workspaces update \
      my-conversion-workspace --region=us-central1 \
      --display-name=new-display-name
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/conversion-workspaces/update)

---

## `gcloud database-migration conversion-workspaces mapping-rules` — manage Database Migration Service Conversion Workspace mapping rules
### `gcloud database-migration conversion-workspaces mapping-rules list`

List Mapping Rules

List mapping rules.

**Synopsis:**
```
gcloud database-migration conversion-workspaces mapping-rules list
    (--conversion-workspace=CONVERSION_WORKSPACE : --region=REGION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--conversion-workspace` | CONVERSION_WORKSPACE |  | _[This must be specified.]_ ID of the conversion_workspace or fully qualified identifier for the conversion_workspace. To set the conversion_workspace attribute: + provide the argument --conversion-workspace on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--region` | REGION |  | _[This must be specified.]_ The name of the region. To set the region attribute: + provide the argument --conversion-workspace on the command line with a fully specified name; + provide the argument --region on the command line. |


**Examples:**
```bash
To list all mapping rules in a project and location us-central1, run:

    $ gcloud database-migration conversion-workspaces mapping-rules \
        list --conversion-workspace=my-conversion-workspace \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/conversion-workspaces/mapping-rules/list)

---
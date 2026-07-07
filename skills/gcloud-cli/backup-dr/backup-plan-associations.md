# gcloud backup-dr backup-plan-associations

manage Backup and DR backup plan associations

### `gcloud backup-dr backup-plan-associations create`

Create a new backup plan association

Create a new backup plan association in the project. It can only be created
in locations where Backup and DR is available.

**Synopsis:**
```
gcloud backup-dr backup-plan-associations create
    (BACKUP_PLAN_ASSOCIATION
      : --location=LOCATION --workload-project=WORKLOAD_PROJECT)
    --backup-plan=BACKUP_PLAN --resource=RESOURCE
    --resource-type=RESOURCE_TYPE [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup Plan Association resource - Name of the backup plan association to
be created. Once the backup plan association is created, this name can't
be changed. The name must be unique for a project and location. To create
backup plan associations in a project that's different from the backup
plan, use the --workload-project flag. The arguments in this group can be
used to specify the attributes of this resource.

This must be specified.

  BACKUP_PLAN_ASSOCIATION
     ID of the Backup Plan Association or fully qualified identifier for
     the Backup Plan Association.

     To set the name attribute:
     + provide the argument BACKUP_PLAN_ASSOCIATION on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Backup Plan Association.

     To set the location attribute:
     + provide the argument BACKUP_PLAN_ASSOCIATION on the command line
       with a fully specified name;
     + provide the argument --location on the command line.

  --workload-project=WORKLOAD_PROJECT
     Cloud project id for the Backup Plan Association.

     To set the workload-project attribute:
     + provide the argument BACKUP_PLAN_ASSOCIATION on the command line
       with a fully specified name;
     + provide the argument --workload-project on the command line;
     + provide the argument --project on the command line;
     + set the property core/project.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--backup-plan` | BACKUP_PLAN |  | _[This must be specified.]_ ID of the Backup Plan or fully qualified identifier for the Backup Plan. To set the name attribute: + provide the argument --backup-plan on the command line. |
| `--resource` | RESOURCE |  | _[This must be specified.]_ The resource to which the backup plan is to be applied. E.g., projects/sample-project/zones/us-central1-a/instances/sample-instance |
| `--resource-type` | RESOURCE_TYPE |  | _[This must be specified.]_ Type of resource to which the backup plan should be applied. E.g., compute.<UNIVERSE_DOMAIN>.com/Instance |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |


**Examples:**
```bash
To create a new backup plan association sample-bpa in project
sample-project and location us-central1 for resource sample-resource-uri
with backup plan sample-backup-plan, run:

    $ gcloud backup-dr backup-plan-associations create sample-bpa \
        --project=sample-project --location=us-central1 \
        --backup-plan=sample-backup-plan --resource=sample-resource-uri
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/backup-plan-associations/create)

---
### `gcloud backup-dr backup-plan-associations delete`

Delete the specified backup plan association

Delete the specified backup plan association.

**Synopsis:**
```
gcloud backup-dr backup-plan-associations delete
    (BACKUP_PLAN_ASSOCIATION
      : --location=LOCATION --workload-project=WORKLOAD_PROJECT) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup Plan Association resource - Name of the backup plan association to
delete. The arguments in this group can be used to specify the attributes
of this resource.

This must be specified.

  BACKUP_PLAN_ASSOCIATION
     ID of the Backup Plan Association or fully qualified identifier for
     the Backup Plan Association.

     To set the name attribute:
     + provide the argument backup_plan_association on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Backup Plan Association.

     To set the location attribute:
     + provide the argument backup_plan_association on the command line
       with a fully specified name;
     + provide the argument --location on the command line.

  --workload-project=WORKLOAD_PROJECT
     Cloud project id for the Backup Plan Association.

     To set the workload-project attribute:
     + provide the argument backup_plan_association on the command line
       with a fully specified name;
     + provide the argument --workload-project on the command line;
     + provide the argument --project on the command line;
     + set the property core/project.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |


**Examples:**
```bash
To delete a backup plan association sample-bpa in project sample-project
and location us-central1 , run:

    $ gcloud backup-dr backup-plan-associations delete sample-bpa \
        --project=sample-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/backup-plan-associations/delete)

---
### `gcloud backup-dr backup-plan-associations describe`

Show details of the backup plan association

Show all configuration data associated with the specified backup plan
association.

**Synopsis:**
```
gcloud backup-dr backup-plan-associations describe
    (BACKUP_PLAN_ASSOCIATION : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup plan association resource - Name of the backup plan association to
describe. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument backup_plan_association on the command line with
   a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP_PLAN_ASSOCIATION
     ID of the backup_plan_association or fully qualified identifier for
     the backup_plan_association.

     To set the backup_plan_association attribute:
     + provide the argument backup_plan_association on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location ID of the resource.

     To set the location attribute:
     + provide the argument backup_plan_association on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To view details for backup plan association BACKUP_PLAN_ASSOCIATION, run:

    $ gcloud backup-dr backup-plan-associations describe \
        BACKUP_PLAN_ASSOCIATION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/backup-plan-associations/describe)

---
### `gcloud backup-dr backup-plan-associations fetch-for-resource-type`

Fetch Backup Plan Associations for a given resource type and location

Fetch Backup Plan Associations for a given resource type and location. List
backup plan associations in a specified location and resource type in a
project.

**Synopsis:**
```
gcloud backup-dr backup-plan-associations fetch-for-resource-type
    RESOURCE_TYPE --location=LOCATION [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RESOURCE_TYPE
   Resource type for which backup plan associations should be fetched.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Location for which backup plan associations should be fetched. |


**Examples:**
```bash
To list backup plan associations for Cloud SQL with location us-central1,
run:

    $ gcloud backup-dr backup-plan-associations \
        fetch-for-resource-type sqladmin.googleapis.com/Instance \
        --location="us-central1"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/backup-plan-associations/fetch-for-resource-type)

---
### `gcloud backup-dr backup-plan-associations list`

List Backup and DR backup plan associations

List backup plan associations in the project for a specified location.

**Synopsis:**
```
gcloud backup-dr backup-plan-associations list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + default is all locations . |


**Examples:**
```bash
To list backup plan associations for all locations, run:

    $ gcloud backup-dr backup-plan-associations list

To list backup plan associations in a location my-location, run:

    $ gcloud backup-dr backup-plan-associations list \
        --location=my-location
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/backup-plan-associations/list)

---
### `gcloud backup-dr backup-plan-associations trigger-backup`

Create an on-demand backup for a resource

Create an on-demand backup for a resource. Trigger an on demand backup for
the given backup rule.

**Synopsis:**
```
gcloud backup-dr backup-plan-associations trigger-backup
    (BACKUP_PLAN_ASSOCIATION
      : --location=LOCATION --workload-project=WORKLOAD_PROJECT) [--async]
    [--labels=[KEY=VALUE,...]]
    [--backup-rule-id=BACKUP_RULE_ID
      | --custom-retention-days=CUSTOM_RETENTION_DAYS]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup Plan Association resource - Name of an existing backup plan
association to use for creating an on-demand backup. The arguments in this
group can be used to specify the attributes of this resource.

This must be specified.

  BACKUP_PLAN_ASSOCIATION
     ID of the Backup Plan Association or fully qualified identifier for
     the Backup Plan Association.

     To set the name attribute:
     + provide the argument BACKUP_PLAN_ASSOCIATION on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Backup Plan Association.

     To set the location attribute:
     + provide the argument BACKUP_PLAN_ASSOCIATION on the command line
       with a fully specified name;
     + provide the argument --location on the command line.

  --workload-project=WORKLOAD_PROJECT
     Cloud project id for the Backup Plan Association.

     To set the workload-project attribute:
     + provide the argument BACKUP_PLAN_ASSOCIATION on the command line
       with a fully specified name;
     + provide the argument --workload-project on the command line;
     + provide the argument --project on the command line;
     + set the property core/project.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--labels` | [KEY=VALUE,...] |  | Labels to be applied to the backup. |


**Examples:**
```bash
To trigger an on demand backup for a backup plan association sample-bpa in
project sample-project and location us-central1 with backup rule
sample-backup-rule, run:

    $ gcloud backup-dr backup-plan-associations trigger-backup \
        sample-bpa --project=sample-project --location=us-central1 \
        --backup-rule-id=sample-backup-rule
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/backup-plan-associations/trigger-backup)

---
### `gcloud backup-dr backup-plan-associations update`

Update a specific backup plan within a backup plan association

Update a specific backup plan within a backup plan association.

**Synopsis:**
```
gcloud backup-dr backup-plan-associations update
    (BACKUP_PLAN_ASSOCIATION
      : --location=LOCATION --workload-project=WORKLOAD_PROJECT)
    --backup-plan=BACKUP_PLAN [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup Plan Association resource - Backup plan association to be updated.
To update backup plan associations in a project that's different from the
backup plan, use the --workload-project flag. The arguments in this group
can be used to specify the attributes of this resource.

This must be specified.

  BACKUP_PLAN_ASSOCIATION
     ID of the Backup Plan Association or fully qualified identifier for
     the Backup Plan Association.

     To set the name attribute:
     + provide the argument BACKUP_PLAN_ASSOCIATION on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Backup Plan Association.

     To set the location attribute:
     + provide the argument BACKUP_PLAN_ASSOCIATION on the command line
       with a fully specified name;
     + provide the argument --location on the command line.

  --workload-project=WORKLOAD_PROJECT
     Cloud project id for the Backup Plan Association.

     To set the workload-project attribute:
     + provide the argument BACKUP_PLAN_ASSOCIATION on the command line
       with a fully specified name;
     + provide the argument --workload-project on the command line;
     + provide the argument --project on the command line;
     + set the property core/project.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--backup-plan` | BACKUP_PLAN |  | _[This must be specified.]_ ID of the Backup Plan or fully qualified identifier for the Backup Plan. To set the name attribute: + provide the argument --backup-plan on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |


**Examples:**
```bash
To update backup plan association sample-bpa in project sample-project and
location us-central1 with backup plan sample-backup-plan in the same
project and location, run:

    $ gcloud backup-dr backup-plan-associations update sample-bpa \
        --project=sample-project --location=us-central1 \
        --backup-plan=sample-backup-plan

To update backup plan association sample-bpa-uri with backup plan
sample-backup-plan-uri (using full URIs), run:

    $ gcloud backup-dr backup-plan-associations update sample-bpa-uri \
        --backup-plan=sample-backup-plan-uri

To update backup plan association sample-bpa in location us-central1 with
backup plan sample-backup-plan-uri, run:

    $ gcloud backup-dr backup-plan-associations update sample-bpa \
        --location=us-central1 --backup-plan=sample-backup-plan-uri

To update backup plan association sample-bpa in project workload-project
and location us-central1 with backup plan sample-backup-plan in project
sample-project, run:

    $ gcloud backup-dr backup-plan-associations update sample-bpa \
        --workload-project=workload-project --location=us-central1 \
        --backup-plan=sample-backup-plan --project=sample-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/backup-plan-associations/update)

---
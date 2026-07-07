# gcloud backup-dr backup-plan-revisions

view Backup and DR backup plan revisions

### `gcloud backup-dr backup-plan-revisions describe`

Show details of the backup plan revision

Show all data associated with the specified backup plan revision.

**Synopsis:**
```
gcloud backup-dr backup-plan-revisions describe
    (BACKUP_PLAN_REVISION : --backup_plan=BACKUP_PLAN --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup plan revision resource - Name of the backup plan revision to
describe. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument backup_plan_revision on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP_PLAN_REVISION
     ID of the backup_plan_revision or fully qualified identifier for the
     backup_plan_revision.

     To set the backup_plan_revision attribute:
     + provide the argument backup_plan_revision on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --backup_plan=BACKUP_PLAN
     The ID of the Backup Plan

     To set the backup_plan attribute:
     + provide the argument backup_plan_revision on the command line
       with a fully specified name;
     + provide the argument --backup_plan on the command line.

  --location=LOCATION
     Location ID of the resource.

     To set the location attribute:
     + provide the argument backup_plan_revision on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To view details for backup plan revision 'BACKUP_PLAN_REVISION', run:

    $ gcloud backup-dr backup-plan-revisions describe \
        BACKUP_PLAN_REVISION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/backup-plan-revisions/describe)

---
### `gcloud backup-dr backup-plan-revisions list`

List backup plan revisions

List backup plan revisions in the project.

**Synopsis:**
```
gcloud backup-dr backup-plan-revisions list
    [--backup-plan=BACKUP_PLAN --location=LOCATION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--backup-plan` | BACKUP_PLAN |  | _[* set the property core/project.]_ ID of the backup_plan or fully qualified identifier for the backup_plan. To set the backup-plan attribute: + provide the argument --backup-plan on the command line; + default is all backup plans . |
| `--location` | LOCATION |  | _[* set the property core/project.]_ Location ID of the resource. To set the location attribute: + provide the argument --backup-plan on the command line with a fully specified name; + default is all backup plans with a fully specified name; + provide the argument --location on the command line; + default is all locations . |


**Examples:**
```bash
To list backup plan revisions for all backup plans and locations, run:

    $ gcloud backup-dr backup-plan-revisions list

To list all backup plan revisions for a backup plan my-backup-plan, run:

    $ gcloud backup-dr backup-plan-revisions list \
        --backup-plan=my-backup-plan

To list all backup plan revisions for a backup plan my-backup-plan in
location my-location, run:

    $ gcloud backup-dr backup-plan-revisions list \
        --backup-plan=my-backup-plan --location=my-location
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/backup-plan-revisions/list)

---
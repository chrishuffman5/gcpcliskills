# gcloud backup-dr backup-plans

manage Backup and DR backup plans

### `gcloud backup-dr backup-plans create`

Creates a new Backup Plan

Create a new backup plan in the project. It can only be created in
locations where Backup and DR is available.

**Synopsis:**
```
gcloud backup-dr backup-plans create (BACKUP_PLAN : --location=LOCATION)
    --backup-rule=[PROPERTY=VALUE,...] --backup-vault=BACKUP_VAULT
    --resource-type=RESOURCE_TYPE [--async] [--description=DESCRIPTION]
    [--labels=[KEY=VALUE,...]]
    [--max-custom-on-demand-retention-days=MAX_CUSTOM_ON_DEMAND_RETENTION_DAYS]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup Plan resource - Name of the backup plan to be created. Once the
backup plan is created, this name can't be changed. The name must be
unique for a project and location. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument BACKUP_PLAN on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP_PLAN
     ID of the Backup Plan or fully qualified identifier for the Backup
     Plan.

     To set the name attribute:
     + provide the argument BACKUP_PLAN on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Backup Plan.

     To set the location attribute:
     + provide the argument BACKUP_PLAN on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--backup-rule` | [PROPERTY=VALUE,...] |  | Backup rule that defines parameters for when and how a backup is created. This flag can be repeated to create more backup rules. Parameters for the backup rule include: rule-id Name of the backup rule. The name must be unique and start with a lowercase letter followed by up to 62 lowercase letters, numbers, or hyphens. retention-days Duration for which backup data should be retained. It must be defined in "days". The value should be greater than or equal to the enforced retention period set for the backup vault. recurrence Frequency for the backup schedule. It must be either: HOURLY, DAILY, WEEKLY, MONTHLY or YEARLY. backup-window-start Start time of the interval during which backup jobs should be executed. It can be defined as backup-window-start=2, that means backup window starts at 2 a.m. The start time and end time must have an interval of 6 hours. backup-window-end End time of the interval during which backup jobs should be executed. It can be defined as backup-window-end=14, that means backup window ends at 2 p.m. The start time and end time must have an interval of 6 hours. Jobs are queued at the beginning of the window and will be marked as SKIPPED if they do not start by the end time. Jobs that are in progress will not be canceled at the end time. time-zone The time zone to be used for the backup schedule. The value must exist in the IANA tz database (https://www.iana.org/time-zones). The default value is UTC. E.g., Europe/Paris Following flags are mutually exclusive: hourly-frequency Frequency for hourly backups. An hourly frequency of 2 means backup jobs will run every 2 hours from start time till the end time defined. The hourly frequency must be between 4 and 23. The value is needed only if recurrence type is HOURLY. days-of-week Days of the week when the backup job should be executed. The value is needed if recurrence type is WEEKLY. E.g., MONDAY,TUESDAY days-of-month Days of the month when the backup job should be executed. The value is needed only if recurrence type is YEARLY. E.g.,"1,5,14" months Month for the backup schedule. The value is needed only if recurrence type is YEARLY. E.g., JANUARY, MARCH week-day-of-month Recurring day of the week in the month or year when the backup job should be executed. E.g. FIRST-SUNDAY, THIRD-MONDAY. The value can only be provided if the recurrence type is MONTHLY or YEARLY. Allowed values for the number of week - FIRST, SECOND, THIRD, FOURTH, LAST. Allowed values for days of the week - MONDAY to SUNDAY. E.g., "rule-id=sample-daily-rule,recurrence=WEEKLY,backup-window-start=2,backup-window-end=14,retention-days=20,days-of-week='SUNDAY MONDAY'" |
| `--resource-type` | RESOURCE_TYPE |  | _[+ provide the argument --backup-vault on the command line.]_ Type of resource to which the backup plan should be applied. E.g., compute.<UNIVERSE_DOMAIN>.com/Instance |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--description` | DESCRIPTION |  | Provide a description of the backup plan, such as specific use cases and relevant details, in 2048 characters or less. E.g., This is a backup plan that performs a daily backup at 6 p.m. and retains data for 3 months. |
| `--labels` | [KEY=VALUE,...] |  | If you have assigned labels to your resources for grouping, you can provide the label using this flag.A label is a key-value pair. Keys must start with a lowercase character and contain only hyphens (-), underscores (), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (), lowercase characters, and numbers. |
| `--max-custom-on-demand-retention-days` | MAX_CUSTOM_ON_DEMAND_RETENTION_DAYS |  | Configure the maximum retention period for on-demand backups. The value must be greater than or equal to the minimum enforced retention period set on the backup vault. |


**Examples:**
```bash
To create a new backup plan sample-backup-plan in project sample-project,
at location us-central1, with resource-type
compute.<UNIVERSE_DOMAIN>.com/Instance and backup-vault backup-vault with 2
backup-rules:

run:

    $ gcloud backup-dr backup-plans create sample-backup-plan \
        --project=sample-project --location=us-central1 \
        --resource-type 'compute.<UNIVERSE_DOMAIN>.com/Instance' \
        --backup-vault <BACKUP-VAULT> --backup-rule <BACKUP-RULE> \
        --backup-rule <BACKUP-RULE>

Backup Rule Examples:

1. Hourly backup rule with hourly backup frequency of 6 hours and store it
for 30 days, and expect the backups to run only between 10:00 to 20:00 UTC

<BACKUP-RULE>:
rule-id=sample-hourly-rule,retention-days=30,recurrence=HOURLY,hourly-frequency=6,time-zone=UTC,backup-window-start=10,backup-window-end=20

Properties:
  o rule-id = "sample-hourly-rule"
  o retention-days = 30
  o recurrence = HOURLY
  o hourly-frequency = 6
  o time-zone = UTC
  o backup-window-start = 10
  o backup-window-end = 20

2. Daily backup rule with daily backup frequency of 6 hours and store it
for 7 days

<BACKUP-RULE>:
rule-id=sample-daily-rule,retention-days=7,recurrence=DAILY,backup-window-start=1,backup-window-end=14

Properties:
  o rule-id = "sample-daily-rule"
  o retention-days = 7
  o recurrence = DAILY
  o backup-window-start = 1
  o backup-window-end = 14

3. Weekly backup rule with weekly backup frequency on every MONDAY & FRIDAY
and store it for 21 days

<BACKUP-RULE>:
rule-id=sample-weekly-rule,retention-days=21,recurrence=WEEKLY,days-of-week="MONDAY
FRIDAY",backup-window-start=10,backup-window-end=20

Properties:
  o rule-id = "sample-weekly-rule"
  o retention-days: 21
  o recurrence = WEEKLY
  o days-of-week = "MONDAY FRIDAY"
  o backup-window-start = 10
  o backup-window-end = 20
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/backup-plans/create)

---
### `gcloud backup-dr backup-plans delete`

Deletes a Backup Plan

Deletes a Backup Plan.

**Synopsis:**
```
gcloud backup-dr backup-plans delete (BACKUP_PLAN : --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup Plan resource - Name of the backup plan to delete The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument backup_plan on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP_PLAN
     ID of the Backup Plan or fully qualified identifier for the Backup
     Plan.

     To set the name attribute:
     + provide the argument backup_plan on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Backup Plan.

     To set the location attribute:
     + provide the argument backup_plan on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |


**Examples:**
```bash
To delete a backup plan sample-backup-plan in project sample-project and
location us-central1 , run:

    $ gcloud backup-dr backup-plans delete sample-backup-plan \
        --project=sample-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/backup-plans/delete)

---
### `gcloud backup-dr backup-plans describe`

Show details of the backup plan

Show all data associated with the specified backup plan.

**Synopsis:**
```
gcloud backup-dr backup-plans describe (BACKUP_PLAN : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup plan resource - Name of the backup plan to describe. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument backup_plan on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP_PLAN
     ID of the backup_plan or fully qualified identifier for the
     backup_plan.

     To set the backup_plan attribute:
     + provide the argument backup_plan on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location ID of the resource.

     To set the location attribute:
     + provide the argument backup_plan on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To view details for backup plan 'BACKUP_PLAN', run:

    $ gcloud backup-dr backup-plans describe BACKUP_PLAN
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/backup-plans/describe)

---
### `gcloud backup-dr backup-plans list`

List backup plans in the project

List backup plans in the project.

**Synopsis:**
```
gcloud backup-dr backup-plans list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + default is all locations . |


**Examples:**
```bash
To list backup plans for all locations, run:

    $ gcloud backup-dr backup-plans list

To list backup plans in a location "my-location", run:

    $ gcloud backup-dr backup-plans list --location=my-location
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/backup-plans/list)

---
### `gcloud backup-dr backup-plans update`

Update a specific backup plan

Update a specific backup plan in the project. It can only be updated in
regions supported by the Backup and DR Service.

**Synopsis:**
```
gcloud backup-dr backup-plans update (BACKUP_PLAN : --location=LOCATION)
    [--add-backup-rule=[PROPERTY=VALUE,...]] [--async]
    [--backup-rule=[PROPERTY=VALUE,...]]
    [--backup-rules-from-file=PATH_TO_FILE] [--description=DESCRIPTION]
    [--max-custom-on-demand-retention-days=MAX_CUSTOM_ON_DEMAND_RETENTION_DAYS]
    [--remove-backup-rule=RULE-ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup Plan resource - Name of the backup plan to be updated. The name
must be unique for a project and location. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument backup_plan on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP_PLAN
     ID of the Backup Plan or fully qualified identifier for the Backup
     Plan.

     To set the name attribute:
     + provide the argument backup_plan on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Backup Plan.

     To set the location attribute:
     + provide the argument backup_plan on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--add-backup-rule` | [PROPERTY=VALUE,...] |  | Parameters of backup rule to be added to the Backup Plan. This flag can be repeated to add more backup rules. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--backup-rule` | [PROPERTY=VALUE,...] |  | Full definition of an existing backup rule with updated values. The existing backup rule is replaced by this new set of values. This flag can be repeated to update multiple backup rules. It is not allowed to pass the same rule-id in this flag more than once in the same command. Parameters for the backup rule include: rule-id Name of the backup rule. The name must be unique and start with a lowercase letter followed by up to 62 lowercase letters, numbers, or hyphens. retention-days Duration for which backup data should be retained. It must be defined in "days". The value should be greater than or equal to the enforced retention period set for the backup vault. recurrence Frequency for the backup schedule. It must be either: HOURLY, DAILY, WEEKLY, MONTHLY or YEARLY. backup-window-start Start time of the interval during which backup jobs should be executed. It can be defined as backup-window-start=2, that means backup window starts at 2 a.m. The start time and end time must have an interval of 6 hours. backup-window-end End time of the interval during which backup jobs should be executed. It can be defined as backup-window-end=14, that means backup window ends at 2 p.m. The start time and end time must have an interval of 6 hours. Jobs are queued at the beginning of the window and will be marked as SKIPPED if they do not start by the end time. Jobs that are in progress will not be canceled at the end time. time-zone The time zone to be used for the backup schedule. The value must exist in the IANA tz database (https://www.iana.org/time-zones). The default value is UTC. E.g., Europe/Paris Following flags are mutually exclusive: hourly-frequency Frequency for hourly backups. An hourly frequency of 2 means backup jobs will run every 2 hours from start time till the end time defined. The hourly frequency must be between 4 and 23. The value is needed only if recurrence type is HOURLY. days-of-week Days of the week when the backup job should be executed. The value is needed if recurrence type is WEEKLY. E.g., MONDAY,TUESDAY days-of-month Days of the month when the backup job should be executed. The value is needed only if recurrence type is YEARLY. E.g.,"1,5,14" months Month for the backup schedule. The value is needed only if recurrence type is YEARLY. E.g., JANUARY, MARCH week-day-of-month Recurring day of the week in the month or year when the backup job should be executed. E.g. FIRST-SUNDAY, THIRD-MONDAY. The value can only be provided if the recurrence type is MONTHLY or YEARLY. Allowed values for the number of week - FIRST, SECOND, THIRD, FOURTH, LAST. Allowed values for days of the week - MONDAY to SUNDAY. E.g., "rule-id=sample-daily-rule,recurrence=WEEKLY,backup-window-start=2,backup-window-end=14,retention-days=20,days-of-week='SUNDAY MONDAY'" |
| `--backup-rules-from-file` | PATH_TO_FILE |  | Path to a YAML or JSON file containing backup rules. Use a full or relative path to a local file containing the value of backup_rules. |
| `--description` | DESCRIPTION |  | Provide a description of the backup plan, such as specific use cases and relevant details, in 2048 characters or less. E.g., This is a backup plan that performs a daily backup at 6 p.m. and retains data for 3 months. |
| `--max-custom-on-demand-retention-days` | MAX_CUSTOM_ON_DEMAND_RETENTION_DAYS |  | Configure the maximum retention period for on-demand backups. The value must be greater than or equal to the minimum enforced retention period set on the backup vault. |
| `--remove-backup-rule` | RULE-ID |  | Name of an existing backup rule to be removed from the Backup Plan. This flag can be repeated to remove more backup rules. |


**Examples:**
```bash
To update 2 backup rules and description of an existing backup plan
sample-backup-plan in project sample-project, at location us-central1:

run:

    $ gcloud backup-dr backup-plans update sample-backup-plan \
        --project=sample-project --location=us-central1 \
        --backup-rule <BACKUP-RULE> --backup-rule <BACKUP-RULE> \
        --description "This is a sample backup plan"

To add backup rules to an existing backup plan sample-backup-plan in
project sample-project, at location us-central1:

run:

    $ gcloud backup-dr backup-plans update sample-backup-plan \
        --project=sample-project --location=us-central1 \
        --add-backup-rule <BACKUP-RULE> --add-backup-rule <BACKUP-RULE>

To remove a backup rule with id sample-daily-rule from an existing backup
plan sample-backup-plan in project sample-project, at location us-central1:

run:

    $ gcloud backup-dr backup-plans update sample-backup-plan \
        --project=sample-project --location=us-central1 \
        --remove-backup-rule sample-daily-rule

To override backup rules in an existing backup plan sample-backup-plan in
project sample-project, at location us-central1, pass a file path
containing backup rules in YAML or JSON format: This flag is mutually
exclusive with --add-backup-rule, --remove-backup-rule and --backup-rule
flags.

run:        $ gcloud backup-dr backup-plans update sample-backup-plan \
        --project=sample-project --location=us-central1 \
        --backup-rules-fom-file <FILE_PATH>

Backup Rule Examples:

1. Hourly backup rule with hourly backup frequency of 6 hours and store it
for 30 days, and expect the backups to run only between 10:00 to 20:00 UTC

<BACKUP-RULE>:
rule-id=sample-hourly-rule,retention-days=30,recurrence=HOURLY,hourly-frequency=6,time-zone=UTC,backup-window-start=10,backup-window-end=20

Properties:
  o rule-id = "sample-hourly-rule"
  o retention-days = 30
  o recurrence = HOURLY
  o hourly-frequency = 6
  o time-zone = UTC
  o backup-window-start = 10
  o backup-window-end = 20

2. Daily backup rule with daily backup frequency of 6 hours and store it
for 7 days

<BACKUP-RULE>:
rule-id=sample-daily-rule,retention-days=7,recurrence=DAILY,backup-window-start=1,backup-window-end=14

Properties:
  o rule-id = "sample-daily-rule"
  o retention-days = 7
  o recurrence = DAILY
  o backup-window-start = 1
  o backup-window-end = 14

3. Weekly backup rule with weekly backup frequency on every MONDAY & FRIDAY
and store it for 21 days

<BACKUP-RULE>:
rule-id=sample-weekly-rule,retention-days=21,recurrence=WEEKLY,days-of-week="MONDAY
FRIDAY",backup-window-start=10,backup-window-end=20

Properties:
  o rule-id = "sample-weekly-rule"
  o retention-days: 21
  o recurrence = WEEKLY
  o days-of-week = "MONDAY FRIDAY"
  o backup-window-start = 10
  o backup-window-end = 20

YAML and JSON file examples:

YAML file example:

    backup-rules:
    - rule-id: weekly-rule
      retention-days: 7
      recurrence: WEEKLY
      backup-window-start: 0
      backup-window-end: 23
      days-of-week: [MONDAY, TUESDAY]
      time-zone: UTC
    - rule-id: daily-rule
      retention-days: 1
      recurrence: DAILY
      backup-window-start: 1
      backup-window-end: 24
      time-zone: UTC

JSON file example:        {
      "backup-rules": [
        {
          "rule-id": "weekly-rule",
          "retention-days": 7,
          "recurrence": "WEEKLY",
          "backup-window-start": 0,
          "backup-window-end": 23,
          "days-of-week": ["MONDAY", "TUESDAY"],
          "time-zone": "UTC"
        },
        {
          "rule-id": "daily-rule",
          "retention-days": 1,
          "recurrence": "DAILY",
          "backup-window-start": 1,
          "backup-window-end": 24,
          "time-zone": "UTC"
        }
      ]
    }
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/backup-plans/update)

---
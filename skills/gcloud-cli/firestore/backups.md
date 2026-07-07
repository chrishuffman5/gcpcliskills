# gcloud firestore backups

the set of commands to manage backups for Cloud Firestore

### `gcloud firestore backups delete`

Deletes a Cloud Firestore backup

**Synopsis:**
```
gcloud firestore backups delete --backup=BACKUP --location=LOCATION
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--backup` | BACKUP |  | The backup to operate on. For example, to operate on backup cf9f748a-7980-4703-b1a1-d1ffff591db0: $ gcloud firestore backups delete \ --backup='cf9f748a-7980-4703-b1a1-d1ffff591db0' |
| `--location` | LOCATION |  | The location to operate on. Available locations are listed at https://cloud.google.com/firestore/docs/locations. For example, to operate on location us-east1: $ gcloud firestore backups delete --location='us-east1' |


**Examples:**
```bash
To delete cf9f748a-7980-4703-b1a1-d1ffff591db0 backup in us-east1.

    $ gcloud firestore backups delete --location=us-east1 \
      --backup=cf9f748a-7980-4703-b1a1-d1ffff591db0
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/backups/delete)

---
### `gcloud firestore backups describe`

Retrieves information about a Cloud Firestore backup

**Synopsis:**
```
gcloud firestore backups describe --backup=BACKUP --location=LOCATION
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--backup` | BACKUP |  | The backup to operate on. For example, to operate on backup cf9f748a-7980-4703-b1a1-d1ffff591db0: $ gcloud firestore backups describe \ --backup='cf9f748a-7980-4703-b1a1-d1ffff591db0' |
| `--location` | LOCATION |  | The location to operate on. Available locations are listed at https://cloud.google.com/firestore/docs/locations. For example, to operate on location us-east1: $ gcloud firestore backups describe --location='us-east1' |


**Examples:**
```bash
To retrieve information about the cf9f748a-7980-4703-b1a1-d1ffff591db0
backup in us-east1.

    $ gcloud firestore backups describe --location=us-east1 \
      --backup=cf9f748a-7980-4703-b1a1-d1ffff591db0
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/backups/describe)

---
### `gcloud firestore backups list`

List backups available to Cloud Firestore

**Synopsis:**
```
gcloud firestore backups list [--location=LOCATION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | The location to operate on. Available locations are listed at https://cloud.google.com/firestore/docs/locations. For example, to operate on location us-east1: $ gcloud firestore backups list --location='us-east1' |


**Examples:**
```bash
To list all backups in location us-east1.

    $ gcloud firestore backups list --location=us-east1 \
      --format="table(name, database, state)"

To list all backups in all location.

    $ gcloud firestore backups list \
      --format="table(name, database, state)"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/backups/list)

---

## `gcloud firestore backups schedules` — manage the backup schedules for a Cloud Firestore Database
### `gcloud firestore backups schedules create`

Creates a Cloud Firestore backup schedule

**Synopsis:**
```
gcloud firestore backups schedules create --database=DATABASE
    --retention=RETENTION
    (--recurrence=RECURRENCE : --day-of-week=DAY_OF_WEEK)
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--database` | DATABASE |  | The database to operate on. For example, to operate on database foo: $ gcloud firestore backups schedules create --database='foo' |
| `--retention` | RETENTION |  | The rention of the backup. At what relative time in the future, compared to the creation time of the backup should the backup be deleted, i.e. keep backups for 7 days. For example, to set retention as 7 days. $ gcloud firestore backups schedules create --retention=7d |


**Examples:**
```bash
To create a backup schedule with 7 days retention and daily recurrence
under database testdb.

    $ gcloud firestore backups schedules create --database=testdb \
      --retention=7d --recurrence=daily

To create a backup schedule with 7 days retention and weekly recurrence on
Monday under database testdb.

    $ gcloud firestore backups schedules create --database=testdb \
      --retention=7d --recurrence=weekly --day-of-week=MON
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/backups/schedules/create)

---
### `gcloud firestore backups schedules delete`

Deletes a Cloud Firestore backup schedule

**Synopsis:**
```
gcloud firestore backups schedules delete --backup-schedule=BACKUP_SCHEDULE
    --database=DATABASE [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--backup-schedule` | BACKUP_SCHEDULE |  | The backup schedule to operate on. For example, to operate on backup schedule 091a49a0-223f-4c98-8c69-a284abbdb26b: $ gcloud firestore backups schedules delete \ --backup-schedule='091a49a0-223f-4c98-8c69-a284abbdb26b' |
| `--database` | DATABASE |  | The database to operate on. For example, to operate on database foo: $ gcloud firestore backups schedules delete --database='foo' |


**Examples:**
```bash
To delete backup schedule 'cf9f748a-7980-4703-b1a1-d1ffff591db0' under
database testdb.

    $ gcloud firestore backups schedules delete --database='testdb' \
      --backup-schedule='cf9f748a-7980-4703-b1a1-d1ffff591db0'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/backups/schedules/delete)

---
### `gcloud firestore backups schedules describe`

Describes a Cloud Firestore backup schedule

**Synopsis:**
```
gcloud firestore backups schedules describe
    --backup-schedule=BACKUP_SCHEDULE --database=DATABASE
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--backup-schedule` | BACKUP_SCHEDULE |  | The backup schedule to operate on. For example, to operate on backup schedule 091a49a0-223f-4c98-8c69-a284abbdb26b: $ gcloud firestore backups schedules describe \ --backup-schedule='091a49a0-223f-4c98-8c69-a284abbdb26b' |
| `--database` | DATABASE |  | The database to operate on. For example, to operate on database foo: $ gcloud firestore backups schedules describe --database='foo' |


**Examples:**
```bash
To describe backup schedule 'cf9f748a-7980-4703-b1a1-d1ffff591db0' under
database testdb.

    $ gcloud firestore backups schedules describe --database='testdb' \
      --backup-schedule='cf9f748a-7980-4703-b1a1-d1ffff591db0'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/backups/schedules/describe)

---
### `gcloud firestore backups schedules list`

Lists backup schedules under a Cloud Firestore database

**Synopsis:**
```
gcloud firestore backups schedules list --database=DATABASE
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--database` | DATABASE |  | The database to operate on. For example, to operate on database foo: $ gcloud firestore backups schedules list --database='foo' |


**Examples:**
```bash
To list all backup schedules under database testdb.

    $ gcloud firestore backups schedules list --database='testdb'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/backups/schedules/list)

---
### `gcloud firestore backups schedules update`

Updates a Cloud Firestore backup schedule

**Synopsis:**
```
gcloud firestore backups schedules update --backup-schedule=BACKUP_SCHEDULE
    --database=DATABASE [--retention=RETENTION] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--backup-schedule` | BACKUP_SCHEDULE |  | The backup schedule to operate on. For example, to operate on backup schedule 091a49a0-223f-4c98-8c69-a284abbdb26b: $ gcloud firestore backups schedules update \ --backup-schedule='091a49a0-223f-4c98-8c69-a284abbdb26b' |
| `--database` | DATABASE |  | The database to operate on. For example, to operate on database foo: $ gcloud firestore backups schedules update --database='foo' |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--retention` | RETENTION |  | The rention of the backup. At what relative time in the future, compared to the creation time of the backup should the backup be deleted, i.e. keep backups for 7 days. For example, to set retention as 7 days. $ gcloud firestore backups schedules update --retention=7d |


**Examples:**
```bash
To update backup schedule 'cf9f748a-7980-4703-b1a1-d1ffff591db0' under
database testdb to 7 days retention.

    $ gcloud firestore backups schedules update --database='testdb' \
      --backup-schedule='cf9f748a-7980-4703-b1a1-d1ffff591db0' \
      --retention='7d'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/backups/schedules/update)

---
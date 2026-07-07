# gcloud database-migration objects

manage Database Migration Service migration job objects

### `gcloud database-migration objects list`

List a DMS migration job objects

List migration job objects.

**Synopsis:**
```
gcloud database-migration objects list
    (--migration-job=MIGRATION_JOB : --region=REGION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--migration-job` | MIGRATION_JOB |  | _[This must be specified.]_ ID of the migration_job or fully qualified identifier for the migration_job. To set the migration_job attribute: + provide the argument --migration-job on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--region` | REGION |  | _[This must be specified.]_ The Cloud region for the migration_job. To set the region attribute: + provide the argument --migration-job on the command line with a fully specified name; + provide the argument --region on the command line. |


**Examples:**
```bash
To list all objects in a migration job and location 'us-central1', run:

    $ gcloud database-migration objects list --migration-job=mj \
      --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/objects/list)

---
### `gcloud database-migration objects lookup`

Lookup a DMS migration job object

Lookup a migration job object by its source object identifier (e.g.
database)

**Synopsis:**
```
gcloud database-migration objects lookup
    (--database=DATABASE --schema=SCHEMA --table=TABLE)
    (--migration-job=MIGRATION_JOB : --region=REGION) [--type=TYPE]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--database` | DATABASE |  | _[At least one of these must be specified:]_ The name of the database to lookup. |
| `--schema` | SCHEMA |  | _[At least one of these must be specified:]_ The name of the schema to lookup. |
| `--table` | TABLE |  | _[At least one of these must be specified:]_ The name of the table to lookup. |
| `--migration-job` | MIGRATION_JOB |  | _[This must be specified.]_ ID of the migration_job or fully qualified identifier for the migration_job. To set the migration_job attribute: + provide the argument --migration-job on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--region` | REGION |  | _[This must be specified.]_ The Cloud region for the migration_job. To set the region attribute: + provide the argument --migration-job on the command line with a fully specified name; + provide the argument --region on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--type` | one of: DATABASE, SCHEMA, TABLE |  | The type of the object to lookup. If not provided, the default is DATABASE. TYPE must be one of: DATABASE, SCHEMA, TABLE. |


**Examples:**
```bash
To lookup an existing migration job object:

    $ gcloud database-migration objects lookup --migration-job=my-job \
      --location=us-central1 --database=my-database
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/objects/lookup)

---
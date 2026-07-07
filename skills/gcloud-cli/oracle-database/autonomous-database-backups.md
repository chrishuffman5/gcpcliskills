# gcloud oracle-database autonomous-database-backups

manage Autonomous Database Backup resources

### `gcloud oracle-database autonomous-database-backups list`

List autonomous database backups

Lists all AutonomousDatabaseBackups for the specified AutonomousDatabase.

**Synopsis:**
```
gcloud oracle-database autonomous-database-backups list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all backups for an AutonomousDatabase with id my-instance in the
location us-east4, run:

    $ gcloud oracle-database autonomous-database-backups list \
      --location=us-east4 \
      --filter='autonomous_database_id="my-instance"'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/autonomous-database-backups/list)

---
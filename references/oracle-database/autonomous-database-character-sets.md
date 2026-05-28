# gcloud oracle-database autonomous-database-character-sets

manage Autonomous Database Character Set resources

### `gcloud oracle-database autonomous-database-character-sets list`

List all AutonomousDatabaseCharacterSets

List all AutonomousDatabaseCharacterSets.

**Synopsis:**
```
gcloud oracle-database autonomous-database-character-sets list
    --location=LOCATION [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all AutonomousDatabaseCharacterSets in the location us-east4, run:

    $ gcloud oracle-database autonomous-database-character-sets list \
        --location=us-east4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/autonomous-database-character-sets/list)

---
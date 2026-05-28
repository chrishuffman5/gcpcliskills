# gcloud oracle-database database-character-sets

manage Database Character Set resources

### `gcloud oracle-database database-character-sets list`

List all DatabaseCharacterSets

List all DatabaseCharacterSets.

**Synopsis:**
```
gcloud oracle-database database-character-sets list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all DatabaseCharacterSets in the location us-east4 for character
set character-set, run:

    $ gcloud oracle-database database-character-sets list \
        --location=us-east4 --filter="character_set_type=character-set"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/database-character-sets/list)

---
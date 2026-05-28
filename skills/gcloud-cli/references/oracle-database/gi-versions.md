# gcloud oracle-database gi-versions

manage Gi Version resources

### `gcloud oracle-database gi-versions list`

List all GiVersions

List all GiVersions.

**Synopsis:**
```
gcloud oracle-database gi-versions list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all GiVersions in the location us-east4, run:

    $ gcloud oracle-database gi-versions list --location=us-east4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/gi-versions/list)

---

## `gcloud oracle-database gi-versions minor-versions` — manage Minor Version resources
### `gcloud oracle-database gi-versions minor-versions list`

List minorVersions

**Synopsis:**
```
gcloud oracle-database gi-versions minor-versions list
    (--gi-version=GI_VERSION : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--gi-version` | GI_VERSION |  | _[This must be specified.]_ ID of the giVersion or fully qualified identifier for the giVersion. To set the gi-version attribute: + provide the argument --gi-version on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The location id of the giVersion resource. To set the location attribute: + provide the argument --gi-version on the command line with a fully specified name; + provide the argument --location on the command line. |


**Examples:**
```bash
To list all minorVersions, run:

    $ gcloud oracle-database gi-versions minor-versions list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/gi-versions/minor-versions/list)

---
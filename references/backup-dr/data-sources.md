# gcloud backup-dr data-sources

view Backup and DR data sources

### `gcloud backup-dr data-sources describe`

Show details of the data source

Show all configuration data associated with the specified data source.

**Synopsis:**
```
gcloud backup-dr data-sources describe
    (DATA_SOURCE : --backup-vault=BACKUP_VAULT --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Data source resource - Name of the data source to describe. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument data_source on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATA_SOURCE
     ID of the data_source or fully qualified identifier for the
     data_source.

     To set the data_source attribute:
     + provide the argument data_source on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --backup-vault=BACKUP_VAULT
     The ID of the Backup Vault.

     To set the backup-vault attribute:
     + provide the argument data_source on the command line with a fully
       specified name;
     + provide the argument --backup-vault on the command line.

  --location=LOCATION
     Location ID of the resource.

     To set the location attribute:
     + provide the argument data_source on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To view details for data source 'DATA_SOURCE', run:

    $ gcloud backup-dr data-sources describe DATA_SOURCE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/data-sources/describe)

---
### `gcloud backup-dr data-sources list`

List Data Sources

Displays all data sources in a project.

**Synopsis:**
```
gcloud backup-dr data-sources list
    [--backup-vault=BACKUP_VAULT --location=LOCATION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--backup-vault` | BACKUP_VAULT |  | _[* set the property core/project.]_ ID of the backup_vault or fully qualified identifier for the backup_vault. To set the backup-vault attribute: + provide the argument --backup-vault on the command line; + default is all backup vaults . |
| `--location` | LOCATION |  | _[* set the property core/project.]_ Location ID of the resource. To set the location attribute: + provide the argument --backup-vault on the command line with a fully specified name; + default is all backup vaults with a fully specified name; + provide the argument --location on the command line; + default is all locations . |


**Examples:**
```bash
To list data sources for all backup vaults and locations, run:

    $ gcloud backup-dr data-sources list

To list all data sources for a backup vault my-vault in a location
my-location, run:

    $ gcloud backup-dr data-sources list --backup-vault=my-vault \
        --location=my-location
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/data-sources/list)

---
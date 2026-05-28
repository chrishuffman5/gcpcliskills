# gcloud sql flags

provide a command to list flags

### `gcloud sql flags list`

List customizable flags for Google Cloud SQL instances

List customizable flags for Google Cloud SQL instances.

**Synopsis:**
```
gcloud sql flags list
    [--database-version=DATABASE_VERSION; default="MYSQL_8_0"]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--database-version` | one of: MYSQL_5_6, MYSQL_5_7, MYSQL_8_0, MYSQL_8_4, POSTGRES_9_6, POSTGRES_10, POSTGRES_11, POSTGRES_12, POSTGRES_13, POSTGRES_14, POSTGRES_15, POSTGRES_16, POSTGRES_17, POSTGRES_18, SQLSERVER_2017_EXPRESS, SQLSERVER_2017_WEB, SQLSERVER_2017_STANDARD, SQLSERVER_2017_ENTERPRISE, SQLSERVER_2019_EXPRESS, SQLSERVER_2019_WEB, SQLSERVER_2019_STANDARD, SQLSERVER_2019_ENTERPRISE, SQLSERVER_2022_EXPRESS, SQLSERVER_2022_WEB, SQLSERVER_2022_STANDARD, SQLSERVER_2022_ENTERPRISE | MYSQL_8_0 | The database engine type and versions. If left unspecified, MYSQL_8_0 is used. See the list of database versions at https://cloud.google.com/sql/docs/mysql/admin-api/rest/v1beta4/SqlDatabaseVersion. Apart from listed major versions, DATABASE_VERSION also accepts supported minor versions. DATABASE_VERSION must be one of: MYSQL_5_6, MYSQL_5_7, MYSQL_8_0, MYSQL_8_4, POSTGRES_9_6, POSTGRES_10, POSTGRES_11, POSTGRES_12, POSTGRES_13, POSTGRES_14, POSTGRES_15, POSTGRES_16, POSTGRES_17, POSTGRES_18, SQLSERVER_2017_EXPRESS, SQLSERVER_2017_WEB, SQLSERVER_2017_STANDARD, SQLSERVER_2017_ENTERPRISE, SQLSERVER_2019_EXPRESS, SQLSERVER_2019_WEB, SQLSERVER_2019_STANDARD, SQLSERVER_2019_ENTERPRISE, SQLSERVER_2022_EXPRESS, SQLSERVER_2022_WEB, SQLSERVER_2022_STANDARD, SQLSERVER_2022_ENTERPRISE. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/flags/list)

---
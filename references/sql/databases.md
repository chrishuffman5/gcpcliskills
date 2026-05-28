# gcloud sql databases

provide commands for managing databases of Cloud SQL instances

### `gcloud sql databases create`

Creates a database for a Cloud SQL instance

Creates a database for a Cloud SQL instance.

**Synopsis:**
```
gcloud sql databases create DATABASE --instance=INSTANCE, -i INSTANCE
    [--async] [--charset=CHARSET] [--collation=COLLATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DATABASE
   Cloud SQL database name.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE, -i INSTANCE |  | Cloud SQL instance ID. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--charset` | CHARSET |  | Cloud SQL database charset setting, which specifies the set of symbols and encodings used to store the data in your database. Each database version may support a different set of charsets. |
| `--collation` | COLLATION |  | Cloud SQL database collation setting, which specifies the set of rules for comparing characters in a character set. Each database version may support a different set of collations. For PostgreSQL database versions, this may only be set to the collation of the template database. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/databases/create)

---
### `gcloud sql databases delete`

Deletes a Cloud SQL database

For MySQL, also deletes all files in the database directory.

**Synopsis:**
```
gcloud sql databases delete DATABASE --instance=INSTANCE, -i INSTANCE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DATABASE
   Cloud SQL database name.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE, -i INSTANCE |  | Cloud SQL instance ID. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/databases/delete)

---
### `gcloud sql databases describe`

Displays configuration and metadata about a Cloud SQL database

Information such as database name, charset, and collation will be
displayed.

**Synopsis:**
```
gcloud sql databases describe DATABASE --instance=INSTANCE, -i INSTANCE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DATABASE
   Cloud SQL database name.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE, -i INSTANCE |  | Cloud SQL instance ID. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/databases/describe)

---
### `gcloud sql databases list`

Lists databases for a Cloud SQL instance

Lists databases for a Cloud SQL instance.

**Synopsis:**
```
gcloud sql databases list --instance=INSTANCE, -i INSTANCE
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE, -i INSTANCE |  | Cloud SQL instance ID. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/databases/list)

---
### `gcloud sql databases patch`

Patches the settings of a Cloud SQL database

Patches the settings of a Cloud SQL database.

**Synopsis:**
```
gcloud sql databases patch DATABASE --instance=INSTANCE, -i INSTANCE
    [--charset=CHARSET] [--collation=COLLATION] [--diff]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DATABASE
   Cloud SQL database name.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE, -i INSTANCE |  | Cloud SQL instance ID. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--charset` | CHARSET |  | Cloud SQL database charset setting, which specifies the set of symbols and encodings used to store the data in your database. Each database version may support a different set of charsets. |
| `--collation` | COLLATION |  | Cloud SQL database collation setting, which specifies the set of rules for comparing characters in a character set. Each database version may support a different set of collations. This flag can't be used with PostgreSQL instances. |
| `--diff` |  |  | Show what changed as a result of the patch. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/databases/patch)

---
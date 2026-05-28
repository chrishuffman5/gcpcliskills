# gcloud datastore indexes

manage your Cloud Datastore indexes

### `gcloud datastore indexes cleanup`

Remove unused datastore indexes based on your local index configuration

This command removes unused datastore indexes based on your local index
configuration. Any indexes that exist that are not in the index file will
be removed.

**Synopsis:**
```
gcloud datastore indexes cleanup INDEX_FILE [--database=DATABASE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INDEX_FILE
   The path to your index.yaml file. For a detailed look into defining
   your index.yaml file, refer to this configuration guide:
   https://cloud.google.com/datastore/docs/tools/indexconfig#Datastore_About_index_yaml
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--database` | DATABASE |  | The database to operate on. If not specified, the CLI refers the (default) database by default. For example, to operate on database testdb: $ gcloud datastore indexes cleanup --database='testdb' |


**Examples:**
```bash
To remove unused indexes based on your local configuration, run:

    $ gcloud datastore indexes cleanup ~/myapp/index.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastore/indexes/cleanup)

---
### `gcloud datastore indexes create`

Create new datastore indexes based on your local index configuration

Create new datastore indexes based on your local index configuration. Any
indexes in your index file that do not exist will be created.

**Synopsis:**
```
gcloud datastore indexes create INDEX_FILE [--database=DATABASE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INDEX_FILE
   The path to your index.yaml file. For a detailed look into defining
   your index.yaml file, refer to this configuration guide:
   https://cloud.google.com/datastore/docs/tools/indexconfig#Datastore_About_index_yaml
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--database` | DATABASE |  | The database to operate on. If not specified, the CLI refers the (default) database by default. For example, to operate on database testdb: $ gcloud datastore indexes create --database='testdb' |


**Examples:**
```bash
To create new indexes based on your local configuration, run:

    $ gcloud datastore indexes create ~/myapp/index.yaml

Detailed information about index configuration can be found at the
index.yaml reference
(https://cloud.google.com/datastore/docs/tools/indexconfig).
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastore/indexes/create)

---
### `gcloud datastore indexes describe`

Show details about an Cloud Datastore index

Show details about an Cloud Datastore index.

**Synopsis:**
```
gcloud datastore indexes describe INDEX [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Index resource - The index you want to get the details of. This represents
a Cloud resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument index on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INDEX
     ID of the index or fully qualified identifier for the index.

     To set the index attribute:
     + provide the argument index on the command line.
```

**Examples:**
```bash
To describe the index with id exampleIndexId, run:

    $ gcloud datastore indexes describe exampleIndexId
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastore/indexes/describe)

---
### `gcloud datastore indexes list`

List Cloud Datastore indexes

List Cloud Datastore indexes.

**Synopsis:**
```
gcloud datastore indexes list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all composite indexes in the database, run:

    $ gcloud datastore indexes list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastore/indexes/list)

---
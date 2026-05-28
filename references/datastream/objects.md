# gcloud datastream objects

manage Datastream stream objects

### `gcloud datastream objects describe`

Show details about a Stream object

Show details about a Stream object.

**Synopsis:**
```
gcloud datastream objects describe
    (OBJECT : --location=LOCATION --stream=STREAM) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Stream object resource - The Stream object you want to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument object on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OBJECT
     ID of the stream_object or fully qualified identifier for the
     stream_object.

     To set the object attribute:
     + provide the argument object on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the resources.

     To set the location attribute:
     + provide the argument object on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --stream=STREAM
     The stream name.

     To set the stream attribute:
     + provide the argument object on the command line with a fully
       specified name;
     + provide the argument --stream on the command line.
```

**Examples:**
```bash
To show details about a stream object, run:

    $ gcloud datastream objects describe my-object --stream=my-stream \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastream/objects/describe)

---
### `gcloud datastream objects list`

List a Datastream stream objects

List stream objects.

**Synopsis:**
```
gcloud datastream objects list (--stream=STREAM : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--stream` | STREAM |  | _[This must be specified.]_ ID of the stream or fully qualified identifier for the stream. To set the stream attribute: + provide the argument --stream on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The Cloud location for the stream. To set the location attribute: + provide the argument --stream on the command line with a fully specified name; + provide the argument --location on the command line. |


**Examples:**
```bash
To list all objects in a stream and location 'us-central1', run:

    $ gcloud datastream objects list --stream=my-stream \
      --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastream/objects/list)

---
### `gcloud datastream objects lookup`

Lookup a Datastream stream object

Lookup a stream object by its source object identifier (e.g. schema.table)

**Synopsis:**
```
gcloud datastream objects lookup
    (--salesforce-object-name=SALESFORCE_OBJECT_NAME
      | --mysql-database=MYSQL_DATABASE --mysql-table=MYSQL_TABLE
      | --oracle-schema=ORACLE_SCHEMA --oracle-table=ORACLE_TABLE
      | --postgresql-schema=POSTGRESQL_SCHEMA
      --postgresql-table=POSTGRESQL_TABLE
      | --sqlserver-schema=SQLSERVER_SCHEMA
      --sqlserver-table=SQLSERVER_TABLE)
    (--stream=STREAM : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--salesforce-object-name` | SALESFORCE_OBJECT_NAME |  | _[Exactly one of these must be specified:]_ Salesforce object name. |
| `--mysql-database` | MYSQL_DATABASE |  | _[Exactly one of these must be specified:]_ Mysql database for the object. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--mysql-table` | MYSQL_TABLE |  | _[Exactly one of these must be specified:]_ Mysql table for the object. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--oracle-schema` | ORACLE_SCHEMA |  | _[Exactly one of these must be specified:]_ Oracle schema for the object. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--oracle-table` | ORACLE_TABLE |  | _[Exactly one of these must be specified:]_ Oracle table for the object. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--postgresql-schema` | POSTGRESQL_SCHEMA |  | _[Exactly one of these must be specified:]_ PostgreSQL schema for the object. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--postgresql-table` | POSTGRESQL_TABLE |  | _[Exactly one of these must be specified:]_ PostgreSQL table for the object. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--sqlserver-schema` | SQLSERVER_SCHEMA |  | _[Exactly one of these must be specified:]_ SQL Server schema for the object. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--sqlserver-table` | SQLSERVER_TABLE |  | _[Exactly one of these must be specified:]_ SQL Server table for the object. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--stream` | STREAM |  | _[This must be specified.]_ ID of the stream or fully qualified identifier for the stream. To set the stream attribute: + provide the argument --stream on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The Cloud location for the stream. To set the location attribute: + provide the argument --stream on the command line with a fully specified name; + provide the argument --location on the command line. |


**Examples:**
```bash
To lookup an existing Mysql stream object:

    $ gcloud datastream objects lookup --stream=my-stream \
      --location=us-central1 --mysql-database=my-db \
      --mysql-table=my-table

To lookup an existing Oracle stream object:

    $ gcloud datastream objects lookup --stream=my-stream \
      --location=us-central1 --oracle-schema=my-schema \
      --oracle-table=my-table

To lookup an existing PostgreSQL stream object:

    $ gcloud datastream objects lookup --stream=my-stream \
      --location=us-central1 --postgresql-schema=my-schema \
      --postgresql-table=my-table

To lookup an existing SQL Server stream object:

    $ gcloud datastream objects lookup --stream=my-stream \
       --location=us-central1 --sqlserver-schema=my-schema \
       --sqlserver-table=my-table

To lookup an existing Salesforce stream object:

    $ gcloud datastream objects lookup --stream=my-stream \
       --location=us-central1 --salesforce-object-name=my-object
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastream/objects/lookup)

---
### `gcloud datastream objects start-backfill`

Start a backfill job for a Stream object

Start a backfill job for a Stream object.

**Synopsis:**
```
gcloud datastream objects start-backfill
    (OBJECT : --location=LOCATION --stream=STREAM) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Stream object resource - The Stream object you want to start backfill for.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument object on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OBJECT
     ID of the stream_object or fully qualified identifier for the
     stream_object.

     To set the object attribute:
     + provide the argument object on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the resources.

     To set the location attribute:
     + provide the argument object on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --stream=STREAM
     The stream name.

     To set the stream attribute:
     + provide the argument object on the command line with a fully
       specified name;
     + provide the argument --stream on the command line.
```

**Examples:**
```bash
To start a stream object backfill job, run:

    $ gcloud datastream objects start-backfill my-object \
        --stream=my-stream --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastream/objects/start-backfill)

---
### `gcloud datastream objects stop-backfill`

Stop a backfill job for a Stream object

Stop a backfill job for a Stream object.

**Synopsis:**
```
gcloud datastream objects stop-backfill
    (OBJECT : --location=LOCATION --stream=STREAM) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Stream object resource - The Stream object you want to stop backfill for.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument object on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OBJECT
     ID of the stream_object or fully qualified identifier for the
     stream_object.

     To set the object attribute:
     + provide the argument object on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the resources.

     To set the location attribute:
     + provide the argument object on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --stream=STREAM
     The stream name.

     To set the stream attribute:
     + provide the argument object on the command line with a fully
       specified name;
     + provide the argument --stream on the command line.
```

**Examples:**
```bash
To stop a stream object backfill job, run:

    $ gcloud datastream objects stop-backfill my-object \
        --stream=my-stream --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastream/objects/stop-backfill)

---
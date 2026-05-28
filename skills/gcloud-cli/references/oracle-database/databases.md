# gcloud oracle-database databases

manage Database resources

### `gcloud oracle-database databases describe`

Get details of a Database

Get details of a Database.

**Synopsis:**
```
gcloud oracle-database databases describe (DATABASE : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Database resource - The name of the Database resource in the following
format: projects/{project}/locations/{region}/databases/{database} The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument database on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATABASE
     ID of the database or fully qualified identifier for the database.

     To set the database attribute:
     + provide the argument database on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the database resource.

     To set the location attribute:
     + provide the argument database on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To get a Database with id my-database in the location us-east4 for a given
DbSystem with id my-db-system, run:

    $ gcloud oracle-database databases describe my-database \
        --location=us-east4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/databases/describe)

---
### `gcloud oracle-database databases list`

List all Databases

List all Databases.

**Synopsis:**
```
gcloud oracle-database databases list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all Databases in the location us-east4 for a given DbSystem with id
my-db-system, run:

    $ gcloud oracle-database databases list --location=us-east4 \
        --filter="dbSystem=projects/project-id/locations/us-east4/dbSyst\
    ems/my-db-system"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/databases/list)

---
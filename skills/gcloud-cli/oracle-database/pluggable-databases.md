# gcloud oracle-database pluggable-databases

manage Pluggable Database resources

### `gcloud oracle-database pluggable-databases describe`

Get details of a PluggableDatabase

Get details of a PluggableDatabase.

**Synopsis:**
```
gcloud oracle-database pluggable-databases describe
    (PLUGGABLE_DATABASE : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PluggableDatabase resource - The name of the PluggableDatabase resource in
the following format:
projects/{project}/locations/{region}/pluggableDatabases/{pluggable_database}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument pluggable_database on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PLUGGABLE_DATABASE
     ID of the pluggableDatabase or fully qualified identifier for the
     pluggableDatabase.

     To set the pluggable_database attribute:
     + provide the argument pluggable_database on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the pluggableDatabase resource.

     To set the location attribute:
     + provide the argument pluggable_database on the command line with
       a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To get a PluggableDatabase with id my-pluggable-database in the location
us-east4 for a given DbSystem with id my-db-system, run:

    $ gcloud oracle-database pluggable-databases describe \
        my-pluggable-database --location=us-east4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/pluggable-databases/describe)

---
### `gcloud oracle-database pluggable-databases list`

List pluggableDatabases

**Synopsis:**
```
gcloud oracle-database pluggable-databases list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all pluggableDatabases, run:

    $ gcloud oracle-database pluggable-databases list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/pluggable-databases/list)

---
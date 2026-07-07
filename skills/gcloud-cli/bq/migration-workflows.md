# gcloud bq migration-workflows

manage Migration Workflow resources

### `gcloud bq migration-workflows create`

Create migration workflows

Create a migration workflow

**Synopsis:**
```
gcloud bq migration-workflows create --config-file=CONFIG_FILE
    --location=LOCATION [--async] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--config-file` | CONFIG_FILE |  | Path to the migration workflows config file. |
| `--location` | LOCATION |  | Location of the migration workflow. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To create a migration workflow in EU synchronously based on a config file,
run:

    $ gcloud bq migration-workflows create --location=EU \
        --config-file=config_file.yaml --no-async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bq/migration-workflows/create)

---
### `gcloud bq migration-workflows delete`

Delete migration workflows

Delete a migration workflow

**Synopsis:**
```
gcloud bq migration-workflows delete (WORKFLOW : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workflow resource - The unique identifier for the migration workflow.
Example: projects/123/locations/us/workflows/1234 The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument workflow on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  WORKFLOW
     ID of the workflow or fully qualified identifier for the workflow.

     To set the workflow attribute:
     + provide the argument workflow on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the workflow resource.

     To set the location attribute:
     + provide the argument workflow on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To delete a migration workflow projects/123/locations/eu/workflows/1234,
run:

    $ gcloud bq migration-workflows delete \
        projects/123/locations/eu/workflows/1234
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bq/migration-workflows/delete)

---
### `gcloud bq migration-workflows describe`

Describe migration workflows

Describe a migration workflow

**Synopsis:**
```
gcloud bq migration-workflows describe (WORKFLOW : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workflow resource - The unique identifier for the migration workflow.
Example: projects/123/locations/us/workflows/1234 The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument workflow on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  WORKFLOW
     ID of the workflow or fully qualified identifier for the workflow.

     To set the workflow attribute:
     + provide the argument workflow on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the workflow resource.

     To set the location attribute:
     + provide the argument workflow on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe a migration workflow projects/123/locations/eu/workflows/1234,
run:

    $ gcloud bq migration-workflows describe \
        projects/123/locations/eu/workflows/1234
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bq/migration-workflows/describe)

---
### `gcloud bq migration-workflows list`

List migration workflows

**Synopsis:**
```
gcloud bq migration-workflows list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all migration workflows in location EU, run:

    $ gcloud bq migration-workflows list --location=eu
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bq/migration-workflows/list)

---
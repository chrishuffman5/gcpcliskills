# gcloud monitoring dashboards

manage Cloud Monitoring dashboards

### `gcloud monitoring dashboards create`

Create a new Cloud Monitoring dashboard

Create a new Monitoring dashboard. A dashboard can be specified as a
JSON/YAML value passed in as a string through the --config flag or as a
file through the --config-from-file flag. Validate a dashboard config
without saving by setting the --validate-only flag.

For information about the format of a dashboard:
https://cloud.google.com/monitoring/api/ref_v3/rest/v1/projects.dashboards

**Synopsis:**
```
gcloud monitoring dashboards create
    (--config=CONFIG | --config-from-file=PATH_TO_FILE) [--validate-only]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--config` | CONFIG |  | _[Exactly one of these must be specified:]_ Dashboard configuration, in either JSON or YAML format, as a string. |
| `--config-from-file` | PATH_TO_FILE |  | _[Exactly one of these must be specified:]_ Path to a JSON or YAML file containing the dashboard configuration. Use a full or relative path to a local file containing the value of config. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--validate-only` |  |  | When set, validate the dashboard but do not save it. |


**Examples:**
```bash
To create a dashboard with a YAML config, run:

    $ gcloud monitoring dashboards create --config='''
      displayName: New Dashboard
      gridLayout:
        widgets:
        - text:
            content: Hello World
      '''

To validate a dashboard and not save it, run:

    $ gcloud monitoring dashboards create --validate-only --config='''
      displayName: New Dashboard
      gridLayout:
        widgets:
        - text:
            content: Hello World
      '''

To create a dashboard with a JSON config, run:

    $ gcloud monitoring dashboards create --config='''
      {
        "displayName": "New Dashboard",
        "gridLayout": {
          "widgets": [
            {
              "text": {
                "content": "Hello World",
              }
            }
          ]
        },
      }
      '''

To create a dashboard with a specific dashboard ID, run:

    $ gcloud monitoring dashboards create --config='''
      name: projects/MY-PROJECT/dashboards/MY-DASHBOARD
      displayName: New Dashboard
      gridLayout:
        widgets:
        - text:
            content: Hello World
      '''

To create a dashboard within a specific project, run:

    $ gcloud monitoring dashboards create --project=MY-PROJECT \
        --config='''
      displayName: New Dashboard
      gridLayout:
        widgets:
        - text:
            content: Hello World
      '''

To create a dashboard with a file, run:

    $ gcloud monitoring dashboards create --config-from-file=MY-FILE

Sample contents of MY-FILE:

    displayName: New Dashboard
    gridLayout:
      widgets:
      - text:
          content: Hello World
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/monitoring/dashboards/create)

---
### `gcloud monitoring dashboards delete`

Delete a Cloud Monitoring dashboard

Delete a Monitoring dashboard.

**Synopsis:**
```
gcloud monitoring dashboards delete DASHBOARD [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Dashboard resource - The dashboard to delete. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument dashboard on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DASHBOARD
     ID of the dashboard or fully qualified identifier for the dashboard.

     To set the dashboard attribute:
     + provide the argument dashboard on the command line.
```

**Examples:**
```bash
To delete a dashboard, run:

    $ gcloud monitoring dashboards delete MY-DASHBOARD

To delete a dashboard contained within a specific project, run:

    $ gcloud monitoring dashboards delete MY-DASHBOARD \
        --project=MY-PROJECT

To delete a dashboard with a fully qualified dashboard ID, run:

    $ gcloud monitoring dashboards delete \
        projects/MY-PROJECT/dashboards/MY-DASHBOARD
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/monitoring/dashboards/delete)

---
### `gcloud monitoring dashboards describe`

Describe a Cloud Monitoring dashboard

Describe a Monitoring dashboard.

**Synopsis:**
```
gcloud monitoring dashboards describe DASHBOARD [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Dashboard resource - The dashboard to describe. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument dashboard on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DASHBOARD
     ID of the dashboard or fully qualified identifier for the dashboard.

     To set the dashboard attribute:
     + provide the argument dashboard on the command line.
```

**Examples:**
```bash
To describe a dashboard, run:

    $ gcloud monitoring dashboards describe MY-DASHBOARD

To describe a dashboard in JSON, run:

    $ gcloud monitoring dashboards describe MY-DASHBOARD --format=json

To describe a dashboard contained within a specific project, run:

    $ gcloud monitoring dashboards describe MY-DASHBOARD \
        --project=MY-PROJECT

To describe a dashboard with a fully qualified dashboard ID, run:

    $ gcloud monitoring dashboards describe \
        projects/MY-PROJECT/dashboards/MY-DASHBOARD
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/monitoring/dashboards/describe)

---
### `gcloud monitoring dashboards list`

List Cloud Monitoring dashboards

List Monitoring dashboards.

**Synopsis:**
```
gcloud monitoring dashboards list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list dashboards, run:

    $ gcloud monitoring dashboards list

To list dashboards for a specific project, run:

    $ gcloud monitoring dashboards list --project=MY-PROJECT
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/monitoring/dashboards/list)

---
### `gcloud monitoring dashboards update`

Update a Cloud Monitoring dashboard

Update a Monitoring dashboard. The updated dashboard can be specified as a
JSON/YAML value passed in as a string through the --config flag or as a
file through the --config-from-file flag.

Note: Etags are used to prevent concurrent updates to the same dashboard.
The latest etag can be found in a describe or list response.

For information about the format of a dashboard:
https://cloud.google.com/monitoring/api/ref_v3/rest/v1/projects.dashboards

**Synopsis:**
```
gcloud monitoring dashboards update DASHBOARD
    (--config=CONFIG | --config-from-file=PATH_TO_FILE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Dashboard resource - The dashboard to update. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument dashboard on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DASHBOARD
     ID of the dashboard or fully qualified identifier for the dashboard.

     To set the dashboard attribute:
     + provide the argument dashboard on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--config` | CONFIG |  | _[Exactly one of these must be specified:]_ Dashboard configuration, in either JSON or YAML format, as a string. |
| `--config-from-file` | PATH_TO_FILE |  | _[Exactly one of these must be specified:]_ Path to a JSON or YAML file containing the dashboard configuration. Use a full or relative path to a local file containing the value of config. |


**Examples:**
```bash
To update a dashboard with a YAML config, run:

    $ gcloud monitoring dashboards update MY-DASHBOARD --config='''
      displayName: New Dashboard with New Display Name
      etag: 40d1040034db4e5a9dee931ec1b12c0d
      gridLayout:
        widgets:
        - text:
            content: Hello World
      '''

To update a dashboard with a JSON config, run:

    $ gcloud monitoring dashboards update MY-DASHBOARD --config='''
      {
        "displayName": "New Dashboard with New Display Name",
        "etag": "40d1040034db4e5a9dee931ec1b12c0d",
        "gridLayout": {
          "widgets": [
            {
              "text": {
                "content": "Hello World",
              }
            }
          ]
        },
      }
      '''

To update a dashboard within a specific project, run:

    $ gcloud monitoring dashboards update MY-DASHBOARD \
        --project=MY-PROJECT --config='''
      displayName: New Dashboard with New Display Name
      etag: 40d1040034db4e5a9dee931ec1b12c0d
      gridLayout:
        widgets:
        - text:
            content: Hello World
      '''

To update a dashboard with a file, run:

    $ gcloud monitoring dashboards update MY-DASHBOARD \
        --config-from-file=MY-FILE

Sample contents of MY-FILE:

    displayName: New Dashboard with new Display Name
    etag: 40d1040034db4e5a9dee931ec1b12c0d
    gridLayout:
      widgets:
      - text:
          content: Hello World
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/monitoring/dashboards/update)

---
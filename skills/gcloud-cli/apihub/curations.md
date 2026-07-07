# gcloud apihub curations

manage Curation resources

### `gcloud apihub curations create`

Create a Curation

Create a curation.

Note: The positional argument for Curation ID is currently not supported. Please use the --curation flag to specify the Curation ID.

**Synopsis:**
```
gcloud apihub curations create ([CURATION] : --location=LOCATION)
    --display-name=DISPLAY_NAME
    ((--application-integration-endpoint-details-trigger-id=APPLICATION_INTEGRATION_ENDPOINT_DETAILS_TRIGGER_ID
      --application-integration-endpoint-details-uri=APPLICATION_INTEGRATION_ENDPOINT_DETAILS_URI))
    [--description=DESCRIPTION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Curation resource - Identifier. The name of the curation.

Format: projects/{project}/locations/{location}/curations/{curation}
The arguments in this group can be used to specify the attributes of
this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument curation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CURATION
     ID of the curation or fully qualified identifier for the curation.

     To set the curation attribute:
     + provide the argument curation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the curation resource.

     To set the location attribute:
     + provide the argument curation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--application-integration-endpoint-details-trigger-id` | APPLICATION_INTEGRATION_ENDPOINT_DETAILS_TRIGGER_ID |  | The API trigger ID of the Application Integration workflow. Specified together with --application-integration-endpoint-details-uri as a required group. |
| `--application-integration-endpoint-details-uri` | APPLICATION_INTEGRATION_ENDPOINT_DETAILS_URI |  | The endpoint URI should be a valid REST URI for triggering an Application Integration. Format: https://integrations.googleapis.com/v1/{name=projects/*/locations/*/integrations/*}:execute or https://{location}-integrations.googleapis.com/v1/{name=projects/*/locations/*/integrations/*}:execute |
| `--display-name` | DISPLAY_NAME |  | The display name of the curation. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | The description of the curation. |

**Examples:**
```bash
To create a curation with the ID my-curation, run:

    $ gcloud apihub curations create --curation=my-curation \
        --display-name="My Curation" --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/curations/create)

---
### `gcloud apihub curations delete`

Delete a Curation

Delete a curation.

**Synopsis:**
```
gcloud apihub curations delete ([CURATION] : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Curation resource - The name of the curation resource to delete.
Format: projects/{project}/locations/{location}/curations/{curation}
The arguments in this group can be used to specify the attributes of
this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument curation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CURATION
     ID of the curation or fully qualified identifier for the curation.

     To set the curation attribute:
     + provide the argument curation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the curation resource.

     To set the location attribute:
     + provide the argument curation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To delete a curation with the ID my-curation, run:

    $ gcloud apihub curations delete my-curation --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/curations/delete)

---
### `gcloud apihub curations describe`

Describe a Curation

Describe a curation.

**Synopsis:**
```
gcloud apihub curations describe ([CURATION] : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Curation resource - The name of the curation resource to retrieve.
Format: projects/{project}/locations/{location}/curations/{curation}
The arguments in this group can be used to specify the attributes of
this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument curation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CURATION
     ID of the curation or fully qualified identifier for the curation.

     To set the curation attribute:
     + provide the argument curation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the curation resource.

     To set the location attribute:
     + provide the argument curation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe a curation with the ID my-curation, run:

    $ gcloud apihub curations describe my-curation \
        --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/curations/describe)

---
### `gcloud apihub curations list`

List Curations

List curations.

**Synopsis:**
```
gcloud apihub curations list --location=LOCATION [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Location resource - The parent, which owns this collection of curation resources. Format: projects/{project}/locations/{location}. This represents a Cloud resource. (NOTE) Some attributes are not given arguments in this group but can be set in other ways. To set the project attribute: provide the argument --location on the command line with a fully specified name; provide the argument --project on the command line; set the property core/project. This must be specified. ID of the location or fully qualified identifier for the location. To set the location attribute: provide the argument --location on the command line. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--filter` | EXPRESSION |  | Apply a Boolean filter EXPRESSION to each resource item to be listed. If the expression evaluates True, then that item is listed. |
| `--limit` | LIMIT | unlimited | Maximum number of resources to list. The default is unlimited. |
| `--page-size` | PAGE_SIZE |  | Some services group resource list output into pages. This flag specifies the maximum number of resources per page. |
| `--sort-by` | [FIELD,...] |  | Comma-separated list of resource field key names to sort by. The default order is ascending. Prefix a field with "~" for descending order on that field. |
| `--uri` |  |  | Print a list of resource URIs instead of the default output, and change the command output to a list of URIs. |

**Examples:**
```bash
To list all curations in project my-project and location us-central1,
run:

    $ gcloud apihub curations list --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/curations/list)

---
### `gcloud apihub curations update`

Update a Curation

Update a curation.

**Synopsis:**
```
gcloud apihub curations update ([CURATION] : --location=LOCATION)
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [--clear-endpoint
      --application-integration-endpoint-details-trigger-id=APPLICATION_INTEGRATION_ENDPOINT_DETAILS_TRIGGER_ID
      --application-integration-endpoint-details-uri=APPLICATION_INTEGRATION_ENDPOINT_DETAILS_URI]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Curation resource - Identifier. The name of the curation.

Format: projects/{project}/locations/{location}/curations/{curation}
The arguments in this group can be used to specify the attributes of
this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument curation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CURATION
     ID of the curation or fully qualified identifier for the curation.

     To set the curation attribute:
     + provide the argument curation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the curation resource.

     To set the location attribute:
     + provide the argument curation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--application-integration-endpoint-details-trigger-id` | APPLICATION_INTEGRATION_ENDPOINT_DETAILS_TRIGGER_ID |  | The API trigger ID of the Application Integration workflow. |
| `--application-integration-endpoint-details-uri` | APPLICATION_INTEGRATION_ENDPOINT_DETAILS_URI |  | The endpoint URI should be a valid REST URI for triggering an Application Integration. Format: https://integrations.googleapis.com/v1/{name=projects/*/locations/*/integrations/*}:execute or https://{location}-integrations.googleapis.com/v1/{name=projects/*/locations/*/integrations/*}:execute |
| `--clear-endpoint` |  |  | Set googleCloudApihubV1Curation.endpoint back to default value. |
| `--description` | DESCRIPTION |  | The description of the curation. |
| `--display-name` | DISPLAY_NAME |  | The display name of the curation. |

**Examples:**
```bash
To update a curation with the ID my-curation, run:

    $ gcloud apihub curations update my-curation \
        --display-name="New Curation Name" --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/curations/update)

---

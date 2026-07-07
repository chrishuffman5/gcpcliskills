# gcloud network-security url-lists

manage Network Security Url Lists

### `gcloud network-security url-lists delete`

Delete Url List

Delete the specified Url List.

**Synopsis:**
```
gcloud network-security url-lists delete (URL_LIST : --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Url list resource - Name of the Url List you want to delete. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument url_list on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  URL_LIST
     ID of the url list or fully qualified identifier for the url list.

     To set the url_list attribute:
     + provide the argument url_list on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument url_list on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a Url List called 'my-url-list', run:

    $ gcloud network-security url-lists delete my-url-list \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/url-lists/delete)

---
### `gcloud network-security url-lists export`

Export Url List

Export a Url List.

**Synopsis:**
```
gcloud network-security url-lists export (URL_LIST : --location=LOCATION)
    [--destination=DESTINATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Url list resource - Name of the Url List to export. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument url_list on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  URL_LIST
     ID of the url list or fully qualified identifier for the url list.

     To set the url_list attribute:
     + provide the argument url_list on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument url_list on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | Path to a YAML file where the configuration will be exported. The exported data will not contain any output-only fields. Alternatively, you may omit this flag to write to standard output. For a schema describing the export/import format, see $CLOUDSDKROOT/lib/googlecloudsdk/schemas/... |


**Examples:**
```bash
To export a Url List, run:

    $ gcloud network-security url-lists export my-url-list \
        --destination=my-url-list.yaml --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/url-lists/export)

---
### `gcloud network-security url-lists import`

Import Url List

Import a Url List.

**Synopsis:**
```
gcloud network-security url-lists import (URL_LIST : --location=LOCATION)
    [--async] [--source=SOURCE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Url list resource - Name of the Url List to import. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument url_list on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  URL_LIST
     ID of the url list or fully qualified identifier for the url list.

     To set the url_list attribute:
     + provide the argument url_list on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument url_list on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--source` | SOURCE |  | Path to a YAML file containing the configuration export data. The YAML file must not contain any output-only fields. Alternatively, you may omit this flag to read from standard input. For a schema describing the export/import format, see: $CLOUDSDKROOT/lib/googlecloudsdk/schemas/... $CLOUDSDKROOT is can be obtained with the following command: $ gcloud info --format='value(installation.sdk_root)' |


**Examples:**
```bash
To import a Url List from a YAML file, run:

    $ gcloud network-security url-lists import my-url-list \
        --source=my-url-list.yaml --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/url-lists/import)

---
### `gcloud network-security url-lists list`

List Url Lists

List all Url Lists in the specified location of the current project.

**Synopsis:**
```
gcloud network-security url-lists list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list Url Lists in the current project, run:

    $ gcloud network-security url-lists list --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/url-lists/list)

---
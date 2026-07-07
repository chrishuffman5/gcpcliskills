# gcloud transcoder templates

manage Cloud Transcoder job templates

### `gcloud transcoder templates create`

Create Transcoder job templates

Create Transcoder job templates.

**Synopsis:**
```
gcloud transcoder templates create (TEMPLATE_ID : --location=LOCATION)
    (--file=FILE | --json=JSON) [--labels=[KEY=VALUE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
JobTemplate resource - Transcoder job template id The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument template_id on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TEMPLATE_ID
     ID of the jobTemplate or fully qualified identifier for the
     jobTemplate.

     To set the template_id attribute:
     + provide the argument template_id on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Transcoder location for resources

     To set the location attribute:
     + provide the argument template_id on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property transcoder/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--file` | FILE |  | _[Exactly one of these must be specified:]_ Path to job template. |
| `--json` | JSON |  | _[Exactly one of these must be specified:]_ Job template in json format. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To create a job template with json format configuration:

    $ gcloud transcoder templates create TEMPLATE_ID \
        --json="config: json-format" --location=us-central1

To create a job template with json format configuration file:

    $ gcloud transcoder templates create TEMPLATE_ID \
        --file="config.json" --location=us-central1

To create a job template with json format configuration and labels

    $ gcloud transcoder templates create TEMPLATE_ID \
        --file="config.json" --location=us-central1 --labels=key=value
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/transcoder/templates/create)

---
### `gcloud transcoder templates delete`

Delete transcoder job templates

Delete transcoder job templates.

**Synopsis:**
```
gcloud transcoder templates delete (TEMPLATE_ID : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
JobTemplate resource - Transcoder job template id The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument template_id on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TEMPLATE_ID
     ID of the jobTemplate or fully qualified identifier for the
     jobTemplate.

     To set the template_id attribute:
     + provide the argument template_id on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Transcoder location for resources

     To set the location attribute:
     + provide the argument template_id on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property transcoder/location.
```

**Examples:**
```bash
To delete a transcoder job template:

    $ gcloud transcoder templates delete TEMPLATE_ID \
      --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/transcoder/templates/delete)

---
### `gcloud transcoder templates describe`

Describe transcoder job templates

Describe transcoder job templates.

**Synopsis:**
```
gcloud transcoder templates describe (TEMPLATE_ID : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
JobTemplate resource - Transcoder job template id The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument template_id on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TEMPLATE_ID
     ID of the jobTemplate or fully qualified identifier for the
     jobTemplate.

     To set the template_id attribute:
     + provide the argument template_id on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Transcoder location for resources

     To set the location attribute:
     + provide the argument template_id on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property transcoder/location.
```

**Examples:**
```bash
To describe a transcoder job template:

    $ gcloud transcoder templates describe TEMPLATE_ID \
      --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/transcoder/templates/describe)

---
### `gcloud transcoder templates list`

List transcoder job templates

List transcoder job templates.

**Synopsis:**
```
gcloud transcoder templates list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property transcoder/location. |


**Examples:**
```bash
To list transcoder job templates in us-central1:

    $ gcloud transcoder templates list --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/transcoder/templates/list)

---
# gcloud apphub service-projects

manage App Hub Service Projects

### `gcloud apphub service-projects add`

Add an Apphub service project

Add an Apphub service project.

**Synopsis:**
```
gcloud apphub service-projects add (SERVICE_PROJECT : --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ServiceProjectAttachment resource - The Service Project ID. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument service_project on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE_PROJECT
     ID of the ServiceProjectAttachment or fully qualified identifier for
     the ServiceProjectAttachment.

     To set the service_project attribute:
     + provide the argument service_project on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the ServiceProjectAttachment.

     To set the location attribute:
     + provide the argument service_project on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + Service project attachments only support global location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To add the service project my-service-project to the host project
my-host-project, run:

    $ gcloud apphub service-projects add my-service-project \
        --project=my-host-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apphub/service-projects/add)

---
### `gcloud apphub service-projects describe`

Describe an Apphub service project

Describe an Apphub service project.

**Synopsis:**
```
gcloud apphub service-projects describe
    (SERVICE_PROJECT : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ServiceProjectAttachment resource - The Service Project ID. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument service_project on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE_PROJECT
     ID of the ServiceProjectAttachment or fully qualified identifier for
     the ServiceProjectAttachment.

     To set the service_project attribute:
     + provide the argument service_project on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the ServiceProjectAttachment.

     To set the location attribute:
     + provide the argument service_project on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + Service project attachments only support global location.
```

**Examples:**
```bash
To describe the service project my-service-project attached to the host
project my-host-project, run:

    $ gcloud apphub service-projects describe my-service-project \
        --project=my-host-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apphub/service-projects/describe)

---
### `gcloud apphub service-projects detach`

Detach an Apphub service project

Detach an Apphub service project.

**Synopsis:**
```
gcloud apphub service-projects detach [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To detach the service project my-service-project, run:

    $ gcloud apphub service-projects detach --project=my-service-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apphub/service-projects/detach)

---
### `gcloud apphub service-projects list`

List Apphub service projects

List Apphub service projects.

**Synopsis:**
```
gcloud apphub service-projects list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + Service project attachments only support global location. |


**Examples:**
```bash
To list all service projects attached to the host project my-host-project,
run:

    $ gcloud apphub service-projects list --project=my-host-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apphub/service-projects/list)

---
### `gcloud apphub service-projects lookup`

Lookup an Apphub service project

Lookup an Apphub service project.

**Synopsis:**
```
gcloud apphub service-projects lookup [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To lookup the service project my-service-project, run:

    $ gcloud apphub service-projects lookup --project=my-service-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apphub/service-projects/lookup)

---
### `gcloud apphub service-projects remove`

Remove an Apphub service project

Remove an Apphub service project.

**Synopsis:**
```
gcloud apphub service-projects remove
    (SERVICE_PROJECT : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ServiceProjectAttachment resource - The Service Project ID. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument service_project on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE_PROJECT
     ID of the ServiceProjectAttachment or fully qualified identifier for
     the ServiceProjectAttachment.

     To set the service_project attribute:
     + provide the argument service_project on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the ServiceProjectAttachment.

     To set the location attribute:
     + provide the argument service_project on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + Service project attachments only support global location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To remove the service project my-service-project from the host project
my-host-project, run:

    $ gcloud apphub service-projects remove my-service-project \
        --project=my-host-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apphub/service-projects/remove)

---
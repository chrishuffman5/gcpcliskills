# gcloud apigee developers

manage Apigee developers

### `gcloud apigee developers describe`

Describe an Apigee developer

Describe an Apigee developer.

gcloud apigee developers describe retrieves the developer's details,
including the developer's name, email address, apps, and other information.

**Synopsis:**
```
gcloud apigee developers describe (DEVELOPER : --organization=ORGANIZATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Developer resource - Email address of the developer to be described. To
get a list of available developers, run gcloud apigee developers list. The
arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  DEVELOPER
     ID of the developer or fully qualified identifier for the developer.

     To set the developer attribute:
     + provide the argument DEVELOPER on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --organization=ORGANIZATION
     Apigee organization containing the developer. If unspecified, the
     Cloud Platform project's associated organization will be used.

     To set the organization attribute:
     + provide the argument DEVELOPER on the command line with a fully
       specified name;
     + provide the argument --organization on the command line;
     + set the property [project] or provide the argument [--project] on
       the command line, using a Cloud Platform project with an associated
       Apigee organization.
```

**Examples:**
```bash
To describe a developer for the active Cloud Platform project whose email
address is larry@example.com, run:

    $ gcloud apigee developers describe larry@example.com

To describe that developer in the Apigee organization my-org, formatted as
a JSON object, run:

    $ gcloud apigee developers describe larry@example.com \
      --organization=my-org --format=json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apigee/developers/describe)

---
### `gcloud apigee developers list`

List Apigee developers by email address

List Apigee developers by email address.

**Synopsis:**
```
gcloud apigee developers list [--organization=ORGANIZATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION |  | _[organization will be used. This represents a Cloud resource.]_ ID of the organization or fully qualified identifier for the organization. To set the organization attribute: + provide the argument --organization on the command line; + set the property [project] or provide the argument [--project] on the command line, using a Cloud Platform project with an associated Apigee organization. |


**Examples:**
```bash
To list all developers for the active Cloud Platform project, run:

    $ gcloud apigee developers list

To list all developers in an Apigee organization called my-org, formatted
as JSON objects, run:

    $ gcloud apigee developers list --organization=my-org --format=json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apigee/developers/list)

---
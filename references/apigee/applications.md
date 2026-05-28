# gcloud apigee applications

manage third-party applications which call Apigee API proxies

### `gcloud apigee applications describe`

Describe an Apigee application

Describe an Apigee application.

gcloud apigee applications describe retrieves the application's details,
including its developer, credentials, API products, and other information.

**Synopsis:**
```
gcloud apigee applications describe
    (APPLICATION : --organization=ORGANIZATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Application resource - Application to be described. To get a list of
available applications, run gcloud apigee applications list. The arguments
in this group can be used to specify the attributes of this resource.

This must be specified.

  APPLICATION
     ID of the application or fully qualified identifier for the
     application.

     To set the app attribute:
     + provide the argument APPLICATION on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --organization=ORGANIZATION
     Apigee organization containing the application. If unspecified, the
     Cloud Platform project's associated organization will be used.

     To set the organization attribute:
     + provide the argument APPLICATION on the command line with a fully
       specified name;
     + provide the argument --organization on the command line;
     + set the property [project] or provide the argument [--project] on
       the command line, using a Cloud Platform project with an associated
       Apigee organization.
```

**Examples:**
```bash
To describe an application for the active Cloud Platform project whose UUID
is 46d6151e-0000-4dfa-b9c7-c03b8b58bb2f, run:

    $ gcloud apigee applications describe \
      46d6151e-0000-4dfa-b9c7-c03b8b58bb2f

To describe that application in the Apigee organization my-org, formatted
as a JSON object, run:

    $ gcloud apigee applications describe \
      46d6151e-0000-4dfa-b9c7-c03b8b58bb2f --organization=my-org \
      --format=json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apigee/applications/describe)

---
### `gcloud apigee applications list`

List Apigee applications

List Apigee applications.

**Synopsis:**
```
gcloud apigee applications list
    [--developer=DEVELOPER --organization=ORGANIZATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--developer` | DEVELOPER |  | _[The arguments in this group can be used to specify the attributes of this resource.]_ ID of the developer or fully qualified identifier for the developer. To set the developer attribute: + provide the argument --developer on the command line; + leave the argument unspecified for it to be chosen automatically. |
| `--organization` | ORGANIZATION |  | _[The arguments in this group can be used to specify the attributes of this resource.]_ Apigee organization containing the developer. If unspecified, the Cloud Platform project's associated organization will be used. To set the organization attribute: + provide the argument --developer on the command line with a fully specified name; + leave the argument unspecified for it to be chosen automatically with a fully specified name; + provide the argument --organization on the command line; + set the property [project] or provide the argument [--project] on the command line, using a Cloud Platform project with an associated Apigee organization. |


**Examples:**
```bash
To list all Apigee applications in the active Cloud Platform project, run:

    $ gcloud apigee applications list

To list all Apigee applications belonging to the developer
horse@example.com in an Apigee organization called my-org, formatted as
JSON, run:

    $ gcloud apigee applications list --developer=horse@example.com \
      --organization=my-org --format=json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apigee/applications/list)

---
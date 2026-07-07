# gcloud apihub host-project-registrations

manage Host Project Registration resources

### `gcloud apihub host-project-registrations create`

Create a Host Project Registration

Create a host project registration.

Note: The positional argument for Host Project Registration ID is currently not supported. Please use the --host-project-registration flag to specify the Host Project Registration ID.

**Synopsis:**
```
gcloud apihub host-project-registrations create
    (HOST_PROJECT_REGISTRATION : --location=LOCATION)
    --gcp-project=GCP_PROJECT [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
HostProjectRegistration resource - Identifier. The name of the host
project registration. Format:
"projects/{project}/locations/{location}/hostProjectRegistrations/{host_project_registration}".
The arguments in this group can be used to specify the attributes of
this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument host_project_registration on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HOST_PROJECT_REGISTRATION
     ID of the hostProjectRegistration or fully qualified identifier
     for the hostProjectRegistration.

     To set the host_project_registration attribute:
     + provide the argument host_project_registration on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the hostProjectRegistration resource.

     To set the location attribute:
     + provide the argument host_project_registration on the command
       line with a fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--gcp-project` | GCP_PROJECT |  | Google cloud project name in the format: "projects/abc" or "projects/123". As input, project name with either project id or number are accepted. As output, this field will contain project number. |

**Examples:**
```bash
To register a host project with the ID `my-registration`, run:

    $ gcloud apihub host-project-registrations create \
        --host-project-registration=my-registration \
        --gcp-project=my-gcp-project --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/host-project-registrations/create)

---
### `gcloud apihub host-project-registrations describe`

Describe a Host Project Registration

Describe a host project registration.

**Synopsis:**
```
gcloud apihub host-project-registrations describe
    (HOST_PROJECT_REGISTRATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
HostProjectRegistration resource - Host project registration resource
name.
projects/{project}/locations/{location}/hostProjectRegistrations/{host_project_registration_id}
The arguments in this group can be used to specify the attributes of
this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument host_project_registration on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HOST_PROJECT_REGISTRATION
     ID of the hostProjectRegistration or fully qualified identifier
     for the hostProjectRegistration.

     To set the host_project_registration attribute:
     + provide the argument host_project_registration on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the hostProjectRegistration resource.

     To set the location attribute:
     + provide the argument host_project_registration on the command
       line with a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe a host project registration with the ID `my-registration`, run:

    $ gcloud apihub host-project-registrations describe my-registration \
        --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/host-project-registrations/describe)

---
### `gcloud apihub host-project-registrations list`

List Host Project Registrations

List host project registrations.

**Synopsis:**
```
gcloud apihub host-project-registrations list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Location resource - The parent, which owns this collection of host projects. Format: projects/*/locations/* This represents a Cloud resource. (NOTE) Some attributes are not given arguments in this group but can be set in other ways. To set the project attribute: provide the argument --location on the command line with a fully specified name; provide the argument --project on the command line; set the property core/project. This must be specified. ID of the location or fully qualified identifier for the location. To set the location attribute: provide the argument --location on the command line. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--filter` | EXPRESSION |  | Apply a Boolean filter EXPRESSION to each resource item to be listed. If the expression evaluates True, then that item is listed. For more details and examples of filter expressions, run $ gcloud topic filters. This flag interacts with other flags that are applied in this order: --flatten, --sort-by, --filter, --limit. |
| `--limit` | LIMIT | unlimited | Maximum number of resources to list. The default is unlimited. This flag interacts with other flags that are applied in this order: --flatten, --sort-by, --filter, --limit. |
| `--page-size` | PAGE_SIZE |  | Some services group resource list output into pages. This flag specifies the maximum number of resources per page. The default is determined by the service if it supports paging, otherwise it is unlimited (no paging). Paging may be applied before or after --filter and --limit depending on the service. |
| `--sort-by` | [FIELD,...] |  | Comma-separated list of resource field key names to sort by. The default order is ascending. Prefix a field with "~" for descending order on that field. This flag interacts with other flags that are applied in this order: --flatten, --sort-by, --filter, --limit. |
| `--uri` |  |  | Print a list of resource URIs instead of the default output, and change the command output to a list of URIs. If this flag is used with --format, the formatting is applied on this URI list. To display URIs alongside other keys instead, use the uri() transform. |

**Examples:**
```bash
To list all host project registrations in project `my-project` and location
`us-central1`, run:

    $ gcloud apihub host-project-registrations list --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/host-project-registrations/list)

---

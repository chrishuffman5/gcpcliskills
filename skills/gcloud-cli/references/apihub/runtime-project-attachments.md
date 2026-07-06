# gcloud apihub runtime-project-attachments

manage Runtime Project Attachment resources

### `gcloud apihub runtime-project-attachments create`

Create a Runtime Project Attachment

Create a runtime project attachment. Note: The positional argument for Runtime Project Attachment ID is currently not supported. Please use the --runtime-project-attachment flag to specify the Runtime Project Attachment ID.

**Synopsis:**
```
gcloud apihub runtime-project-attachments create
    (RUNTIME_PROJECT_ATTACHMENT : --location=LOCATION)
    --runtime-project=RUNTIME_PROJECT [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RuntimeProjectAttachment resource - Identifier. The resource name of a
runtime project attachment. Format:
"projects/{project}/locations/{location}/runtimeProjectAttachments/{runtime_project_attachment}".
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group
but can be set in other ways.

  RUNTIME_PROJECT_ATTACHMENT
     ID of the runtimeProjectAttachment or fully qualified identifier for
     the runtimeProjectAttachment.

  --location=LOCATION
     The location id of the runtimeProjectAttachment resource.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--runtime-project` | RUNTIME_PROJECT |  | Google cloud project name in the format: 'projects/abc' or 'projects/123'. As input, project name with either project id or number are accepted. As output, this field will contain project number. |

**Examples:**
```bash
To create a runtime project attachment with the ID my-attachment, run:

    $ gcloud apihub runtime-project-attachments create --runtime-project-attachment=my-attachment --runtime-project=my-runtime-project --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/runtime-project-attachments/create)

---
### `gcloud apihub runtime-project-attachments delete`

Delete a Runtime Project Attachment

Delete a runtime project attachment.

**Synopsis:**
```
gcloud apihub runtime-project-attachments delete
    (RUNTIME_PROJECT_ATTACHMENT : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RuntimeProjectAttachment resource - The name of the Runtime Project
Attachment to delete. Format:
projects/{project}/locations/{location}/runtimeProjectAttachments/{runtime_project_attachment}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group
but can be set in other ways.

To set the project attribute:
 * provide the argument runtime_project_attachment on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RUNTIME_PROJECT_ATTACHMENT
     ID of the runtimeProjectAttachment or fully qualified identifier for
     the runtimeProjectAttachment.

     To set the runtime_project_attachment attribute:
     + provide the argument runtime_project_attachment on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the runtimeProjectAttachment resource.

     To set the location attribute:
     + provide the argument runtime_project_attachment on the command
       line with a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To delete a runtime project attachment with the ID my-attachment, run:

    $ gcloud apihub runtime-project-attachments delete my-attachment --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/runtime-project-attachments/delete)

---
### `gcloud apihub runtime-project-attachments describe`

Describe a Runtime Project Attachment

Describe a runtime project attachment.

**Synopsis:**
```
gcloud apihub runtime-project-attachments describe
    (RUNTIME_PROJECT_ATTACHMENT : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RuntimeProjectAttachment resource - The name of the API resource to
retrieve. Format:
projects/{project}/locations/{location}/runtimeProjectAttachments/{runtime_project_attachment}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group
but can be set in other ways.

To set the project attribute:
 * provide the argument runtime_project_attachment on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RUNTIME_PROJECT_ATTACHMENT
     ID of the runtimeProjectAttachment or fully qualified identifier for
     the runtimeProjectAttachment.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the runtimeProjectAttachment resource.

     To set the location attribute:
     + provide the argument runtime_project_attachment on the command
       line with a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe a runtime project attachment with the ID my-attachment, run:

    $ gcloud apihub runtime-project-attachments describe my-attachment --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/runtime-project-attachments/describe)

---
### `gcloud apihub runtime-project-attachments list`

List Runtime Project Attachments

List runtime project attachments.

**Synopsis:**
```
gcloud apihub runtime-project-attachments list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Location resource - The parent, which owns this collection of runtime project attachments. Format: projects/{project}/locations/{location} This represents a Cloud resource. (NOTE) Some attributes are not given arguments in this group but can be set in other ways. To set the project attribute: provide the argument --location on the command line with a fully specified name; provide the argument --project on the command line; set the property core/project. This must be specified. ID of the location or fully qualified identifier for the location. To set the location attribute: provide the argument --location on the command line. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--filter` | EXPRESSION |  | Apply a Boolean filter EXPRESSION to each resource item to be listed. If the expression evaluates True, then that item is listed. For more details and examples of filter expressions, run $ gcloud topic filters. This flag interacts with other flags that are applied in this order: --flatten, --sort-by, --filter, --limit. |
| `--limit` | LIMIT | unlimited | Maximum number of resources to list. The default is unlimited. This flag interacts with other flags that are applied in this order: --flatten, --sort-by, --filter, --limit. |
| `--page-size` | PAGE_SIZE | determined by service | Some services group resource list output into pages. This flag specifies the maximum number of resources per page. The default is determined by the service if it supports paging, otherwise it is unlimited (no paging). Paging may be applied before or after --filter and --limit depending on the service. |
| `--sort-by` | [FIELD,...] | ascending | Comma-separated list of resource field key names to sort by. The default order is ascending. Prefix a field with ~ for descending order on that field. This flag interacts with other flags that are applied in this order: --flatten, --sort-by, --filter, --limit. |
| `--uri` |  |  | Print a list of resource URIs instead of the default output, and change the command output to a list of URIs. If this flag is used with --format, the formatting is applied on this URI list. To display URIs alongside other keys instead, use the uri() transform. |

**Examples:**
```bash
To list all runtime project attachments in project my-project and location us-central1, run:

    $ gcloud apihub runtime-project-attachments list --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/runtime-project-attachments/list)

---
### `gcloud apihub runtime-project-attachments lookup`

Lookup a runtime project attachment

Lookup a runtime project attachment.

**Synopsis:**
```
gcloud apihub runtime-project-attachments lookup --location=LOCATION
    --service-project=SERVICE_PROJECT [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | The location of the runtime project attachment. |
| `--service-project` | SERVICE_PROJECT |  | The service project ID to lookup attachment for. |

**Examples:**
```bash
To lookup a runtime project attachment for a specific service project, run:

    $ gcloud apihub runtime-project-attachments lookup --service-project=my-service-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/runtime-project-attachments/lookup)

---

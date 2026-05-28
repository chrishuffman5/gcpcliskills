# gcloud scc posture-templates

manage Cloud Security Command Center posture templates

### `gcloud scc posture-templates describe`

Describe a Cloud Security Command Center posture template

Describe a Cloud Security Command Center (SCC) posture template.

By default, the latest created revision of the posture template is
described. Users must provide revision ID to describe a specific revision.

**Synopsis:**
```
gcloud scc posture-templates describe
    (POSTURE_TEMPLATE : --location=LOCATION --organization=ORGANIZATION)
    [--revision-id=REVISION_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Posture template resource - Posture template to be described. For example
organizations/<organizationID>/locations/<location>/postureTemplates/<postureTemplateID>.
The arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  POSTURE_TEMPLATE
     ID of the posture_template or fully qualified identifier for the
     posture_template.

     To set the posture_template attribute:
     + provide the argument posture_template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     ID of the location where the resource exists (for example, global).

     To set the location attribute:
     + provide the argument posture_template on the command line with a
       fully specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     ID of the organization which is the parent of the resource.

     To set the organization attribute:
     + provide the argument posture_template on the command line with a
       fully specified name;
     + provide the argument --organization on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--revision-id` | REVISION_ID |  | ID of the specific posture template revision to be described. If not specified, latest revision is described. |


**Examples:**
```bash
Describe a posture template named
organizations/123/locations/global/postureTemplates/secure_by_default (i.e.
a posture in organization 123, location global, with id secure_by_default):

    $ gcloud scc posture-templates describe \
        organizations/123/locations/global/postureTemplates/\
    secure_by_default

Describe a specific revision v1.0.0 of posture template named
organizations/123/locations/global/postureTemplates/secure_by_default:

    $ gcloud scc posture-templates describe \
        organizations/123/locations/global/postureTemplates/\
    secure_by_default --revision-id=v1.0.0
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/posture-templates/describe)

---
### `gcloud scc posture-templates list`

List the details of the Cloud Security Command Center posture templates

List the details of the Cloud Security Command Center (SCC) posture
templates for the specified organization.

**Synopsis:**
```
gcloud scc posture-templates list
    ([PARENT] --location=LOCATION --organization=ORGANIZATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Exactly one of these must be specified:

  [PARENT]
     Parent of Cloud Security Command Center posture templates. Formatted
     as organizations/<organizationID>/locations/<location>.

  Specify organization and location using flags.

    --location=LOCATION
       When data residency controls are enabled, this attribute specifies
       the location in which the resource is located and applicable.

       This flag argument must be specified if any of the other arguments
       in this group are specified.

    --organization=ORGANIZATION
       The organization ID (e.g., 123) that contains the resource.

       This flag argument must be specified if any of the other arguments
       in this group are specified.
```

**Examples:**
```bash
To list Cloud Security Command Center posture templates for organization
123 and in the global location, run:

    $ gcloud scc posture-templates list \
        organizations/123/locations/global

    $ gcloud scc posture-templates list --organization=123 \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/posture-templates/list)

---
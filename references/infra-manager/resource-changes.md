# gcloud infra-manager resource-changes

manage resource change resources

### `gcloud infra-manager resource-changes describe`

Describe resource changes

Describe a resource change

**Synopsis:**
```
gcloud infra-manager resource-changes describe
    (RESOURCE_CHANGE : --location=LOCATION --preview=PREVIEW)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ResourceChange resource - The resource change to describe The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument resource_change on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RESOURCE_CHANGE
     ID of the resourceChange or fully qualified identifier for the
     resourceChange.

     To set the resource_change attribute:
     + provide the argument resource_change on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     locations TBD

     To set the location attribute:
     + provide the argument resource_change on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property infra-manager/location.

  --preview=PREVIEW
     preview TBD

     To set the preview attribute:
     + provide the argument resource_change on the command line with a
       fully specified name;
     + provide the argument --preview on the command line.
```

**Examples:**
```bash
To describe a resource change rc under preview pr1 at location us-central1,
run:

    $ gcloud infra-manager resource-changes describe \
        projects/p1/locations/us-central1/previews/pr1/resourceChanges/\
    rc
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/infra-manager/resource-changes/describe)

---
### `gcloud infra-manager resource-changes list`

List resource changes

List resource changes for a preview

**Synopsis:**
```
gcloud infra-manager resource-changes list
    (--preview=PREVIEW : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--preview` | PREVIEW |  | _[This must be specified.]_ ID of the preview or fully qualified identifier for the preview. To set the preview attribute: + provide the argument --preview on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ locations TBD To set the location attribute: + provide the argument --preview on the command line with a fully specified name; + provide the argument --location on the command line; + set the property infra-manager/location. |


**Examples:**
```bash
To list all resource changes for preview
projects/p1/locations/us-central1/previews/pr1, run:

    $ gcloud infra-manager resource-changes list \
        --preview=projects/p1/locations/us-central1/previews/pr1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/infra-manager/resource-changes/list)

---
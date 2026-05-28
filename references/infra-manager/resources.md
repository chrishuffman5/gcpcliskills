# gcloud infra-manager resources

list or describe resources under a Revision

### `gcloud infra-manager resources describe`

Describe resources

Describe a resource

**Synopsis:**
```
gcloud infra-manager resources describe
    (RESOURCE
      : --deployment=DEPLOYMENT --location=LOCATION --revision=REVISION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Resource resource - The resource to describe The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument resource on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RESOURCE
     ID of the resource or fully qualified identifier for the resource.

     To set the resource attribute:
     + provide the argument resource on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --deployment=DEPLOYMENT
     deployments TBD

     To set the deployment attribute:
     + provide the argument resource on the command line with a fully
       specified name;
     + provide the argument --deployment on the command line.

  --location=LOCATION
     locations TBD

     To set the location attribute:
     + provide the argument resource on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property infra-manager/location.

  --revision=REVISION
     revisions TBD

     To set the revision attribute:
     + provide the argument resource on the command line with a fully
       specified name;
     + provide the argument --revision on the command line.
```

**Examples:**
```bash
To describe a resource compute-resource under revision
projects/p1/locations/us-central1/deployments/example-deployment/revisions/r-0,
run:

    $ gcloud infra-manager resources describe \
        projects/p1/locations/us-central1/deployments/\
    example-deployment/revisions/r-0/resources/compute-resource
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/infra-manager/resources/describe)

---
### `gcloud infra-manager resources list`

List resources

List resources for a deployment revision

**Synopsis:**
```
gcloud infra-manager resources list
    (--revision=REVISION : --deployment=DEPLOYMENT --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--revision` | REVISION |  | _[This must be specified.]_ ID of the revision or fully qualified identifier for the revision. To set the revision attribute: + provide the argument --revision on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--deployment` | DEPLOYMENT |  | _[This must be specified.]_ deployments TBD To set the deployment attribute: + provide the argument --revision on the command line with a fully specified name; + provide the argument --deployment on the command line. |
| `--location` | LOCATION |  | _[This must be specified.]_ locations TBD To set the location attribute: + provide the argument --revision on the command line with a fully specified name; + provide the argument --location on the command line; + set the property infra-manager/location. |


**Examples:**
```bash
To list all resources for a deployment revision,
projects/p1/locations/l1/deployments/d1/revisions/r-0, run:

    $ gcloud infra-manager resources list \
        --revision=projects/p1/locations/l1/deployments/d1/revisions/r-0
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/infra-manager/resources/list)

---
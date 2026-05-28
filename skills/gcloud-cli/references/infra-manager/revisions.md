# gcloud infra-manager revisions

manage Revision resources

### `gcloud infra-manager revisions describe`

Describe revisions

Describe a revision

**Synopsis:**
```
gcloud infra-manager revisions describe
    (REVISION : --deployment=DEPLOYMENT --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Revision resource - The revision to describe The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument revision on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  REVISION
     ID of the revision or fully qualified identifier for the revision.

     To set the revision attribute:
     + provide the argument revision on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --deployment=DEPLOYMENT
     deployments TBD

     To set the deployment attribute:
     + provide the argument revision on the command line with a fully
       specified name;
     + provide the argument --deployment on the command line.

  --location=LOCATION
     locations TBD

     To set the location attribute:
     + provide the argument revision on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property infra-manager/location.
```

**Examples:**
```bash
To describe the revision r-0 under deployment example-deployment at
location us-central1, run:

    $ gcloud infra-manager revisions describe \
        projects/p1/locations/us-central1/deployments/\
    example-deployment/revisions/r-0
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/infra-manager/revisions/describe)

---
### `gcloud infra-manager revisions export-statefile`

Export a terraform state file

This command generates a signed url to download a terraform state file.

**Synopsis:**
```
gcloud infra-manager revisions export-statefile
    (REVISION : --deployment=DEPLOYMENT --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Revision resource - the revision to be used as parent. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument REVISION on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  REVISION
     ID of the revision or fully qualified identifier for the revision.

     To set the revision attribute:
     + provide the argument REVISION on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --deployment=DEPLOYMENT
     The deployment for the revision.

     To set the deployment attribute:
     + provide the argument REVISION on the command line with a fully
       specified name;
     + provide the argument --deployment on the command line.

  --location=LOCATION
     The Cloud location for the revision.

     To set the location attribute:
     + provide the argument REVISION on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property infra-manager/location.
```

**Examples:**
```bash
Export state file for revision
projects/p1/locations/l1/deployments/d1/revisions/r-0:

    $ gcloud infra-manager revisions export-statefile \
        projects/p1/locations/l1/deployments/d1/revisions/r-0
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/infra-manager/revisions/export-statefile)

---
### `gcloud infra-manager revisions list`

List revisions

List revisions for a deployment

**Synopsis:**
```
gcloud infra-manager revisions list
    (--deployment=DEPLOYMENT : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--deployment` | DEPLOYMENT |  | _[This must be specified.]_ ID of the deployment or fully qualified identifier for the deployment. To set the deployment attribute: + provide the argument --deployment on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ locations TBD To set the location attribute: + provide the argument --deployment on the command line with a fully specified name; + provide the argument --location on the command line; + set the property infra-manager/location. |


**Examples:**
```bash
To list all revisions for deployment
projects/p1/locations/l1/deployments/d1, run:

    $ gcloud infra-manager revisions list \
        --deployment=projects/p1/locations/l1/deployments/d1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/infra-manager/revisions/list)

---
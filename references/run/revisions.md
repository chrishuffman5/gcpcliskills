# gcloud run revisions

view and manage your Cloud Run revisions

### `gcloud run revisions delete`

Delete a revision

Delete a revision.

**Synopsis:**
```
gcloud run revisions delete (REVISION : --namespace=NAMESPACE)
    [--[no-]async] [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Revision resource - Revision to delete. The arguments in this group can be
used to specify the attributes of this resource.

This must be specified.

  REVISION
     ID of the revision or fully qualified identifier for the revision.

     To set the revision attribute:
     + provide the argument REVISION on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --namespace=NAMESPACE
     Specific to Cloud Run for Anthos: Kubernetes namespace for the
     revision.

     To set the namespace attribute:
     + provide the argument REVISION on the command line with a fully
       specified name;
     + provide the argument --namespace on the command line;
     + set the property run/namespace;
     + For Cloud Run on Kubernetes Engine, defaults to "default".
       Otherwise, defaults to project ID.;
     + provide the argument project on the command line;
     + set the property core/project.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--[no-]async` |  |  | Return immediately, without waiting for the operation in progress to complete. Defaults to --no-async. Use --async to enable and --no-async to disable. |
| `--region` | REGION |  | Region in which the resource can be found. Alternatively, set the property [run/region]. |


**Examples:**
```bash
To delete a revision:

    $ gcloud run revisions delete <revision-name>
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/revisions/delete)

---
### `gcloud run revisions describe`

Obtain details about revisions

Obtain details about revisions.

**Synopsis:**
```
gcloud run revisions describe (REVISION : --namespace=NAMESPACE)
    [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Revision resource - Revision to describe. The arguments in this group can
be used to specify the attributes of this resource.

This must be specified.

  REVISION
     ID of the revision or fully qualified identifier for the revision.

     To set the revision attribute:
     + provide the argument REVISION on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --namespace=NAMESPACE
     Specific to Cloud Run for Anthos: Kubernetes namespace for the
     revision.

     To set the namespace attribute:
     + provide the argument REVISION on the command line with a fully
       specified name;
     + provide the argument --namespace on the command line;
     + set the property run/namespace;
     + For Cloud Run on Kubernetes Engine, defaults to "default".
       Otherwise, defaults to project ID.;
     + provide the argument project on the command line;
     + set the property core/project.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region in which the resource can be found. Alternatively, set the property [run/region]. |


**Examples:**
```bash
To describe a revision my-service-00001-abc`in us-central1:

    $ gcloud run revisions describe --region=us-central1 \
      my-service-00001-abc
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/revisions/describe)

---
### `gcloud run revisions list`

List available revisions

List available revisions.

**Synopsis:**
```
gcloud run revisions list [--region=REGION] [--service=SERVICE]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region in which the resource can be found. Alternatively, set the property [run/region]. |
| `--service` | SERVICE |  | Limit matched revisions to the given service. |


**Examples:**
```bash
To list all revisions for the provided service:

    $ gcloud run revisions list --service=foo
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/revisions/list)

---
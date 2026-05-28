# gcloud workspace-add-ons deployments

manage Google Workspace Add-ons Deployments

### `gcloud workspace-add-ons deployments create`

Create a Google Workspace Add-ons deployment

**Synopsis:**
```
gcloud workspace-add-ons deployments create DEPLOYMENT
    (--deployment-file=DEPLOYMENT_FILE
      | --deployment-object=DEPLOYMENT_OBJECT) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Deployment resource - Google Workspace Add-ons deployment to create This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument deployment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DEPLOYMENT
     ID of the deployment or fully qualified identifier for the
     deployment.

     To set the deployment attribute:
     + provide the argument deployment on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--deployment-file` | DEPLOYMENT_FILE |  | _[Exactly one of these must be specified:]_ path to the deployment file |
| `--deployment-object` | DEPLOYMENT_OBJECT |  | _[Exactly one of these must be specified:]_ json string of the deploymentObject |


**Examples:**
```bash
To create an deployment called my-deployment with the deployment file, run:

    $ gcloud workspace-add-ons deployments create my-deployment \
        --deployment-file=my-deployment.json

To create an deployment called my-deployment with the deployment object,
run:

    $ gcloud workspace-add-ons deployments create my-deployment \
        --deployment-object=my-deployment-string
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workspace-add-ons/deployments/create)

---
### `gcloud workspace-add-ons deployments delete`

Delete a Google Workspace Add-ons deployment

**Synopsis:**
```
gcloud workspace-add-ons deployments delete DEPLOYMENT [--etag=ETAG]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Deployment resource - Google Workspace Add-ons deployment to delete This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument deployment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DEPLOYMENT
     ID of the deployment or fully qualified identifier for the
     deployment.

     To set the deployment attribute:
     + provide the argument deployment on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--etag` | ETAG |  | etag of the deployment file |


**Examples:**
```bash
To delete an deployment called my-deployment, run:

    $ gcloud workspace-add-ons deployments delete my-deployment
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workspace-add-ons/deployments/delete)

---
### `gcloud workspace-add-ons deployments describe`

Describe a Google Workspace Add-ons deployment

**Synopsis:**
```
gcloud workspace-add-ons deployments describe DEPLOYMENT
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Deployment resource - Google Workspace Add-ons deployment to describe This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument deployment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DEPLOYMENT
     ID of the deployment or fully qualified identifier for the
     deployment.

     To set the deployment attribute:
     + provide the argument deployment on the command line.
```

**Examples:**
```bash
To describe an deployment called my-deployment, run:

    $ gcloud workspace-add-ons deployments describe my-deployment
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workspace-add-ons/deployments/describe)

---
### `gcloud workspace-add-ons deployments install`

Install a Google Workspace Add-ons deployment

**Synopsis:**
```
gcloud workspace-add-ons deployments install DEPLOYMENT
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Deployment resource - Google Workspace Add-ons deployment to install This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument deployment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DEPLOYMENT
     ID of the deployment or fully qualified identifier for the
     deployment.

     To set the deployment attribute:
     + provide the argument deployment on the command line.
```

**Examples:**
```bash
To install a deployment called my-deployment, run:

    $ gcloud workspace-add-ons deployments install my-deployment
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workspace-add-ons/deployments/install)

---
### `gcloud workspace-add-ons deployments install-status`

Get the install status of a Google Workspace Add-ons deployment

**Synopsis:**
```
gcloud workspace-add-ons deployments install-status DEPLOYMENT
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Deployment resource - Google Workspace Add-ons deployment to get install
status This represents a Cloud resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument deployment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DEPLOYMENT
     ID of the deployment or fully qualified identifier for the
     deployment.

     To set the deployment attribute:
     + provide the argument deployment on the command line.
```

**Examples:**
```bash
To get the install status of a deployment called my-deployment, run:

    $ gcloud workspace-add-ons deployments install-status my-deployment
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workspace-add-ons/deployments/install-status)

---
### `gcloud workspace-add-ons deployments list`

List Google Workspace Add-ons deployments

**Synopsis:**
```
gcloud workspace-add-ons deployments list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all deployments, run:

    $ gcloud workspace-add-ons deployments list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workspace-add-ons/deployments/list)

---
### `gcloud workspace-add-ons deployments replace`

Replace a Google Workspace Add-ons deployment

**Synopsis:**
```
gcloud workspace-add-ons deployments replace DEPLOYMENT
    (--deployment-file=DEPLOYMENT_FILE
      | --deployment-object=DEPLOYMENT_OBJECT) [--etag=ETAG]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Deployment resource - Google Workspace Add-ons deployment to replace This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument deployment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DEPLOYMENT
     ID of the deployment or fully qualified identifier for the
     deployment.

     To set the deployment attribute:
     + provide the argument deployment on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--deployment-file` | DEPLOYMENT_FILE |  | _[Exactly one of these must be specified:]_ path to the deployment file |
| `--deployment-object` | DEPLOYMENT_OBJECT |  | _[Exactly one of these must be specified:]_ json string of the deploymentObject |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--etag` | ETAG |  | etag of the deployment file |


**Examples:**
```bash
To replace an deployment called my-deployment with the deployment file,
run:

    $ gcloud workspace-add-ons deployments replace my-deployment \
        --deployment-file=my-deployment.json

To replace an deployment called my-deployment with the deployment object,
run:

    $ gcloud workspace-add-ons deployments replace my-deployment \
        --deployment-object=my-deployment-string
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workspace-add-ons/deployments/replace)

---
### `gcloud workspace-add-ons deployments uninstall`

Uninstall a Google Workspace Add-ons deployment

**Synopsis:**
```
gcloud workspace-add-ons deployments uninstall DEPLOYMENT
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Deployment resource - Google Workspace Add-ons deployment to uninstall
This represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument deployment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DEPLOYMENT
     ID of the deployment or fully qualified identifier for the
     deployment.

     To set the deployment attribute:
     + provide the argument deployment on the command line.
```

**Examples:**
```bash
To uninstall a deployment called my-deployment, run:

    $ gcloud workspace-add-ons deployments uninstall my-deployment
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workspace-add-ons/deployments/uninstall)

---
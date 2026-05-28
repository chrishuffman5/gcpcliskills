# gcloud compute shared-vpc

configure shared VPC

### `gcloud compute shared-vpc disable`

Disable the given project as a shared VPC host

That is, after running this command, this project will not be able to share
VPC networks to other projects.

**Synopsis:**
```
gcloud compute shared-vpc disable PROJECT_ID [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PROJECT_ID
   ID for the project to disable as a shared VPC host
```

**Examples:**
```bash
To disable the project myproject as a shared VPC host, run:

    $ gcloud compute shared-vpc disable myproject
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/shared-vpc/disable)

---
### `gcloud compute shared-vpc enable`

Enable the given project as a shared VPC host

That is, after running this command, one can enable another project to use
the VPC networks shared by this project.

**Synopsis:**
```
gcloud compute shared-vpc enable PROJECT_ID [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PROJECT_ID
   ID for the project to enable as a shared VPC host
```

**Examples:**
```bash
To enable the project myproject as a shared VPC host, run:

    $ gcloud compute shared-vpc enable myproject
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/shared-vpc/enable)

---
### `gcloud compute shared-vpc get-host-project`

Get the shared VPC host project that the given project is associated with

Get the shared VPC host project that the given project is associated with.

**Synopsis:**
```
gcloud compute shared-vpc get-host-project PROJECT_ID
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PROJECT_ID
   ID for the project to get the host project for
```

**Examples:**
```bash
If service-project1 and service-project2 are associated service projects of
the shared VPC host project host-project,

    $ gcloud compute shared-vpc get-host-project service-project1

will show the host-project project.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/shared-vpc/get-host-project)

---
### `gcloud compute shared-vpc list-associated-resources`

List the resources associated with the given shared VPC host project

List the resources associated with the given shared VPC host project.

**Synopsis:**
```
gcloud compute shared-vpc list-associated-resources PROJECT_ID
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PROJECT_ID
   ID for the project to get associated resources for
```

**Examples:**
```bash
If service-project1 and service-project2 are associated service projects of
the shared VPC host project host-project,

    $ gcloud compute shared-vpc list-associated-resources host-project

yields the output

    RESOURCE_ID         RESOURCE_TYPE
    service-project1    PROJECT
    service-project2    PROJECT
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/shared-vpc/list-associated-resources)

---

## `gcloud compute shared-vpc associated-projects` — configure associated projects for Shared VPC networking
### `gcloud compute shared-vpc associated-projects add`

Associate the given project with a given shared VPC host project

Associate the given project with a given shared VPC host project.

**Synopsis:**
```
gcloud compute shared-vpc associated-projects add PROJECT_ID
    --host-project=HOST_PROJECT [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PROJECT_ID
   ID for the project to add to the host project
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--host-project` | HOST_PROJECT |  | The XPN host to add an associated project to |


**Examples:**
```bash
To add the project service-project as an associated service project of the
shared VPC host project host-project, run:

    $ gcloud compute shared-vpc associated-projects add \
        --host-project=host-project service-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/shared-vpc/associated-projects/add)

---
### `gcloud compute shared-vpc associated-projects list`

List the associated service projects of the given host project

List the associated service projects of the given host project.

**Synopsis:**
```
gcloud compute shared-vpc associated-projects list PROJECT_ID
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PROJECT_ID
   ID for the project to get associated projects for
```

**Examples:**
```bash
If service-project1 and service-project2 are associated service projects of
the shared VPC host project host-project,

    $ gcloud compute shared-vpc associated-projects list host-project

yields the output

    RESOURCE_ID         RESOURCE_TYPE
    service-project1    PROJECT
    service-project2    PROJECT
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/shared-vpc/associated-projects/list)

---
### `gcloud compute shared-vpc associated-projects remove`

Disassociate the given project from the given shared VPC host project

Disassociate the given project from the given shared VPC host project.

**Synopsis:**
```
gcloud compute shared-vpc associated-projects remove PROJECT_ID
    --host-project=HOST_PROJECT [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PROJECT_ID
   ID for the project to remove from the host project
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--host-project` | HOST_PROJECT |  | The XPN host to remove the associated project from |


**Examples:**
```bash
To remove the project service-project as an associated shared VPC service
project of the shared VPC host project host-project, run:

    $ gcloud compute shared-vpc associated-projects remove \
        --host-project=host-project service-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/shared-vpc/associated-projects/remove)

---

## `gcloud compute shared-vpc organizations` — configure organizations for Shared VPC networking
### `gcloud compute shared-vpc organizations list-host-projects`

List shared VPC host projects in a given organization

List shared VPC host projects in a given organization.

**Synopsis:**
```
gcloud compute shared-vpc organizations list-host-projects ORGANIZATION_ID
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ORGANIZATION_ID
   ID or domain for the organization whose XPN host projects to list.
```

**Examples:**
```bash
To list the shared VPC host projects in the organization with ID 12345,
run:

    $ gcloud compute shared-vpc organizations list-host-projects 12345

    NAME       CREATION_TIMESTAMP            XPN_PROJECT_STATUS
    xpn-host1  2000-01-01T12:00:00.00-00:00  HOST
    xpn-host2  2000-01-02T12:00:00.00-00:00  HOST
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/shared-vpc/organizations/list-host-projects)

---
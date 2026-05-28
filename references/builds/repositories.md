# gcloud builds repositories

manage repositories for Cloud Build

### `gcloud builds repositories create`

Create a Cloud Build repository

Create a Cloud Build repository in a connection.

**Synopsis:**
```
gcloud builds repositories create
    (REPOSITORY : --connection=CONNECTION --region=REGION)
    --remote-uri=REMOTE_URI [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Repository resource - Repository to create. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument repository on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  REPOSITORY
     ID of the repository or fully qualified identifier for the
     repository.

     To set the repository attribute:
     + provide the argument repository on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --connection=CONNECTION
     Connection ID.

     To set the connection attribute:
     + provide the argument repository on the command line with a fully
       specified name;
     + provide the argument --connection on the command line.

  --region=REGION
     The Google Cloud region.

     To set the region attribute:
     + provide the argument repository on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property builds/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--remote-uri` | REMOTE_URI |  | The remote git clone URL of the repository. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To Create a repository with name my-repo in the connection my-conn, run the
following command:

    $ gcloud builds repositories create my-repo \
        --remote-uri=https://github.com/octocat/Hello-World.git \
        --connection=my-conn --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/repositories/create)

---
### `gcloud builds repositories delete`

Delete a Cloud Build Repository

Delete a Cloud Build Repository in a Connection.

**Synopsis:**
```
gcloud builds repositories delete
    (REPOSITORY : --connection=CONNECTION --region=REGION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Repository resource - Cloud Build repository to delete. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument repository on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  REPOSITORY
     ID of the repository or fully qualified identifier for the
     repository.

     To set the repository attribute:
     + provide the argument repository on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --connection=CONNECTION
     Connection ID.

     To set the connection attribute:
     + provide the argument repository on the command line with a fully
       specified name;
     + provide the argument --connection on the command line.

  --region=REGION
     The Google Cloud region.

     To set the region attribute:
     + provide the argument repository on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property builds/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete Cloud Build repository my-repo in connection my-conn, run the
following command:

    $ gcloud builds repositories delete my-repo --connection=my-conn \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/repositories/delete)

---
### `gcloud builds repositories describe`

Describe a Cloud Build Repository

Describe a Cloud Build Repository.

**Synopsis:**
```
gcloud builds repositories describe
    (REPOSITORY : --connection=CONNECTION --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Repository resource - Cloud Build Repository to describe. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument repository on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  REPOSITORY
     ID of the repository or fully qualified identifier for the
     repository.

     To set the repository attribute:
     + provide the argument repository on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --connection=CONNECTION
     Connection ID.

     To set the connection attribute:
     + provide the argument repository on the command line with a fully
       specified name;
     + provide the argument --connection on the command line.

  --region=REGION
     The Google Cloud region.

     To set the region attribute:
     + provide the argument repository on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property builds/region.
```

**Examples:**
```bash
To list all the Cloud Build connections in region us-central1, run the
following command:

    $ gcloud builds repositories describe --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/repositories/describe)

---
### `gcloud builds repositories list`

List all Cloud Build repositories in a connection

List all Cloud Build repositories in a connection.

**Synopsis:**
```
gcloud builds repositories list (--connection=CONNECTION : --region=REGION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--connection` | CONNECTION |  | _[This must be specified.]_ ID of the connection or fully qualified identifier for the connection. To set the connection attribute: + provide the argument --connection on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--region` | REGION |  | _[This must be specified.]_ The Google Cloud region. To set the region attribute: + provide the argument --connection on the command line with a fully specified name; + provide the argument --region on the command line; + set the property builds/region. |


**Examples:**
```bash
To list all the repositories in the Cloud Build connection my-conn, run the
following command:

    $ gcloud builds repositories list --connection=my-conn \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/repositories/list)

---
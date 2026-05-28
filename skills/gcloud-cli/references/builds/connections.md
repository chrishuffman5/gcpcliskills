# gcloud builds connections

manage connections for Google Cloud Build

### `gcloud builds connections add-iam-policy-binding`

Add IAM policy binding to a Cloud Build connection

Add IAM policy binding to a Cloud Build connection. One binding consists of
a member and a role.

**Synopsis:**
```
gcloud builds connections add-iam-policy-binding
    (CONNECTION : --region=REGION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connection resource - Cloud Build Connection for which to add the IAM
policy binding. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument connection on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTION
     ID of the connection or fully qualified identifier for the
     connection.

     To set the connection attribute:
     + provide the argument connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Google Cloud region.

     To set the region attribute:
     + provide the argument connection on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property builds/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Examples:**
```bash
To add an IAM policy binding for the role of
'roles/cloudbuild.connectionViewer' for the user 'test-user@gmail.com' on a
Connection named 'my-conn', run:

    $ gcloud builds connections add-iam-policy-binding my-conn \
        --region=us-central1 --member='user:test-user@gmail.com' \
        --role='roles/cloudbuild.connectionViewer'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/connections/add-iam-policy-binding)

---
### `gcloud builds connections delete`

Delete a Cloud Build Connection

Delete a Cloud Build Connection.

**Synopsis:**
```
gcloud builds connections delete (CONNECTION : --region=REGION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connection resource - Cloud Build connection to delete. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument connection on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTION
     ID of the connection or fully qualified identifier for the
     connection.

     To set the connection attribute:
     + provide the argument connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Google Cloud region.

     To set the region attribute:
     + provide the argument connection on the command line with a fully
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
To delete Cloud Build connection my-conn in region us-central1, run the
following command:

    $ gcloud builds connections delete my-conn --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/connections/delete)

---
### `gcloud builds connections describe`

Describe a Cloud Build Connection

Describe a Cloud Build Connection.

**Synopsis:**
```
gcloud builds connections describe (CONNECTION : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connection resource - Cloud Build Connection to describe. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument connection on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTION
     ID of the connection or fully qualified identifier for the
     connection.

     To set the connection attribute:
     + provide the argument connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Google Cloud region.

     To set the region attribute:
     + provide the argument connection on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property builds/region.
```

**Examples:**
```bash
To describe a Connection my-conn in region us-central1, run the following
command:

    $ gcloud builds connections describe my-conn --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/connections/describe)

---
### `gcloud builds connections get-iam-policy`

Get the IAM policy for a Cloud Build connection

Get the IAM policy for a Cloud Build connection.

**Synopsis:**
```
gcloud builds connections get-iam-policy (CONNECTION : --region=REGION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connection resource - Cloud Build Connection from which to get IAM policy.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument connection on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTION
     ID of the connection or fully qualified identifier for the
     connection.

     To set the connection attribute:
     + provide the argument connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Google Cloud region.

     To set the region attribute:
     + provide the argument connection on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property builds/region.
```

**Examples:**
```bash
To print the IAM policy for a Connection named 'my-conn', run the following
command:

    $ gcloud builds connections get-iam-policy my-conn \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/connections/get-iam-policy)

---
### `gcloud builds connections list`

List all Cloud Build connections for a project and region

List all Cloud Build connections for a project and region.

**Synopsis:**
```
gcloud builds connections list [--region=REGION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[* set the property core/project.]_ ID of the region or fully qualified identifier for the region. To set the region attribute: + provide the argument --region on the command line; + set the property builds/region. |


**Examples:**
```bash
To list all the Cloud Build connections in region us-central1, run the
following command:

    $ gcloud builds connections list --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/connections/list)

---
### `gcloud builds connections set-iam-policy`

Set the IAM policy for a Cloud Build connection

Set the IAM policy for a Cloud Build connection as defined in a JSON or
YAML file.

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud builds connections set-iam-policy (CONNECTION : --region=REGION)
    POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connection resource - Cloud Build Connection for which to set IAM policy.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument connection on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTION
     ID of the connection or fully qualified identifier for the
     connection.

     To set the connection attribute:
     + provide the argument connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Google Cloud region.

     To set the region attribute:
     + provide the argument connection on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property builds/region.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command will read an IAM policy defined in a JSON file
'policy.json' and set it for the Connection named 'my-conn':

    $ gcloud builds connections set-iam-policy my-conn policy.json \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/connections/set-iam-policy)

---

## `gcloud builds connections create` — create Connections in Google Cloud Build
### `gcloud builds connections create bitbucket-cloud`

Create a Cloud Build Connection for Bitbucket Cloud

Create a Cloud Build Connection for Bitbucket Cloud.

A Bitbucket Cloud Connection can be created by using a
repository/project/workspace access token with
repository_read,repository_admin, pullrequest_read, webhook scope
permission and a repository/project/workspace access token with
repository_read scope permission.

**Synopsis:**
```
gcloud builds connections create bitbucket-cloud
    (CONNECTION : --region=REGION)
    --authorizer-token-secret-version=AUTHORIZER_TOKEN_SECRET_VERSION
    --read-authorizer-token-secret-version=READ_AUTHORIZER_TOKEN_SECRET_VERSION
    --webhook-secret-secret-version=WEBHOOK_SECRET_SECRET_VERSION
    --workspace=WORKSPACE [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connection resource - Connection to create. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument connection on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTION
     ID of the connection or fully qualified identifier for the
     connection.

     To set the connection attribute:
     + provide the argument connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Google Cloud region.

     To set the region attribute:
     + provide the argument connection on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property builds/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--authorizer-token-secret-version` | AUTHORIZER_TOKEN_SECRET_VERSION |  | Secret containing the repository_read,repository_admin, pullrequest_read, webhook repository/project/workspace access token. |
| `--read-authorizer-token-secret-version` | READ_AUTHORIZER_TOKEN_SECRET_VERSION |  | Secret containing the repository_read repository/project/workspace access token. |
| `--webhook-secret-secret-version` | WEBHOOK_SECRET_SECRET_VERSION |  | Secret containing the webhook secret string for validating webhook events sent by Bitbucket Cloud. |
| `--workspace` | WORKSPACE |  | Workspace of the Bitbucket Cloud instance. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To create a Bitbucket Cloud connection, provide all the required
parameters:

    $ gcloud builds connections create bitbucket-cloud \
        my-bitbucket-conn --project=myproj --region=us-central1 \
        --workspace=my-workspace \
        --read-authorizer-token-secret-version=projects/myproj/secrets/\
    read-pat/versions/1 \
        --authorizer-token-secret-version=projects/myproj/secrets/\
    admin-pat/versions/1 \
        --webhook-secret-secret-version=projects/myproj/secrets/\
    whsecret/versions/1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/connections/create/bitbucket-cloud)

---
### `gcloud builds connections create bitbucket-data-center`

Create a Cloud Build Connection for Bitbucket Data Center

Create a Cloud Build Connection for Bitbucket Data Center.

A Bitbucket Data Center Connection can be created by using a personal
access token with REPO_ADMIN scope permission. A REPO_READ scoped personal
access token will also be required.

If the Bitbucket Data Center can only be accessed within a VPC, a Service
Directory service resource can be provided for connecting to it.

**Synopsis:**
```
gcloud builds connections create bitbucket-data-center
    (CONNECTION : --region=REGION)
    --authorizer-token-secret-version=AUTHORIZER_TOKEN_SECRET_VERSION
    --read-authorizer-token-secret-version=READ_AUTHORIZER_TOKEN_SECRET_VERSION
    --webhook-secret-secret-version=WEBHOOK_SECRET_SECRET_VERSION [--async]
    [--host-uri=HOST_URI]
    [--service-directory-service=SERVICE_DIRECTORY_SERVICE
      : --ssl-ca-file=SSL_CA_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connection resource - Connection to create. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument connection on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTION
     ID of the connection or fully qualified identifier for the
     connection.

     To set the connection attribute:
     + provide the argument connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Google Cloud region.

     To set the region attribute:
     + provide the argument connection on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property builds/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--authorizer-token-secret-version` | AUTHORIZER_TOKEN_SECRET_VERSION |  | Secret containing the REPO_ADMIN personal access token. |
| `--read-authorizer-token-secret-version` | READ_AUTHORIZER_TOKEN_SECRET_VERSION |  | Secret containing the REPO_READ personal access token. |
| `--webhook-secret-secret-version` | WEBHOOK_SECRET_SECRET_VERSION |  | Secret containing the webhook secret string for validating webhook events sent by Bitbucket Data Center. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--host-uri` | HOST_URI |  | URI of the Bitbucket Data Center instance. |


**Examples:**
```bash
To create a Bitbucket Data Center connection, provide all the required
parameters:

    $ gcloud builds connections create bitbucket-data-center \
        my-bitbucket-conn --project=myproj --region=us-central1 \
        --host-uri=https://bitbucket-server.net \
        --read-authorizer-token-secret-version=projects/myproj/secrets/\
    read-pat/versions/1 \
        --authorizer-token-secret-version=projects/myproj/secrets/\
    admin-pat/versions/1 \
        --webhook-secret-secret-version=projects/myproj/secrets/\
    whsecret/versions/1

To create a Bitbucket Data Center connection for a private Bitbucket Data
Center server. Provide the service-directory-service and ssl-ca-file as
well:

    $ gcloud builds connections create bitbucket-data-center \
        my-private-bitbucket-conn \
        --host-uri=https://my.private-bitbucket-server.net \
        --project=myproj --region=us-central1 \
        --service-directory-service=projects/myproj/namespaces/x/\
    services/mysds --ssl-ca-file=mycertificate.crt \
        --authorizer-token-secret-version=projects/myproj/secrets/\
    admin-pat/versions/1 \
        --read-authorizer-token-secret-version=projects/myproj/secrets/\
    read-pat/versions/1 \
        --webhook-secret-secret-version=projects/myproj/secrets/\
    whsecret/versions/1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/connections/create/bitbucket-data-center)

---
### `gcloud builds connections create github`

Create a Cloud Build Connection of type GitHub

Create a Cloud Build Connection of type GitHub (for github.com).

Connections for github.com can be created either by following an
installation process (that requires manual steps in a web browser) or by
providing the properties of an already-installed application (installation
ID and a user token) as arguments to this command.

**Synopsis:**
```
gcloud builds connections create github (CONNECTION : --region=REGION)
    [--async]
    [--authorizer-token-secret-version=AUTHORIZER_TOKEN_SECRET_VERSION
      : --app-installation-id=APP_INSTALLATION_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connection resource - Connection to create. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument connection on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTION
     ID of the connection or fully qualified identifier for the
     connection.

     To set the connection attribute:
     + provide the argument connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Google Cloud region.

     To set the region attribute:
     + provide the argument connection on the command line with a fully
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
To create a connection by following the installation process, provide only
the connection name:

    $ gcloud builds connections create github myconn --project=myproj \
        --region=us-central1

The command will print a URL to be opened in a web browser in order to
authorize Cloud Build (i.e. Cloud Build gets an OAuth token for the github
account that you use). After doing this authorization, you can get the
connection's installation state with the describe command:

    $ gcloud alpha builds connections describe myconn

The output will include a second link to install the Cloud Build GitHub
App. After doing this, the connection will be in installation state
COMPLETE and repositories can be added to it (see gcloud alpha builds
repositories create).

--

To create a complete connection (e.g. based on an existing user token and
installation), provide both the authorizer secret token and the app
installation id:

    $ gcloud builds connections create github myconn --project=myproj \
        --region=us-central1 \
        --authorizer-token-secret-version=projects/myproj/secrets/\
    mytoken/versions/1 --app-installation-id=1234

Above command creates the connection in installation state COMPLETE, ready
for adding repositories.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/connections/create/github)

---
### `gcloud builds connections create github-enterprise`

Create a Cloud Build Connection of type GitHub Enterprise

Create a Cloud Build Connection of type GitHub Enterprise.

Connections for GitHub Enterprise can be created either by following an
intallation process (that requires manual steps in a web browser) or by
providing all the properties of an already-installed application as
arguments to this command.

If the GitHub Enterprise server can only be accessed within a VPC, a
Service Directory service resource can be provided for connecting to it.

**Synopsis:**
```
gcloud builds connections create github-enterprise
    (CONNECTION : --region=REGION) --host-uri=HOST_URI [--async]
    [--app-id=APP_ID --app-slug=APP_SLUG
      --private-key-secret-version=PRIVATE_KEY_SECRET_VERSION
      --webhook-secret-secret-version=WEBHOOK_SECRET_SECRET_VERSION
      : --app-installation-id=APP_INSTALLATION_ID]
    [--service-directory-service=SERVICE_DIRECTORY_SERVICE
      : --ssl-ca-file=SSL_CA_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connection resource - Connection to create. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument connection on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTION
     ID of the connection or fully qualified identifier for the
     connection.

     To set the connection attribute:
     + provide the argument connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Google Cloud region.

     To set the region attribute:
     + provide the argument connection on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property builds/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--host-uri` | HOST_URI |  | URI of the GitHub Enterprise server. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To create a connection by following the installation process, provide only
the connection name and the host URI. If the server can only be accessed
within a VPC, provide also the Service Directory service resource:

    $ gcloud builds connections create github-enterprise my-ghe-conn \
        --project=myproj --region=us-central1 \
        --host-uri=https://my.ghe-server.net \
        --service-directory-service=projects/myproj/namespaces/x/\
    services/mysds

The command will print a URL to be opened in a web browser in order create
and install a GitHub App in that server. After following the URL, you can
get the connection's installation state with The describe command:

    $ gcloud alpha builds connections describe my-ghe-conn \
        --region=us-central1

If the connection's installation state is not COMPLETE yet, it will provide
a link to continue the installation process. Once the connection is in
installation state COMPLETE, repositories can be added to it (see gcloud
alpha builds repositories create).

--

To create a complete connection (e.g. based on an existing installation),
provide all the parameters:

    $ gcloud builds connections create github-enterprise my-ghe-conn \
        --project=myproj --region=us-central1 --app-id=111 \
        --app-slug=gcb-app \
        --service-directory-service=projects/myproj/namespaces/x/\
    services/mysds \
        --private-key-secret-version=projects/myproj/secrets/pk/\
    versions/1 \
        --webhook-secret-secret-version=projects/myproj/secrets/\
    whsecret/versions/1 --app-slug=myapp --app-installation-id=1234

Above command creates the connection in installation state COMPLETE, ready
for adding repositories.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/connections/create/github-enterprise)

---
### `gcloud builds connections create gitlab`

Create a Cloud Build Connection for gitlab.com or GitLab Enterprise

Create a Cloud Build Connection for gitlab.com or GitLab Enterprise.

A gitlab.com or GitLab Enterprise Connection can be created by using a
personal access token with api scope permission. A read_repository scoped
personal access token will also be required on gitlab.com or if the
self-hosted GitLab server doesn't support project access token (GitLab
Enterprise server version < 13.10).

If the GitLab Enterprise server can only be accessed within a VPC, a
Service Directory service resource can be provided for connecting to it.

**Synopsis:**
```
gcloud builds connections create gitlab (CONNECTION : --region=REGION)
    --authorizer-token-secret-version=AUTHORIZER_TOKEN_SECRET_VERSION
    --read-authorizer-token-secret-version=READ_AUTHORIZER_TOKEN_SECRET_VERSION
    --webhook-secret-secret-version=WEBHOOK_SECRET_SECRET_VERSION [--async]
    [--host-uri=HOST_URI]
    [--service-directory-service=SERVICE_DIRECTORY_SERVICE
      : --ssl-ca-file=SSL_CA_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connection resource - Connection to create. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument connection on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTION
     ID of the connection or fully qualified identifier for the
     connection.

     To set the connection attribute:
     + provide the argument connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Google Cloud region.

     To set the region attribute:
     + provide the argument connection on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property builds/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--authorizer-token-secret-version` | AUTHORIZER_TOKEN_SECRET_VERSION |  | Secret containing the api personal access token. |
| `--read-authorizer-token-secret-version` | READ_AUTHORIZER_TOKEN_SECRET_VERSION |  | Secret containing the read_api personal access token. |
| `--webhook-secret-secret-version` | WEBHOOK_SECRET_SECRET_VERSION |  | Secret containing the webhook secret string for validating webhook events sent by GitLab. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--host-uri` | HOST_URI |  | URI of the GitLab instance. |


**Examples:**
```bash
To create a GitLab connection for gitlab.com, provide all the required
parameters:

    $ gcloud builds connections create gitlab my-gitlab-conn \
        --project=myproj --region=us-central1 \
        --read-authorizer-token-secret-version=projects/myproj/secrets/\
    read-pat/versions/1 \
        --authorizer-token-secret-version=projects/myproj/secrets/\
    api-pat/versions/1 \
        --webhook-secret-secret-version=projects/myproj/secrets/\
    whsecret/versions/1

To create a GitLab connection for a GitLab server, provide host-uri
parameter as well:

    $ gcloud builds connections create gitlab my-gle-conn \
        --host-uri=https://my.gle-server.net --project=myproj \
        --region=us-central1 \
        --authorizer-token-secret-version=projects/myproj/secrets/\
    api-pat/versions/1 \
        --read-authorizer-token-secret-version=projects/myproj/secrets/\
    read-pat/versions/1 \
        --webhook-secret-secret-version=projects/myproj/secrets/\
    whsecret/versions/1

To create a GitLab connection for a private GitLab server. provide the
service-directory-service and ssl-ca-file as well:

    $ gcloud builds connections create gitlab my-gle-conn \
        --host-uri=https://my.private-gle-server.net --project=myproj \
        --region=us-central1 \
        --service-directory-service=projects/myproj/namespaces/x/\
    services/mysds --ssl-ca-file=mycertificate.crt \
        --authorizer-token-secret-version=projects/myproj/secrets/\
    api-pat/versions/1 \
        --read-authorizer-token-secret-version=projects/myproj/secrets/\
    read-pat/versions/1 \
        --webhook-secret-secret-version=projects/myproj/secrets/\
    whsecret/versions/1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/connections/create/gitlab)

---

## `gcloud builds connections update` — update Connections in Google Cloud Build
### `gcloud builds connections update bitbucket-cloud`

Update a Cloud Build Connection of type Bitbucket Cloud

Update a Cloud Build Connection of type Bitbucket Cloud.

**Synopsis:**
```
gcloud builds connections update bitbucket-cloud
    (CONNECTION : --region=REGION) [--async]
    [--authorizer-token-secret-version=AUTHORIZER_TOKEN_SECRET_VERSION]
    [--read-authorizer-token-secret-version=READ_AUTHORIZER_TOKEN_SECRET_VERSION]
    [--webhook-secret-secret-version=WEBHOOK_SECRET_SECRET_VERSION]
    [--workspace=WORKSPACE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connection resource - Connection to update. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument connection on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTION
     ID of the connection or fully qualified identifier for the
     connection.

     To set the connection attribute:
     + provide the argument connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Google Cloud region.

     To set the region attribute:
     + provide the argument connection on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property builds/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--authorizer-token-secret-version` | AUTHORIZER_TOKEN_SECRET_VERSION |  | Secret containing the repository_read,repository_admin, pullrequest_read, webhook access token. It can be a repository, project or workspace access token. |
| `--read-authorizer-token-secret-version` | READ_AUTHORIZER_TOKEN_SECRET_VERSION |  | Secret containing the repository_read access token. It can be a repository, project or workspace access token. |
| `--webhook-secret-secret-version` | WEBHOOK_SECRET_SECRET_VERSION |  | Secret containing the webhook secret string for validating webhook events sent by Bitbucket Cloud. |
| `--workspace` | WORKSPACE |  | Workspace of the Bitbucket Cloud instance. |


**Examples:**
```bash
To update the workspace, provide the connection name and the workspace
name:

    $ gcloud builds connections update bitbucket-cloud my-bbc-conn \
        --region=us-west1 --workspace=my-workspace

To update the authorization token, provide the connection name and the new
authorization token        secret version.

    $ gcloud builds connections update bitbucket-cloud my-bbc-conn \
        --region=us-west1 \
        --authorizer-token-secret-version=projects/myproj/secrets/\
    admin-pat/versions/1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/connections/update/bitbucket-cloud)

---
### `gcloud builds connections update bitbucket-data-center`

Update a Cloud Build Connection of type Bitbucket Data Center

Update a Cloud Build Connection of type Bitbucket Data Center.

**Synopsis:**
```
gcloud builds connections update bitbucket-data-center
    (CONNECTION : --region=REGION) [--async]
    [--authorizer-token-secret-version=AUTHORIZER_TOKEN_SECRET_VERSION]
    [--host-uri=HOST_URI]
    [--read-authorizer-token-secret-version=READ_AUTHORIZER_TOKEN_SECRET_VERSION]
    [--service-directory-service=SERVICE_DIRECTORY_SERVICE]
    [--ssl-ca-file=SSL_CA_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connection resource - Connection to update. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument connection on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTION
     ID of the connection or fully qualified identifier for the
     connection.

     To set the connection attribute:
     + provide the argument connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Google Cloud region.

     To set the region attribute:
     + provide the argument connection on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property builds/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--authorizer-token-secret-version` | AUTHORIZER_TOKEN_SECRET_VERSION |  | Secret containing the REPO_ADMIN personal access token. |
| `--host-uri` | HOST_URI |  | URI of the Bitbucket Data Center instance. |
| `--read-authorizer-token-secret-version` | READ_AUTHORIZER_TOKEN_SECRET_VERSION |  | Secret containing the REPO_READ personal access token. |
| `--service-directory-service` | SERVICE_DIRECTORY_SERVICE |  | Service Directory service resource to use for accessing the Bitbucket Data Center. Necessary only if the server has no public access from the internet. |
| `--ssl-ca-file` | SSL_CA_FILE |  | File containing the SSL_CA to be used. |


**Examples:**
```bash
To update the ssl_ca, provide the connection name and the ssl_ca file:

    $ gcloud builds connections update bitbucket-data-center \
        my-gle-conn --region=us-west1 --ssl-ca-file=mycertificate.crt

To update the authorization token, provide the connection name and the new
authorization token secret version name.

    $ gcloud builds connections update bitbucket-data-center \
        my-gle-conn --region=us-west1 \
        --authorizer-token-secret-version=projects/myproj/secrets/\
    admin-pat/versions/1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/connections/update/bitbucket-data-center)

---
### `gcloud builds connections update github`

Update a Cloud Build Connection of type GitHub

Update a Cloud Build Connection of type GitHub (for github.com).

**Synopsis:**
```
gcloud builds connections update github (CONNECTION : --region=REGION)
    [--app-installation-id=APP_INSTALLATION_ID] [--async]
    [--authorizer-token-secret-version=AUTHORIZER_TOKEN_SECRET_VERSION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connection resource - Connection to update. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument connection on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTION
     ID of the connection or fully qualified identifier for the
     connection.

     To set the connection attribute:
     + provide the argument connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Google Cloud region.

     To set the region attribute:
     + provide the argument connection on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property builds/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--app-installation-id` | APP_INSTALLATION_ID |  | Installation ID of the Cloud Build GitHub App. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--authorizer-token-secret-version` | AUTHORIZER_TOKEN_SECRET_VERSION |  | Secret containing the authorizer user's token. |


**Examples:**
```bash
To update the authorizer token, provide the connection name and the
authorizer token secret:

    $ gcloud builds connections update github myconn \
        --region=us-central1 \
        --authorizer-token-secret-version=projects/myproj/secrets/\
    mytoken/versions/1

To update the installation id, provide the connection name and the
installation id of the Cloud Build GitHub app.

    $ gcloud builds connections update github myconn \
        --region=us-central1 --app-installation-id=1234
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/connections/update/github)

---
### `gcloud builds connections update github-enterprise`

Update a Cloud Build Connection of type GitHub Enterprise

Update a Cloud Build Connection of type GitHub Enterprise.

**Synopsis:**
```
gcloud builds connections update github-enterprise
    (CONNECTION : --region=REGION) [--app-id=APP_ID]
    [--app-installation-id=APP_INSTALLATION_ID] [--app-slug=APP_SLUG]
    [--async] [--host-uri=HOST_URI]
    [--private-key-secret-version=PRIVATE_KEY_SECRET_VERSION]
    [--service-directory-service=SERVICE_DIRECTORY_SERVICE]
    [--ssl-ca-file=SSL_CA_FILE]
    [--webhook-secret-secret-version=WEBHOOK_SECRET_SECRET_VERSION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connection resource - Connection to update. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument connection on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTION
     ID of the connection or fully qualified identifier for the
     connection.

     To set the connection attribute:
     + provide the argument connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Google Cloud region.

     To set the region attribute:
     + provide the argument connection on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property builds/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--app-id` | APP_ID |  | App ID of the GitHub App in the GitHub Enterprise server. |
| `--app-installation-id` | APP_INSTALLATION_ID |  | Installation ID of the Cloud Build GitHub App. |
| `--app-slug` | APP_SLUG |  | App slug (url-friendly name) of the GitHub App. When seeing the configuration page of the App (e.g. in https://my-ghe-server.net/settings/apps/my-app), the app-slug is the last component of the URL path ("my-app" in that example). |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--host-uri` | HOST_URI |  | URI of the GitHub Enterprise server. |
| `--private-key-secret-version` | PRIVATE_KEY_SECRET_VERSION |  | Secret containing the private key of the GitHub App. |
| `--service-directory-service` | SERVICE_DIRECTORY_SERVICE |  | Service Directory service resource to use for accessing the GitHub Enterprise Server. Necessary only if the server has no public access from the internet. |
| `--ssl-ca-file` | SSL_CA_FILE |  | File containing the SSL_CA to be used. |
| `--webhook-secret-secret-version` | WEBHOOK_SECRET_SECRET_VERSION |  | Secret containing the webhook secret string for validating webhook events generated by the GitHub App. |


**Examples:**
```bash
To update the ssl_ca, provide the connection name and the ssl_ca file:

    $ gcloud builds connections update github-enterprise my-ghe-conn \
        --region=us-west1 --ssl-ca-file=mycertificate.crt

To update the installation id, provide the connection name and the
installation id of the Cloud Build GitHub app.

    $ gcloud builds connections update github-enterprise my-ghe-conn \
        --region=us-west1 --app-installation-id=1234
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/connections/update/github-enterprise)

---
### `gcloud builds connections update gitlab`

Update a Cloud Build Connection of type gitlab.com or GitLab Enterprise

Update a Cloud Build Connection of type gitlab.com or GitLab Enterprise.

**Synopsis:**
```
gcloud builds connections update gitlab (CONNECTION : --region=REGION)
    [--async]
    [--authorizer-token-secret-version=AUTHORIZER_TOKEN_SECRET_VERSION]
    [--host-uri=HOST_URI]
    [--read-authorizer-token-secret-version=READ_AUTHORIZER_TOKEN_SECRET_VERSION]
    [--service-directory-service=SERVICE_DIRECTORY_SERVICE]
    [--ssl-ca-file=SSL_CA_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connection resource - Connection to update. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument connection on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTION
     ID of the connection or fully qualified identifier for the
     connection.

     To set the connection attribute:
     + provide the argument connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Google Cloud region.

     To set the region attribute:
     + provide the argument connection on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property builds/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--authorizer-token-secret-version` | AUTHORIZER_TOKEN_SECRET_VERSION |  | Secret containing the api personal access token. |
| `--host-uri` | HOST_URI |  | URI of the GitLab instance. |
| `--read-authorizer-token-secret-version` | READ_AUTHORIZER_TOKEN_SECRET_VERSION |  | Secret containing the read_repository personal access token. Required for GitLab Enterprise versions older than 13.10. |
| `--service-directory-service` | SERVICE_DIRECTORY_SERVICE |  | Service Directory service resource to use for accessing the GitLab Enterprise Server. Necessary only if the server has no public access from the internet. |
| `--ssl-ca-file` | SSL_CA_FILE |  | File containing the SSL_CA to be used. |


**Examples:**
```bash
To update the ssl_ca, provide the connection name and the ssl_ca file:

    $ gcloud builds connections update gitlab my-gle-conn \
        --region=us-west1 --ssl-ca-file=mycertificate.crt

To update the authorization token, provide the connection name and the new
authorization token        secret version.

    $ gcloud builds connections update gitlab my-gle-conn \
        --region=us-west1 \
        --authorizer-token-secret-version=projects/myproj/secrets/\
    api-pat/versions/1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/connections/update/gitlab)

---
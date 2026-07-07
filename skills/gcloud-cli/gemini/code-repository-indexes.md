# gcloud gemini code-repository-indexes

manage Code Repository Index resources

### `gcloud gemini code-repository-indexes create`

Create a code repository index instance

Create a code repository index instance.

The instance will be created in the specified project and location.

**Synopsis:**
```
gcloud gemini code-repository-indexes create
    (CODE_REPOSITORY_INDEX : --location=LOCATION) [--async]
    [--kms-key=KMS_KEY] [--labels=[LABELS,...]] [--request-id=REQUEST_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CodeRepositoryIndex resource - Identifier. name of resource The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument code_repository_index on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CODE_REPOSITORY_INDEX
     ID of the codeRepositoryIndex or fully qualified identifier for the
     codeRepositoryIndex.

     To set the code_repository_index attribute:
     + provide the argument code_repository_index on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the codeRepositoryIndex resource.

     To set the location attribute:
     + provide the argument code_repository_index on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--kms-key` | KMS_KEY |  | Customer-managed encryption key name, in the format projects/*/locations/*/keyRings/*/cryptoKeys/*. |
| `--labels` | [LABELS,...] |  | Labels as key value pairs. KEY Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. VALUE Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Shorthand Example: --labels=string=string JSON Example: --labels='{"string": "string"}' File Example: --labels=path_to_file.(yaml\|json) |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes since the first request. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To create a code repository index instance my-instance in project
my-project and location us-central1, run:

    $ gcloud gemini code-repository-indexes create my-instance \
        --project=my-project --location=us-central1

To create a code repository index instance my-instance in project
my-project, location us-central1 with your managed encryption key run:

    $ gcloud gemini code-repository-indexes create my-instance \
        --project=my-project --location=us-central1 \
        --kms-key=projects/*/locations/*/keyRings/*/cryptoKeys/*

Note: --kms-key can be only passed during index creation and can not be
used during update.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/code-repository-indexes/create)

---
### `gcloud gemini code-repository-indexes delete`

Delete a code repository index instance

Delete a code repository index instance.

**Synopsis:**
```
gcloud gemini code-repository-indexes delete
    (CODE_REPOSITORY_INDEX : --location=LOCATION) [--async] [--force]
    [--request-id=REQUEST_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CodeRepositoryIndex resource - Name of the resource The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument code_repository_index on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CODE_REPOSITORY_INDEX
     ID of the codeRepositoryIndex or fully qualified identifier for the
     codeRepositoryIndex.

     To set the code_repository_index attribute:
     + provide the argument code_repository_index on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the codeRepositoryIndex resource.

     To set the location attribute:
     + provide the argument code_repository_index on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--force` |  |  | If set to true, any RepositoryGroups from this CodeRepositoryIndex will also be deleted. (Otherwise, the request will only work if the CodeRepositoryIndex has no RepositoryGroups.) |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes after the first request. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To delete code repository index instance my-instance in project my-project
and location us-central1, run:

    $ gcloud gemini code-repository-indexes delete my-instance \
        --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/code-repository-indexes/delete)

---
### `gcloud gemini code-repository-indexes describe`

Get details of a code repository index instance

Get details of a code repository index instance.

**Synopsis:**
```
gcloud gemini code-repository-indexes describe
    (CODE_REPOSITORY_INDEX : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CodeRepositoryIndex resource - Name of the resource The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument code_repository_index on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CODE_REPOSITORY_INDEX
     ID of the codeRepositoryIndex or fully qualified identifier for the
     codeRepositoryIndex.

     To set the code_repository_index attribute:
     + provide the argument code_repository_index on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the codeRepositoryIndex resource.

     To set the location attribute:
     + provide the argument code_repository_index on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To get the details of code repository index instance my-instance in project
my-project and location us-central, run:

    $ gcloud gemini code-repository-indexes describe my-instance \
        --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/code-repository-indexes/describe)

---
### `gcloud gemini code-repository-indexes list`

List all code repository index instances in a specified project and location

List all code repository index instances in a specified project and
location.

**Synopsis:**
```
gcloud gemini code-repository-indexes list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all code repository index instances in project my-project and
location us-central, run:

    $ gcloud gemini code-repository-indexes list --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/code-repository-indexes/list)

---
### `gcloud gemini code-repository-indexes update`

Update the configuration of a code repository index instance

Update the configuration of a code repository index instance.

**Synopsis:**
```
gcloud gemini code-repository-indexes update
    (CODE_REPOSITORY_INDEX : --location=LOCATION) [--async]
    [--request-id=REQUEST_ID]
    [--labels=[LABELS,...]
      | --update-labels=[UPDATE_LABELS,...] --clear-labels
      | --remove-labels=REMOVE_LABELS] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CodeRepositoryIndex resource - Identifier. name of resource The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument code_repository_index on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CODE_REPOSITORY_INDEX
     ID of the codeRepositoryIndex or fully qualified identifier for the
     codeRepositoryIndex.

     To set the code_repository_index attribute:
     + provide the argument code_repository_index on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the codeRepositoryIndex resource.

     To set the location attribute:
     + provide the argument code_repository_index on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes since the first request. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To update code repository index instance my-instance in project my-project
and location us-central1 with new labels, run:

    $ gcloud gemini code-repository-indexes update `my-instance` \
        --project=my-project --location=us-central1 \
        --labels='{"my_label": "my_value"}'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/code-repository-indexes/update)

---

## `gcloud gemini code-repository-indexes repository-groups` — manage Repository Group resources
### `gcloud gemini code-repository-indexes repository-groups create`

Create a repository group for a given code repository index instance

Create a repository group for a given code repository index instance.

**Synopsis:**
```
gcloud gemini code-repository-indexes repository-groups create
    (REPOSITORY_GROUP
      : --code-repository-index=CODE_REPOSITORY_INDEX --location=LOCATION)
    [--async] [--labels=[LABELS,...]]
    [--repositories=[branchPattern=BRANCHPATTERN],[resource=RESOURCE]]
    [--request-id=REQUEST_ID]
    [--resources=[authConfig=AUTHCONFIG],
      [connection=CONNECTION],[sourceConfig=SOURCECONFIG],[type=TYPE]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RepositoryGroup resource - Identifier. name of resource The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument repository_group on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  REPOSITORY_GROUP
     ID of the repositoryGroup or fully qualified identifier for the
     repositoryGroup.

     To set the repository_group attribute:
     + provide the argument repository_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --code-repository-index=CODE_REPOSITORY_INDEX
     The codeRepositoryIndex id of the repositoryGroup resource.

     To set the code-repository-index attribute:
     + provide the argument repository_group on the command line with a
       fully specified name;
     + provide the argument --code-repository-index on the command line.

  --location=LOCATION
     The location id of the repositoryGroup resource.

     To set the location attribute:
     + provide the argument repository_group on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--labels` | [LABELS,...] |  | Labels as key value pairs. KEY Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. VALUE Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Shorthand Example: --labels=string=string JSON Example: --labels='{"string": "string"}' File Example: --labels=path_to_file.(yaml\|json) |
| `--repositories` | [branchPattern=BRANCHPATTERN],[resource=RESOURCE] |  | List of repositories to group. branchPattern The Git branch pattern used for indexing in RE2 syntax. See https://github.com/google/re2/wiki/syntax for syntax. resource The DeveloperConnect repository full resource name, relative resource name or resource URL to be indexed. Shorthand Example: --repositories=branchPattern=string,resource=string --repositories=branchPattern=string,resource=string JSON Example: --repositories='[{"branchPattern": "string", "resource": "string"}]' File Example: --repositories=path_to_file.(yaml\|json) |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes since the first request. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |
| `--resources` | [authConfig=AUTHCONFIG],[connection=CONNECTION],[sourceConfig=SOURCECONFIG],[type=TYPE] |  | List of third party connection resources. authConfig The authentication configuration for the resource. apiToken API Token based authentication. tokenSecretResource The secret key for the API token. Example: projects/<project>/secrets/<secret>/versions/<version>. username The username for the API token. connection The DeveloperConnect connection full resource name, relative resource name or resource URL to be indexed. sourceConfig The source configuration for the resource. confluenceConfig Confluence source configuration. pageId The optional page ID of the Confluence page. spaceKey The space key of the Confluence space. uri The host address of the Confluence instance. type The type of the 3p resource. Shorthand Example: --resources=authConfig={apiToken={tokenSecretResource=string,username=string}},connection=string,sourceConfig={confluenceConfig={pageId=string,spaceKey=string,uri=string}},type=string --resources=authConfig={apiToken={tokenSecretResource=string,username=string}},connection=string,sourceConfig={confluenceConfig={pageId=string,spaceKey=string,uri=string}},type=string JSON Example: --resources='[{"authConfig": {"apiToken": {"tokenSecretResource": "string", "username": "string"}}, "connection": "string", "sourceConfig": {"confluenceConfig": {"pageId": "string", "spaceKey": "string", "uri": "string"}}, "type": "string"}]' File Example: --resources=path_to_file.(yaml\|json) |


**Examples:**
```bash
To create a repository group my-repository-group for a code repository
index instance my-instance in project my-project and location us-central1
with one Developer Connect repository and branch pattern .*, run:

    $ gcloud gemini code-repository-indexes repository-groups create \
        my-repository-group --code-repository-index=my-instance \
        --project=my-project --location=us-central1 \
        --repositories=branchPattern=.*,\
    resource=developerconnect.googleapis.com/projects/<PROJECT>/\
    locations/<LOCATION>/connections/<CONNECTION>/gitRepositoryLinks/\
    <REPOSITORY>

Developer Connect Git repository resource must already exist. Refer to
Developer Connect documentation
(http://cloud.google.com/developer-connect/docs/connect-repo) for more
details.

To create a repository group my-repository-group for a code repository
index instance my-instance in project my-project and location us-central1
with a fully qualified name, run:

    $ gcloud gemini code-repository-indexes repository-groups create \
        projects/my-project/locations/us-central1/\
    codeRepositoryIndexes/my-instance/repositoryGroups/\
    my-repository-group \
        --repositories=branchPattern=.*,\
    resource=developerconnect.googleapis.com/projects/<PROJECT>/\
    locations/<LOCATION>/connections/<CONNECTION>/gitRepositoryLinks/\
    <REPOSITORY>

Developer Connect Git repository resource must already exist. Refer to
Developer Connect documentation
(http://cloud.google.com/developer-connect/docs/connect-repo) for more
details.

To create a repository group my-repository-group for a code repository
index instance my-instance in project my-project and location us-central1
with Developer Connect repositories defined in a separate file, run:

    $ gcloud gemini code-repository-indexes repository-groups create \
        my-repository-group --code-repository-index=my-instance \
        --project=my-project --location=us-central1 \
        --repositories=@/path/to/repositories.json

Developer Connect Git repository resource must already exist. Refer to
Developer Connect documentation
(http://cloud.google.com/developer-connect/docs/connect-repo) for more
details.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/code-repository-indexes/repository-groups/create)

---
### `gcloud gemini code-repository-indexes repository-groups delete`

Delete a repository group from a given code repository index instance

Delete a repository group from a given code repository index instance.

**Synopsis:**
```
gcloud gemini code-repository-indexes repository-groups delete
    (REPOSITORY_GROUP
      : --code-repository-index=CODE_REPOSITORY_INDEX --location=LOCATION)
    [--async] [--request-id=REQUEST_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RepositoryGroup resource - Name of the resource The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument repository_group on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  REPOSITORY_GROUP
     ID of the repositoryGroup or fully qualified identifier for the
     repositoryGroup.

     To set the repository_group attribute:
     + provide the argument repository_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --code-repository-index=CODE_REPOSITORY_INDEX
     The codeRepositoryIndex id of the repositoryGroup resource.

     To set the code-repository-index attribute:
     + provide the argument repository_group on the command line with a
       fully specified name;
     + provide the argument --code-repository-index on the command line.

  --location=LOCATION
     The location id of the repositoryGroup resource.

     To set the location attribute:
     + provide the argument repository_group on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes after the first request. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To delete a repository group my-repository-group from a code repository
index instance my-instance in project my-project and location us-central1
with a fully qualified name, run:

    $ gcloud gemini code-repository-indexes repository-groups delete \
        my-repository-group --code-repository-index=my-instance \
        --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/code-repository-indexes/repository-groups/delete)

---
### `gcloud gemini code-repository-indexes repository-groups describe`

Get details of a code repository index instance

Get details of a code repository index instance.

**Synopsis:**
```
gcloud gemini code-repository-indexes repository-groups describe
    (REPOSITORY_GROUP
      : --code-repository-index=CODE_REPOSITORY_INDEX --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RepositoryGroup resource - Name of the resource The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument repository_group on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  REPOSITORY_GROUP
     ID of the repositoryGroup or fully qualified identifier for the
     repositoryGroup.

     To set the repository_group attribute:
     + provide the argument repository_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --code-repository-index=CODE_REPOSITORY_INDEX
     The codeRepositoryIndex id of the repositoryGroup resource.

     To set the code-repository-index attribute:
     + provide the argument repository_group on the command line with a
       fully specified name;
     + provide the argument --code-repository-index on the command line.

  --location=LOCATION
     The location id of the repositoryGroup resource.

     To set the location attribute:
     + provide the argument repository_group on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To get the details of repository group my-repository-group of a code
repository index instance my-instance in project my-project and location
us-central1, run:

    $ gcloud gemini code-repository-indexes repository-groups describe \
        my-repository-group --code-repository-index=my-instance \
        --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/code-repository-indexes/repository-groups/describe)

---
### `gcloud gemini code-repository-indexes repository-groups get-iam-policy`

Get the IAM policy for a code repository index repository group

gcloud gemini code-repository-indexes repository-groups get-iam-policy
displays the IAM policy associated with a code repository index repository
group. If formatted as JSON, the output can be edited and used as a policy
file for set-iam-policy. The output includes an "etag" field identifying
the version emitted and allowing detection of concurrent policy updates;
see $ gcloud gemini code-repository-indexes repository-groups
set-iam-policy for additional details.

**Synopsis:**
```
gcloud gemini code-repository-indexes repository-groups get-iam-policy
    (REPOSITORY_GROUP
      : --code-repository-index=CODE_REPOSITORY_INDEX --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Repository group resource - The repository group for which to display the
IAM policy. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument repository_group on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  REPOSITORY_GROUP
     ID of the repository_group or fully qualified identifier for the
     repository_group.

     To set the repository_group attribute:
     + provide the argument repository_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --code-repository-index=CODE_REPOSITORY_INDEX
     ID of the code repository index resource.

     To set the code-repository-index attribute:
     + provide the argument repository_group on the command line with a
       fully specified name;
     + provide the argument --code-repository-index on the command line.

  --location=LOCATION
     Location of the Gemini resource.

     To set the location attribute:
     + provide the argument repository_group on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To print the IAM policy for a target my-repository-group, run:

    $ gcloud gemini code-repository-indexes repository-groups \
        get-iam-policy my-repository-group --region=us-central1 \
        --code-repository-index=my-index
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/code-repository-indexes/repository-groups/get-iam-policy)

---
### `gcloud gemini code-repository-indexes repository-groups list`

List all repository group for a given code repository index instance

List all repository group for a given code repository index instance.

**Synopsis:**
```
gcloud gemini code-repository-indexes repository-groups list
    (--code-repository-index=CODE_REPOSITORY_INDEX : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--code-repository-index` | CODE_REPOSITORY_INDEX |  | _[This must be specified.]_ ID of the codeRepositoryIndex or fully qualified identifier for the codeRepositoryIndex. To set the code-repository-index attribute: + provide the argument --code-repository-index on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The location id of the codeRepositoryIndex resource. To set the location attribute: + provide the argument --code-repository-index on the command line with a fully specified name; + provide the argument --location on the command line. |


**Examples:**
```bash
To list all repository groups of a code repository index instance
my-instance in project my-project and location us-central1, run:

    $ gcloud gemini code-repository-indexes repository-groups list \
        --code-repository-index=my-instance --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/code-repository-indexes/repository-groups/list)

---
### `gcloud gemini code-repository-indexes repository-groups set-iam-policy`

Get the IAM policy for a code repository index repository group

gcloud gemini code-repository-indexes repository-groups set-iam-policy sets
the IAM policy for a code repository index repository group as defined in a
JSON or YAML file.

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud gemini code-repository-indexes repository-groups set-iam-policy
    (REPOSITORY_GROUP
      : --code-repository-index=CODE_REPOSITORY_INDEX --location=LOCATION)
    POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Repository group resource - The repository group for which to set the IAM
policy. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument repository_group on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  REPOSITORY_GROUP
     ID of the repository_group or fully qualified identifier for the
     repository_group.

     To set the repository_group attribute:
     + provide the argument repository_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --code-repository-index=CODE_REPOSITORY_INDEX
     ID of the code repository index resource.

     To set the code-repository-index attribute:
     + provide the argument repository_group on the command line with a
       fully specified name;
     + provide the argument --code-repository-index on the command line.

  --location=LOCATION
     Location of the Gemini resource.

     To set the location attribute:
     + provide the argument repository_group on the command line with a
       fully specified name;
     + provide the argument --location on the command line.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command will read an IAM policy defined in a JSON file
'policy.json' and set it for the repository group named
'my-repository-group':

    $ gcloud gemini code-repository-indexes repository-groups \
        set-iam-policy my-repository-group policy.json \
        --region=us-central1 --code-repository-index=my-index
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/code-repository-indexes/repository-groups/set-iam-policy)

---
### `gcloud gemini code-repository-indexes repository-groups update`

Update the configuration of a repository group

Update the configuration of a repository group.

**Synopsis:**
```
gcloud gemini code-repository-indexes repository-groups update
    (REPOSITORY_GROUP
      : --code-repository-index=CODE_REPOSITORY_INDEX --location=LOCATION)
    [--async] [--request-id=REQUEST_ID]
    [--labels=[LABELS,...]
      | --update-labels=[UPDATE_LABELS,...] --clear-labels
      | --remove-labels=REMOVE_LABELS]
    [--repositories=[branchPattern=BRANCHPATTERN],[resource=RESOURCE]
      | --add-repositories=[branchPattern=BRANCHPATTERN],
      [resource=RESOURCE] --clear-repositories
      | --remove-repositories=[branchPattern=BRANCHPATTERN],
      [resource=RESOURCE]]
    [--resources=[authConfig=AUTHCONFIG],
      [connection=CONNECTION],[sourceConfig=SOURCECONFIG],[type=TYPE]
      | --add-resources=[authConfig=AUTHCONFIG],
      [connection=CONNECTION],[sourceConfig=SOURCECONFIG],[type=TYPE]
      --clear-resources
      | --remove-resources=[authConfig=AUTHCONFIG],
      [connection=CONNECTION],[sourceConfig=SOURCECONFIG],[type=TYPE]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RepositoryGroup resource - Identifier. name of resource The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument repository_group on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  REPOSITORY_GROUP
     ID of the repositoryGroup or fully qualified identifier for the
     repositoryGroup.

     To set the repository_group attribute:
     + provide the argument repository_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --code-repository-index=CODE_REPOSITORY_INDEX
     The codeRepositoryIndex id of the repositoryGroup resource.

     To set the code-repository-index attribute:
     + provide the argument repository_group on the command line with a
       fully specified name;
     + provide the argument --code-repository-index on the command line.

  --location=LOCATION
     The location id of the repositoryGroup resource.

     To set the location attribute:
     + provide the argument repository_group on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes since the first request. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To update repository group my-repository-group of code repository index
instance my-instance in project my-project and location us-central1 with a
new branch pattern for one of the Git repositories, run:

    $ gcloud gemini code-repository-indexes repository-groups update \
        my-repository-group --code-repository-index=my-instance \
        --project=my-project --location=us-central1 \
        --repositories=branchPattern=new_branch,\
    resource=developerconnect.googleapis.com/projects/<PROJECT>/\
    locations/<LOCATION>/connections/<CONNECTION>/gitRepositoryLinks/\
    <REPOSITORY>
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/gemini/code-repository-indexes/repository-groups/update)

---
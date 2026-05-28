# gcloud artifacts repositories

manage Artifact Registry repositories

### `gcloud artifacts repositories add-iam-policy-binding`

Add an IAM policy binding to the IAM policy of an Artifact Registry repository

gcloud artifacts repositories add-iam-policy-binding adds an IAM policy
binding to the IAM policy of an Artifact Registry repository. One binding
consists of a member, a role, and an optional condition.

This command can fail for the following reasons:
  o The repository specified does not exist.
  o The active account does not have permission to access the given
    repository's IAM policies.

**Synopsis:**
```
gcloud artifacts repositories add-iam-policy-binding
    (REPOSITORY : --location=LOCATION) --member=PRINCIPAL --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Repository resource - Name of the Artifact Registry repository. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

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

  --location=LOCATION
     Location of the repository. Overrides the default artifacts/location
     property value for this command invocation. To configure the default
     location, use the command: gcloud config set artifacts/location.

     To set the location attribute:
     + provide the argument repository on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property artifacts/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--condition` | [KEY=VALUE,...] |  | _[At most one of these can be specified:]_ A condition to include in the binding. When the condition is explicitly specified as None (--condition=None), a binding without a condition is added. When the condition is specified and is not None, --role cannot be a basic role. Basic roles are roles/editor, roles/owner, and roles/viewer. For more on conditions, refer to the conditions overview guide: https://cloud.google.com/iam/docs/conditions-overview When using the --condition flag, include the following key-value pairs: expression (Required) Condition expression that evaluates to True or False. This uses a subset of Common Expression Language syntax. If the condition expression includes a comma, use a different delimiter to separate the key-value pairs. Specify the delimiter before listing the key-value pairs. For example, to specify a colon (:) as the delimiter, do the following: --condition=^:^title=TITLE:expression=EXPRESSION. For more information, see https://cloud.google.com/sdk/gcloud/reference/topic/escaping. title (Required) A short string describing the purpose of the expression. description (Optional) Additional description for the expression. |
| `--condition-from-file` | PATH_TO_FILE |  | _[At most one of these can be specified:]_ Path to a local JSON or YAML file that defines the condition. To see available fields, see the help for --condition. Use a full or relative path to a local file containing the value of condition. |


**Examples:**
```bash
To add an IAM policy binding for the role of 'roles/editor' for the user
'test-user@gmail.com' with repository 'my-repo', run:

    $ gcloud artifacts repositories add-iam-policy-binding my-repo \
        --member='user:test-user@gmail.com' --role='roles/editor'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/repositories/add-iam-policy-binding)

---
### `gcloud artifacts repositories create`

Create an Artifact Registry repository

Create a new Artifact Registry repository.

This command can fail for the following reasons:
  o A repository with the same name already exists.
  o The active account does not have permission to create repositories.
  o A valid repository format was not provided.

**Synopsis:**
```
gcloud artifacts repositories create (REPOSITORY : --location=LOCATION)
    --repository-format=REPOSITORY_FORMAT [--allow-snapshot-overwrites]
    [--async] [--description=DESCRIPTION] [--disable-remote-validation]
    [--immutable-tags] [--kms-key=KMS_KEY] [--labels=[KEY=VALUE,...]]
    [--mode=MODE; default="NONE"] [--remote-apt-repo=REMOTE_APT_REPO]
    [--remote-apt-repo-path=REMOTE_APT_REPO_PATH]
    [--remote-docker-repo=REMOTE_DOCKER_REPO]
    [--remote-go-repo=REMOTE_GO_REPO] [--remote-mvn-repo=REMOTE_MVN_REPO]
    [--remote-npm-repo=REMOTE_NPM_REPO]
    [--remote-password-secret-version=REMOTE_PASSWORD_SECRET_VERSION]
    [--remote-python-repo=REMOTE_PYTHON_REPO]
    [--remote-repo-config-desc=REMOTE_REPO_CONFIG_DESC]
    [--remote-username=REMOTE_USERNAME] [--remote-yum-repo=REMOTE_YUM_REPO]
    [--remote-yum-repo-path=REMOTE_YUM_REPO_PATH]
    [--upstream-policy-file=FILE] [--version-policy=VERSION_POLICY]
    [--allow-vulnerability-scanning | --disable-vulnerability-scanning]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Repository resource - The Artifact Registry repository to create. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

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

  --location=LOCATION
     Location of the repository. Overrides the default artifacts/location
     property value for this command invocation. To configure the default
     location, use the command: gcloud config set artifacts/location.

     To set the location attribute:
     + provide the argument repository on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property artifacts/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--repository-format` | one of: apt APT package format |  | Format of the repository. REPOSITORY_FORMAT must be one of: apt APT package format. docker Docker image format. go Go module format. kfp KFP package format. maven Maven package format. npm NPM package format. python Python package format. yum YUM package format. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allow-snapshot-overwrites` |  |  | (Maven only) Allow repository users to publish a snapshot that overwrites the same snapshot version in the repository. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Description for the repository. |
| `--disable-remote-validation` |  |  | Do not make an HTTP request to validate the remote upstream. Not recommended when setting a custom remote upstream unless you are absolutely sure your upstream URI and any auth is valid. |
| `--immutable-tags` |  |  | (Docker only) Prevent changes to tagged images in the repository. Tags cannot be deleted or moved to a different image digest, and tagged images cannot be deleted. |
| `--kms-key` | KMS_KEY |  | Name of the encryption key that's used for encrypting the contents of the repository. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--mode` | one of: none Repository mode not specified | NONE | Mode is the type of the repository - Standard, Virtual or Remote. MODE must be one of: none Repository mode not specified. remote-repository Remote repository mode - fetches data from upstream and caches it. standard-repository Standard repository mode - should be possible to write/read data to this repo. virtual-repository Virtual repository mode - aggregates data from several upstreams. |
| `--remote-apt-repo` | one of: [debian, debian-snapshot, ubuntu] |  | (Apt only) Repository base for apt remote repository. REMOTE_APT_REPO must be one of: [debian, debian-snapshot, ubuntu]. |
| `--remote-apt-repo-path` | REMOTE_APT_REPO_PATH |  | (Apt only) Remaining URL path to apt remote repository. |
| `--remote-docker-repo` | REMOTE_DOCKER_REPO |  | (Docker only) Repo upstream for docker remote repository. REMOTE_DOCKER_REPO can be either: * one of the following enums: [docker-hub]. * an http/https custom registry uri (ex: https://my.docker.registry) |
| `--remote-go-repo` | REMOTE_GO_REPO |  | (Go only) Repo upstream for Go remote repository. "https://proxy.golang.org/" is the only valid value. |
| `--remote-mvn-repo` | REMOTE_MVN_REPO |  | (Maven only) Repo upstream for maven remote repository. REMOTE_MVN_REPO can be either: * one of the following enums: [maven-central]. * an http/https custom registry uri (ex: https://my.maven.registry) |
| `--remote-npm-repo` | REMOTE_NPM_REPO |  | (Npm only) Repo upstream for npm remote repository. REMOTE_NPM_REPO can be either: * one of the following enums: [npmjs]. * an http/https custom registry uri (ex: https://my.npm.registry) |
| `--remote-password-secret-version` | REMOTE_PASSWORD_SECRET_VERSION |  | Secret Manager secret version that contains password for the remote repository upstream. |
| `--remote-python-repo` | REMOTE_PYTHON_REPO |  | (Python only) Repo upstream for python remote repository. REMOTE_PYTHON_REPO can be either: * one of the following enums: [pypi]. * an http/https custom registry uri (ex: https://my.python.registry) |
| `--remote-repo-config-desc` | REMOTE_REPO_CONFIG_DESC |  | The description for the remote repository config. |
| `--remote-username` | REMOTE_USERNAME |  | Remote Repository upstream registry username. |
| `--remote-yum-repo` | one of: [centos, centos-debug, centos-stream, centos-vault, epel, rocky] |  | (Yum only) Repository base for yum remote repository. REMOTE_YUM_REPO must be one of: [centos, centos-debug, centos-stream, centos-vault, epel, rocky]. |
| `--remote-yum-repo-path` | REMOTE_YUM_REPO_PATH |  | (Yum only) Remaining URL path to yum remote repository. |
| `--upstream-policy-file` | FILE |  | (Virtual Repositories only) is the upstreams for the Virtual Repository. Example of the file contents: [ { "id": "test1", "repository": "projects/p1/locations/us-central1/repositories/repo1", "priority": 1 }, { "id": "test2", "repository": "projects/p2/locations/us-west2/repositories/repo2", "priority": 2 } ] |
| `--version-policy` | one of: none (Maven only) The repository doesn't validate the version type |  | (Maven only) The package versions that the repository will store. VERSION_POLICY must be one of: none (Maven only) The repository doesn't validate the version type. release (Maven only) The repository accepts release versions only. snapshot (Maven only) The repository accepts snapshot versions only. |


**Examples:**
```bash
To create a docker repository with the name my-repo in the default project
and location, run the following command:

    $ gcloud artifacts repositories create my-repo \
        --repository-format=docker

To create a docker repository my-repo with a KMS key
projects/my-project/locations/us/keyRings/my-kr/cryptoKeys/my-key in the
default project and location, run the following command:

    $ gcloud artifacts repositories create my-repo \
        --repository-format=docker \
        --kms-key=projects/my-project/locations/us/keyRings/my-kr/\
    cryptoKeys/my-key
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/repositories/create)

---
### `gcloud artifacts repositories delete`

Delete an Artifact Registry repository

Delete an Artifact Registry repository. Before you delete a repository,
ensure that any active dependencies on this repository are adjusted to use
a new location.

This command can fail for the following reasons:
  o The specified repository does not exist.
  o The active account does not have permission to delete repositories.

**Synopsis:**
```
gcloud artifacts repositories delete (REPOSITORY : --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Repository resource - The Artifact Registry repository to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

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

  --location=LOCATION
     Location of the repository. Overrides the default artifacts/location
     property value for this command invocation. To configure the default
     location, use the command: gcloud config set artifacts/location.

     To set the location attribute:
     + provide the argument repository on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property artifacts/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete repository named my-repo under the current project, run:

    $ gcloud artifacts repositories delete my-repo
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/repositories/delete)

---
### `gcloud artifacts repositories delete-cleanup-policies`

Delete cleanup policies from an Artifact Registry repository

Delete cleanup policies from an Artifact Registry repository.

This command can fail for the following reasons:
  o The given repository does not exist.
  o The active account does not have permission to update repositories.

**Synopsis:**
```
gcloud artifacts repositories delete-cleanup-policies
    (REPOSITORY : --location=LOCATION) --policynames=POLICYNAMES
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Repository resource - The Artifact Registry repository to update. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

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

  --location=LOCATION
     Location of the repository. Overrides the default artifacts/location
     property value for this command invocation. To configure the default
     location, use the command: gcloud config set artifacts/location.

     To set the location attribute:
     + provide the argument repository on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property artifacts/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--policynames` | POLICYNAMES |  | Comma-separated list of cleanup policy names to delete. |


**Examples:**
```bash
To delete a cleanup policy named policy_a from the repository my-repo, run:

    $ gcloud artifacts repositories delete-cleanup-policies my-repo \
        --policynames=policy_a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/repositories/delete-cleanup-policies)

---
### `gcloud artifacts repositories describe`

Describe an Artifact Registry repository

Describe an Artifact Registry repository given the repository name.

**Synopsis:**
```
gcloud artifacts repositories describe (REPOSITORY : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Repository resource - The Artifact Registry repository to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

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

  --location=LOCATION
     Location of the repository. Overrides the default artifacts/location
     property value for this command invocation. To configure the default
     location, use the command: gcloud config set artifacts/location.

     To set the location attribute:
     + provide the argument repository on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property artifacts/location.
```

**Examples:**
```bash
To describe a repository named my-repo under the current project in
us-west1, run:

    $ gcloud artifacts repositories describe my-repo --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/repositories/describe)

---
### `gcloud artifacts repositories get-iam-policy`

Get IAM policy for an Artifact Registry repository

gcloud artifacts repositories get-iam-policy displays the IAM policy
associated with an Artifact Registry repository. The output includes an
"etag" identifier that is used to check for concurrent policy updates. An
edited policy should include the same etag so that set-iam-policy applies
the changes to the correct policy version.

This command can fail for the following reasons:
  o The repository specified does not exist.
  o The active account does not have permission to access the given
    repository's IAM policies.

**Synopsis:**
```
gcloud artifacts repositories get-iam-policy
    (REPOSITORY : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Repository resource - Name of the Artifact Registry repository. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

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

  --location=LOCATION
     Location of the repository. Overrides the default artifacts/location
     property value for this command invocation. To configure the default
     location, use the command: gcloud config set artifacts/location.

     To set the location attribute:
     + provide the argument repository on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property artifacts/location.
```

**Examples:**
```bash
To print the IAM policy for repository my-repo, run:

    $ gcloud artifacts repositories get-iam-policy my-repo
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/repositories/get-iam-policy)

---
### `gcloud artifacts repositories list`

List repositories in the specified project

List all Artifact Registry repositories in the specified project.

To specify the maximum number of repositories to list, use the --limit
flag.

**Synopsis:**
```
gcloud artifacts repositories list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property artifacts/location. |


**Examples:**
```bash
The following command lists a maximum of five repositories:

    $ gcloud artifacts repositories list --limit=5

To list repositories with name as my_repo:

    $ gcloud artifacts repositories list \
      --filter='name="projects/my-project/locations/us/repositories/my\
    _repo"'

To list repositories with a given partial name, use * to match any
character in name:

    $ gcloud artifacts repositories list \
      --filter='name="projects/my-project/locations/us/repositories/*r\
    epo"'

    $ gcloud artifacts repositories list \
      --filter='name="projects/my-project/locations/us/repositories/my\
    _*"'

To list files that have annotations:

    $ gcloud artifacts repositories list --filter=annotations:*

To list repositories with annotations pair as [annotation_key:
annotation_value]

    $ gcloud artifacts repositories list \
      --filter='annotations.annotation_key:annotation_value'

To list repositories with annotations containing key as my_key:

    $ gcloud artifacts repositories list --filter='annotations.my_key'

If the key or value contains special characters, such as my.key or
my.value, backtick("") is required:

    $ gcloud artifacts repositories list --filter='annotations.`my.key`'

    $ gcloud artifacts repositories list \
      --filter='annotations.`my.key`:`my.value`'

To list repositories with given partial annotation key or value, use * to
match any character:

    $ gcloud artifacts repositories list \
      --filter='annotations.*key:`*.value`'

To list repositories ordered by create_time:

    $ gcloud artifacts repositories list --sort-by=create_time

To list repositories ordered by update_time reversely:

    $ gcloud artifacts repositories list--sort-by=~update_time
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/repositories/list)

---
### `gcloud artifacts repositories list-cleanup-policies`

List cleanup policies of an Artifact Registry repository

List cleanup policies of an Artifact Registry repository.

This command can fail for the following reasons:
  o The specified repository does not exist.
  o The active account does not have permission to list cleanup policies.

**Synopsis:**
```
gcloud artifacts repositories list-cleanup-policies
    (REPOSITORY : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Repository resource - The parent Artifact Registry repository for the list
of cleanup policies. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

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

  --location=LOCATION
     Location of the repository. Overrides the default artifacts/location
     property value for this command invocation. To configure the default
     location, use the command: gcloud config set artifacts/location.

     To set the location attribute:
     + provide the argument repository on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property artifacts/location.
```

**Examples:**
```bash
To list cleanup policies for the repository my-repo, run:

    $ gcloud artifacts repositories list-cleanup-policies my-repo
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/repositories/list-cleanup-policies)

---
### `gcloud artifacts repositories remove-iam-policy-binding`

Remove an IAM policy binding from the IAM policy of an Artifact Registry repository

gcloud artifacts repositories remove-iam-policy-binding removes an IAM
policy binding from the IAM policy of an Artifact Registry repository. One
binding consists of a member, a role, and an optional condition.

This command can fail for the following reasons:
  o The repository specified does not exist.
  o The active account does not have permission to access the given
    repository's IAM policies.

**Synopsis:**
```
gcloud artifacts repositories remove-iam-policy-binding
    (REPOSITORY : --location=LOCATION) --member=PRINCIPAL --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Repository resource - Name of the Artifact Registry repository. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

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

  --location=LOCATION
     Location of the repository. Overrides the default artifacts/location
     property value for this command invocation. To configure the default
     location, use the command: gcloud config set artifacts/location.

     To set the location attribute:
     + provide the argument repository on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property artifacts/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--all` |  |  | _[At most one of these can be specified:]_ Remove all bindings with this role and principal, irrespective of any conditions. |
| `--condition` | [KEY=VALUE,...] |  | _[At most one of these can be specified:]_ The condition of the binding that you want to remove. When the condition is explicitly specified as None (--condition=None), a binding without a condition is removed. Otherwise, only a binding with a condition that exactly matches the specified condition (including the optional description) is removed. For more on conditions, refer to the conditions overview guide: https://cloud.google.com/iam/docs/conditions-overview When using the --condition flag, include the following key-value pairs: expression (Required) Condition expression that evaluates to True or False. This uses a subset of Common Expression Language syntax. If the condition expression includes a comma, use a different delimiter to separate the key-value pairs. Specify the delimiter before listing the key-value pairs. For example, to specify a colon (:) as the delimiter, do the following: --condition=^:^title=TITLE:expression=EXPRESSION. For more information, see https://cloud.google.com/sdk/gcloud/reference/topic/escaping. title (Required) A short string describing the purpose of the expression. description (Optional) Additional description for the expression. |
| `--condition-from-file` | PATH_TO_FILE |  | _[At most one of these can be specified:]_ Path to a local JSON or YAML file that defines the condition. To see available fields, see the help for --condition. Use a full or relative path to a local file containing the value of condition. |


**Examples:**
```bash
To remove an IAM policy binding for the role of 'roles/editor' for the user
'test-user@gmail.com' with repository 'my-repo', run:

    $ gcloud artifacts repositories remove-iam-policy-binding my-repo \
        --member='user:test-user@gmail.com' --role='roles/editor'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/repositories/remove-iam-policy-binding)

---
### `gcloud artifacts repositories set-cleanup-policies`

Set or update cleanup policies for an Artifact Registry repository

Set or update cleanup policies for an Artifact Registry repository.

This command can fail for the following reasons:
  o The given repository does not exist.
  o The active account does not have permission to update repositories.
  o A valid cleanup policy format was not provided.
  o The repository exceeds the maximum number of cleanup policies.

See
https://cloud.google.com/artifact-registry/docs/repositories/cleanup-policy
for details of the cleanup policy file format and contents.

**Synopsis:**
```
gcloud artifacts repositories set-cleanup-policies
    (REPOSITORY : --location=LOCATION) (--dry-run --policy=POLICY)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Repository resource - The parent Artifact Registry repository for the list
of cleanup policies. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

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

  --location=LOCATION
     Location of the repository. Overrides the default artifacts/location
     property value for this command invocation. To configure the default
     location, use the command: gcloud config set artifacts/location.

     To set the location attribute:
     + provide the argument repository on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property artifacts/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--dry-run` |  |  | _[At least one of these must be specified:]_ Disable deleting images according to cleanup policies. |
| `--policy` | POLICY |  | _[At least one of these must be specified:]_ Path to a local JSON formatted file containing valid cleanup policies. |


**Examples:**
```bash
To create a cleanup policy from a file with the name policy.json in the
repository my-repo, run:

    $ gcloud artifacts repositories set-cleanup-policies my-repo \
        --policy=policy.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/repositories/set-cleanup-policies)

---
### `gcloud artifacts repositories set-iam-policy`

Set the IAM policy for an Artifact Registry repository

Set the IAM policy associated with an Artifact Registry repository.

This command can fail for the following reasons:
  o The repository specified does not exist.
  o The active account does not have permission to access the given
    repository's IAM policies.

**Synopsis:**
```
gcloud artifacts repositories set-iam-policy
    (REPOSITORY : --location=LOCATION) POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Repository resource - Name of the Artifact Registry repository. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

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

  --location=LOCATION
     Location of the repository. Overrides the default artifacts/location
     property value for this command invocation. To configure the default
     location, use the command: gcloud config set artifacts/location.

     To set the location attribute:
     + provide the argument repository on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property artifacts/location.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
To set the IAM policy for my-repository, run:

    $ gcloud artifacts repositories set-iam-policy my-repo policy.json

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/repositories/set-iam-policy)

---
### `gcloud artifacts repositories update`

Update an Artifact Registry repository

Update the description or labels for an Artifact Registry repository.

This command can fail for the following reasons:
  o A repository with this name does not exist.
  o The active account does not have permission to update repositories.

**Synopsis:**
```
gcloud artifacts repositories update (REPOSITORY : --location=LOCATION)
    [--description=DESCRIPTION] [--disable-remote-validation]
    [--immutable-tags]
    [--remote-password-secret-version=REMOTE_PASSWORD_SECRET_VERSION]
    [--remote-username=REMOTE_USERNAME] [--update-labels=[KEY=VALUE,...]]
    [--upstream-policy-file=FILE]
    [--allow-vulnerability-scanning | --disable-vulnerability-scanning]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Repository resource - The Artifact Registry repository to update. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

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

  --location=LOCATION
     Location of the repository. Overrides the default artifacts/location
     property value for this command invocation. To configure the default
     location, use the command: gcloud config set artifacts/location.

     To set the location attribute:
     + provide the argument repository on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property artifacts/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description for the repository. |
| `--disable-remote-validation` |  |  | Do not make an HTTP request to validate the remote upstream. Not recommended when setting a custom remote upstream unless you are absolutely sure your upstream URI and any auth is valid. |
| `--immutable-tags` |  |  | (Docker only) Prevent changes to tagged images in the repository. Tags cannot be deleted or moved to a different image digest, and tagged images cannot be deleted. |
| `--remote-password-secret-version` | REMOTE_PASSWORD_SECRET_VERSION |  | Secret Manager secret version that contains password for the remote repository upstream. |
| `--remote-username` | REMOTE_USERNAME |  | Remote Repository upstream registry username. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--upstream-policy-file` | FILE |  | (Virtual Repositories only) is the upstreams for the Virtual Repository. Example of the file contents: [ { "id": "test1", "repository": "projects/p1/locations/us-central1/repositories/repo1", "priority": 1 }, { "id": "test2", "repository": "projects/p2/locations/us-west2/repositories/repo2", "priority": 2 } ] |


**Examples:**
```bash
To update a repository with the name my-repo under the current project,
run:

    $ gcloud artifacts repositories update my-repo \
        --description="New description"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/repositories/update)

---
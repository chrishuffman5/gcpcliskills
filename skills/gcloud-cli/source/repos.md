# gcloud source repos

manage cloud source repositories

### `gcloud source repos clone`

Clone a cloud source repository

This command clones a git repository from the currently active Google Cloud
project into the specified directory or into the current directory if no
target directory is specified.

Each Google Cloud project can have zero or more git repositories associated
with it. To see the available repositories, run:

    $ gcloud source repos list

The clone operation configures the local clone to use your gcloud
credentials to authenticate future git operations. This command emits a
warning if the cloud source repository is a mirror.

**Synopsis:**
```
gcloud source repos clone REPOSITORY_NAME [DIRECTORY_NAME] [--dry-run]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
REPOSITORY_NAME
   Name of the repository.

[DIRECTORY_NAME]
   Directory name for the cloned repo. Defaults to the repository name.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--dry-run` |  |  | If provided, prints the command that would be run to standard out instead of executing it. |


**Examples:**
```bash
The example commands below show a sample workflow.

    $ gcloud init

    $ gcloud source repos clone REPOSITORY_NAME DIRECTORY_NAME

    $ cd DIRECTORY_NAME ... create/edit files and create one or more \
        commits ...

    $ git push origin main
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/source/repos/clone)

---
### `gcloud source repos create`

Create a cloud source repository

This command creates a named git repository for the currently active Google
Cloud Platform project.

**Synopsis:**
```
gcloud source repos create REPOSITORY_NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
REPOSITORY_NAME
   Name of the repository. May contain between 3 and 63 (inclusive)
   lowercase letters, digits, and hyphens. Must start with a letter, and
   may not end with a hyphen.
```

**Examples:**
```bash
To create a named repository in the current project issue the following
commands:

    $ gcloud init

    $ gcloud source repos create REPOSITORY_NAME

Once you push contents to it, they can be browsed in the Developers
Console.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/source/repos/create)

---
### `gcloud source repos delete`

Delete a cloud source repository

This command deletes a named git repository from the currently active
Google Cloud Platform project.

**Synopsis:**
```
gcloud source repos delete REPOSITORY_NAME [--force] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
REPOSITORY_NAME
   Name of the repository.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--force` |  |  | (REMOVED) If provided, skip the delete confirmation prompt. The --force option has been removed; use --quiet to suppress prompting. |


**Examples:**
```bash
To delete a named repository in the current project issue the following
commands:

    $ gcloud init

    $ gcloud source repos delete REPOSITORY_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/source/repos/delete)

---
### `gcloud source repos describe`

Describe a cloud source repository

This command describes a repository from the currently active Google Cloud
Platform project. The description includes the full repository name
(projects/<projectid>/repos/<reponame>), the size (if non-zero), and the
url.

**Synopsis:**
```
gcloud source repos describe REPOSITORY_NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
REPOSITORY_NAME
   Name of the repository.
```

**Examples:**
```bash
To describe a repository named example-repo in the current project issue
the following command:

    $ gcloud source repos describe REPOSITORY_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/source/repos/describe)

---
### `gcloud source repos get-iam-policy`

Get the IAM policy for the named cloud source repository

This command gets the IAM policy for the given repository.

**Synopsis:**
```
gcloud source repos get-iam-policy REPOSITORY_NAME [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
REPOSITORY_NAME
   Name of the repository.
```

**Examples:**
```bash
To get the IAM policy, issue the following command:

    $ gcloud source repos get-iam-policy REPOSITORY_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/source/repos/get-iam-policy)

---
### `gcloud source repos list`

List the repositories the currently active project

By default, repos in the current project are listed; this can be overridden
with the gcloud --project flag. The repository size is not returned, but
can be retrieved for a particular repository with the describe command.

**Synopsis:**
```
gcloud source repos list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all repositories in the current project, run:

    $ gcloud source repos list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/source/repos/list)

---
### `gcloud source repos set-iam-policy`

Set the IAM policy for the named repository

This command sets the IAM policy for the given repository from the policy
in the provided file.

**Synopsis:**
```
gcloud source repos set-iam-policy REPOSITORY_NAME POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
REPOSITORY_NAME
   Name of the repository.

POLICY_FILE
   JSON or YAML file with IAM policy. See
   https://cloud.google.com/resource-manager/reference/rest/Shared.Types/Policy
```

**Examples:**
```bash
To set the IAM policy, issue the following command:

    $ gcloud source repos set-iam-policy REPOSITORY_NAME POLICY_FILE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/source/repos/set-iam-policy)

---
### `gcloud source repos update`

Update the configuration of a Cloud Source Repository

**Synopsis:**
```
gcloud source repos update REPO
    ((--add-topic=ADD_TOPIC | --remove-topic=REMOVE_TOPIC
      | --update-topic=UPDATE_TOPIC) : --message-format=MESSAGE_FORMAT
      --service-account=SERVICE_ACCOUNT --topic-project=TOPIC_PROJECT)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Repo resource - Name of the Cloud Source repository to update. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument repo on the command line with a fully specified
   name;
 * set the property core/project.

This must be specified.

  REPO
     ID of the repo or fully qualified identifier for the repo.

     To set the repo attribute:
     + provide the argument repo on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--message-format` | one of: json, protobuf |  | _[At least one of these must be specified:]_ The format of the message to publish to the topic. MESSAGE_FORMAT must be one of: json, protobuf. |
| `--service-account` | SERVICE_ACCOUNT |  | _[At least one of these must be specified:]_ Email address of the service account used for publishing Cloud Pub/Sub messages. This service account needs to be in the same project as the repo. When added, the caller needs to have iam.serviceAccounts.actAs permission on this service account. If unspecified, it defaults to the Compute Engine default service account. |
| `--topic-project` | TOPIC_PROJECT |  | _[At least one of these must be specified:]_ Cloud project for the topic. If not set, the currently set project will be used. |


**Examples:**
```bash
To associate a Cloud Pub/Sub topic to receive repository update
notifications, run:

    $ gcloud source repos update REPO_NAME --add-topic=TOPIC_NAME \
        --service-account=SERVICE_ACCOUNT_EMAIL --message-format=json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/source/repos/update)

---
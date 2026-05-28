# gcloud builds triggers

create and manage build triggers for Google Cloud Build

### `gcloud builds triggers delete`

Delete a build trigger

Delete a build trigger.

**Synopsis:**
```
gcloud builds triggers delete (TRIGGER : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Trigger resource - Build Trigger. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument TRIGGER on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TRIGGER
     ID of the trigger or fully qualified identifier for the trigger.

     To set the trigger attribute:
     + provide the argument TRIGGER on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud location for the trigger.

     To set the region attribute:
     + provide the argument TRIGGER on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property builds/region.
```

**Examples:**
```bash
To delete a build trigger, run:

    $ gcloud builds triggers delete MY-TRIGGER
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/triggers/delete)

---
### `gcloud builds triggers describe`

Get information about a particular trigger

Get information about the specified build trigger.

**Synopsis:**
```
gcloud builds triggers describe (TRIGGER : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Trigger resource - Build Trigger. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument TRIGGER on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TRIGGER
     ID of the trigger or fully qualified identifier for the trigger.

     To set the trigger attribute:
     + provide the argument TRIGGER on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud location for the trigger.

     To set the region attribute:
     + provide the argument TRIGGER on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property builds/region.
```

**Examples:**
```bash
To describe a build trigger, run:

    $ gcloud builds triggers describe MY-TRIGGER
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/triggers/describe)

---
### `gcloud builds triggers import`

Import a build trigger

To import a trigger from a file: $ cat > trigger.yaml <<EOF name:
my-trigger github: owner: GoogleCloudPlatform name: cloud-builders push:
branch: . EOF

**Synopsis:**
```
gcloud builds triggers import --source=PATH [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source` | PATH |  | File path where trigger should be imported from. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | The region of the Cloud Build Service to use. Must be set to a supported region name (e.g. us-central1). If unset, builds/region, which is the default region to use when working with Cloud Build resources, is used. If builds/region is unset, region is set to global. Note: Region must be specified in 2nd gen repo; global is not supported. |


**Examples:**
```bash
To import a build trigger from a file called trigger.yaml, run:

    $ gcloud builds triggers import --source=trigger.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/triggers/import)

---
### `gcloud builds triggers list`

List Cloud Build triggers for a project

List Cloud Build triggers for a project.

**Synopsis:**
```
gcloud builds triggers list [--region=REGION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | The region of the Cloud Build Service to use. Must be set to a supported region name (e.g. us-central1). If unset, builds/region, which is the default region to use when working with Cloud Build resources, is used. If builds/region is unset, region is set to global. Note: Region must be specified in 2nd gen repo; global is not supported. |


**Examples:**
```bash
To list build triggers, run:

    $ gcloud builds triggers list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/triggers/list)

---
### `gcloud builds triggers run`

Run a build trigger

Run a build trigger.

**Synopsis:**
```
gcloud builds triggers run (TRIGGER : --region=REGION)
    [--substitutions=[KEY=VALUE,...]]
    [--branch=BRANCH | --sha=SHA | --tag=TAG] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Trigger resource - Build Trigger. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument TRIGGER on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TRIGGER
     ID of the trigger or fully qualified identifier for the trigger.

     To set the trigger attribute:
     + provide the argument TRIGGER on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud location for the trigger.

     To set the region attribute:
     + provide the argument TRIGGER on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property builds/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--substitutions` | [KEY=VALUE,...] |  | Parameters to be substituted in the build specification. For example: $ gcloud builds triggers run ... \ --substitutions _FAVORITE_COLOR=blue,_NUM_CANDIES=10 This will result in a build where every occurrence of ${_FAVORITE_COLOR} in certain fields is replaced by "blue", and similarly for ${_NUM_CANDIES} and "10". Substitutions can be applied to user-defined variables (starting with an underscore) and to the following built-in variables: REPO_NAME, BRANCH_NAME, TAG_NAME, REVISION_ID, COMMIT_SHA, SHORT_SHA. For more details, see: https://cloud.google.com/build/docs/configuring-builds/substitute-variable-values |


**Examples:**
```bash
To run a build trigger, run:

    $ gcloud builds triggers run MY-TRIGGER --branch=master
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/triggers/run)

---

## `gcloud builds triggers create` — create build triggers for Google Cloud Build
### `gcloud builds triggers create bitbucket-cloud`

Create a build trigger for a 2nd-gen Bitbucket Cloud repository

Create a build trigger for a 2nd-gen Bitbucket Cloud repository.

**Synopsis:**
```
gcloud builds triggers create bitbucket-cloud
    (--trigger-config=PATH | [(--branch-pattern=REGEX | --tag-pattern=REGEX
      | [--pull-request-pattern=REGEX : --comment-control=COMMENT_CONTROL;
      default="COMMENTS_ENABLED"]) (--build-config=PATH
      | --inline-config=PATH
      | [--dockerfile=DOCKERFILE --dockerfile-image=DOCKERFILE_IMAGE
      : --dockerfile-dir=DOCKERFILE_DIR; default="/"])
      : --description=DESCRIPTION --ignored-files=[GLOB,...]
      --included-files=[GLOB,...] --name=NAME --region=REGION
      --repository=REPOSITORY --[no-]require-approval
      --service-account=SERVICE_ACCOUNT --substitutions=[KEY=VALUE,...]])
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--trigger-config` | PATH |  | _[Exactly one of these must be specified:]_ Path to Build Trigger config file (JSON or YAML format). For more details, see https://cloud.google.com/cloud-build/docs/api/reference/rest/v1/projects.triggers#BuildTrigger |


**Examples:**
```bash
To create a push trigger with a 2nd-gen repository for all branches:

    $ gcloud builds triggers create bitbucket-cloud \
        --name="my-trigger" \
        --service-account="projects/my-project/serviceAccounts/my-byosa@\
    my-project.iam.gserviceaccount.com" \
        --repository="projects/1234/locations/us-central1/connections/my\
    conn/repositories/myrepo" --branch-pattern=".*" \
        --build-config="cloudbuild.yaml" --region=us-central1

To create a pull request trigger with a 2nd-gen repository for main:

    $ gcloud builds triggers create bitbucket-cloud \
        --name="my-trigger" \
        --service-account="projects/my-project/serviceAccounts/my-byosa@\
    my-project.iam.gserviceaccount.com" \
        --repository="projects/1234/locations/us-central1/connections/my\
    conn/repositories/myrepo" --build-config="cloudbuild.yaml" \
        --pull-request-pattern="^main$" --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/triggers/create/bitbucket-cloud)

---
### `gcloud builds triggers create bitbucket-data-center`

Create a build trigger for a 2nd-gen Bitbucket Data Center repository

Create a build trigger for a 2nd-gen Bitbucket Data Center repository.

**Synopsis:**
```
gcloud builds triggers create bitbucket-data-center
    (--trigger-config=PATH | [(--branch-pattern=REGEX | --tag-pattern=REGEX
      | [--pull-request-pattern=REGEX : --comment-control=COMMENT_CONTROL;
      default="COMMENTS_ENABLED"]) (--build-config=PATH
      | --inline-config=PATH
      | [--dockerfile=DOCKERFILE --dockerfile-image=DOCKERFILE_IMAGE
      : --dockerfile-dir=DOCKERFILE_DIR; default="/"])
      : --description=DESCRIPTION --ignored-files=[GLOB,...]
      --included-files=[GLOB,...] --name=NAME --region=REGION
      --repository=REPOSITORY --[no-]require-approval
      --service-account=SERVICE_ACCOUNT --substitutions=[KEY=VALUE,...]])
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--trigger-config` | PATH |  | _[Exactly one of these must be specified:]_ Path to Build Trigger config file (JSON or YAML format). For more details, see https://cloud.google.com/cloud-build/docs/api/reference/rest/v1/projects.triggers#BuildTrigger |


**Examples:**
```bash
To create a push trigger with a 2nd-gen repository for all branches:

    $ gcloud builds triggers create bitbucket-data-center \
        --name="my-trigger" \
        --service-account="projects/my-project/serviceAccounts/my-byosa@\
    my-project.iam.gserviceaccount.com" \
        --repository="projects/1234/locations/us-central1/connections/my\
    conn/repositories/myrepo" --branch-pattern=".*" \
        --build-config="cloudbuild.yaml" --region=us-central1

To create a pull request trigger with a 2nd-gen repository for main:

    $ gcloud builds triggers create bitbucket-data-center \
        --name="my-trigger" \
        --service-account="projects/my-project/serviceAccounts/my-byosa@\
    my-project.iam.gserviceaccount.com" \
        --repository="projects/1234/locations/us-central1/connections/my\
    conn/repositories/myrepo" --build-config="cloudbuild.yaml" \
        --pull-request-pattern="^main$" --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/triggers/create/bitbucket-data-center)

---
### `gcloud builds triggers create bitbucketserver`

Create a build trigger for a Bitbucket Server repository

Create a build trigger for a Bitbucket Server repository.

**Synopsis:**
```
gcloud builds triggers create bitbucketserver
    (--trigger-config=PATH
      | [--bitbucket-server-config-resource=BITBUCKET_SERVER_CONFIG_RESOURCE --project-key=PROJECT_KEY --repo-slug=REPO_SLUG (--branch-pattern=REGEX | --tag-pattern=REGEX | [--pull-request-pattern=REGEX : --comment-control=COMMENT_CONTROL; default="COMMENTS_ENABLED"]) (--build-config=PATH | --inline-config=PATH | [--dockerfile=DOCKERFILE : --dockerfile-dir=DOCKERFILE_DIR; default="/" --dockerfile-image=DOCKERFILE_IMAGE]) : --description=DESCRIPTION --ignored-files=[GLOB,
      ...] --included-files=[GLOB,...] --name=NAME --region=REGION
      --[no-]require-approval
      --service-account=SERVICE_ACCOUNT --substitutions=[KEY=VALUE,...]])
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--trigger-config` | PATH |  | _[Exactly one of these must be specified:]_ Path to Build Trigger config file (JSON or YAML format). For more details, see https://cloud.google.com/cloud-build/docs/api/reference/rest/v1/projects.triggers#BuildTrigger |


**Examples:**
```bash
To create a push trigger for all branches:

    $ gcloud builds triggers create bitbucketserver \
        --name="my-trigger" \
        --service-account="projects/my-project/serviceAccounts/my-byosa@\
    my-project.iam.gserviceaccount.com" \
        --project-key="GoogleCloudPlatform" \
        --repo-slug="cloud-builders" \
        --bitbucket-server-config-resource="projects/1234/locations/glob\
    al/bitbucketServerConfigs/5678" --branch-pattern=".*" \
        --build-config="cloudbuild.yaml"

To create a pull request trigger for main:

    $ gcloud builds triggers create bitbucketserver \
        --name="my-trigger" \
        --service-account="projects/my-project/serviceAccounts/my-byosa@\
    my-project.iam.gserviceaccount.com" \
        --project-key="GoogleCloudPlatform" \
        --repo-slug="cloud-builders" \
        --bitbucket-server-config-resource="projects/1234/locations/glob\
    al/bitbucketServerConfigs/5678" --pull-request-pattern="^main$" \
        --build-config="cloudbuild.yaml"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/triggers/create/bitbucketserver)

---
### `gcloud builds triggers create cloud-source-repositories`

Create a build trigger from a Cloud Source Repository

Create a build trigger from a Cloud Source Repository.

**Synopsis:**
```
gcloud builds triggers create cloud-source-repositories
    (--trigger-config=PATH | [--repo=REPO (--branch-pattern=REGEX
      | --tag-pattern=REGEX) (--build-config=PATH | --inline-config=PATH
      | [--dockerfile=DOCKERFILE : --dockerfile-dir=DOCKERFILE_DIR;
      default="/" --dockerfile-image=DOCKERFILE_IMAGE])
      : --description=DESCRIPTION --ignored-files=[GLOB,...]
      --included-files=[GLOB,...] --name=NAME --region=REGION
      --[no-]require-approval
      --service-account=SERVICE_ACCOUNT --substitutions=[KEY=VALUE,...]])
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--trigger-config` | PATH |  | _[Exactly one of these must be specified:]_ Path to Build Trigger config file (JSON or YAML format). For more details, see https://cloud.google.com/cloud-build/docs/api/reference/rest/v1/projects.triggers#BuildTrigger |


**Examples:**
```bash
To create a push trigger for all branches:

    $ gcloud builds triggers create cloud-source-repositories \
        --name="my-trigger" \
        --service-account="projects/my-project/serviceAccounts/my-byosa@\
    my-project.iam.gserviceaccount.com" --repo="my-repo" \
        --branch-pattern=".*" --build-config="cloudbuild.yaml"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/triggers/create/cloud-source-repositories)

---
### `gcloud builds triggers create github`

Create a build trigger for a GitHub repository

Create a build trigger for a GitHub repository.

**Synopsis:**
```
gcloud builds triggers create github
    (--trigger-config=PATH | [(--branch-pattern=REGEX | --tag-pattern=REGEX
      | [--pull-request-pattern=REGEX : --comment-control=COMMENT_CONTROL;
      default="COMMENTS_ENABLED"]) (--build-config=PATH
      | --inline-config=PATH | [--dockerfile=DOCKERFILE
      : --dockerfile-dir=DOCKERFILE_DIR; default="/"
      --dockerfile-image=DOCKERFILE_IMAGE]) (--repository=REPOSITORY
      | [--repo-name=REPO_NAME --repo-owner=REPO_OWNER
      : --enterprise-config=ENTERPRISE_CONFIG]) : --description=DESCRIPTION
      --ignored-files=[GLOB,...] --include-logs-with-status
      --included-files=[GLOB,...] --name=NAME --region=REGION
      --[no-]require-approval
      --service-account=SERVICE_ACCOUNT --substitutions=[KEY=VALUE,...]])
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--trigger-config` | PATH |  | _[Exactly one of these must be specified:]_ Path to Build Trigger config file (JSON or YAML format). For more details, see https://cloud.google.com/cloud-build/docs/api/reference/rest/v1/projects.triggers#BuildTrigger |


**Examples:**
```bash
To create a push trigger with a 1st-gen repository for all branches:

    $ gcloud builds triggers create github --name="my-trigger" \
        --service-account="projects/my-project/serviceAccounts/my-byosa@\
    my-project.iam.gserviceaccount.com" \
        --repo-owner="GoogleCloudPlatform" \
        --repo-name="cloud-builders" --branch-pattern=".*" \
        --build-config="cloudbuild.yaml"

To create a pull request trigger with a 1st-gen repository for master:

    $ gcloud builds triggers create github --name="my-trigger" \
        --service-account="projects/my-project/serviceAccounts/my-byosa@\
    my-project.iam.gserviceaccount.com" \
        --repo-owner="GoogleCloudPlatform" \
        --repo-name="cloud-builders" --pull-request-pattern="^master$" \
        --build-config="cloudbuild.yaml"

To create a pull request trigger with a 2nd gen repository for master:

    $ gcloud builds triggers create github --name="my-trigger" \
        --repository=projects/my-project/locations/us-central1/\
    connections/my-conn/repositories/my-repo \
        --pull-request-pattern="^master$" \
        --build-config="cloudbuild.yaml" --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/triggers/create/github)

---
### `gcloud builds triggers create gitlab`

Create a build trigger for a 2nd-gen GitLab repository

Create a build trigger for a 2nd-gen GitLab repository.

**Synopsis:**
```
gcloud builds triggers create gitlab
    (--trigger-config=PATH | [(--branch-pattern=REGEX | --tag-pattern=REGEX
      | [--pull-request-pattern=REGEX : --comment-control=COMMENT_CONTROL;
      default="COMMENTS_ENABLED"]) (--build-config=PATH
      | --inline-config=PATH
      | [--dockerfile=DOCKERFILE --dockerfile-image=DOCKERFILE_IMAGE
      : --dockerfile-dir=DOCKERFILE_DIR; default="/"])
      : --description=DESCRIPTION --ignored-files=[GLOB,...]
      --included-files=[GLOB,...] --name=NAME --region=REGION
      --repository=REPOSITORY --[no-]require-approval
      --service-account=SERVICE_ACCOUNT --substitutions=[KEY=VALUE,...]])
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--trigger-config` | PATH |  | _[Exactly one of these must be specified:]_ Path to Build Trigger config file (JSON or YAML format). For more details, see https://cloud.google.com/cloud-build/docs/api/reference/rest/v1/projects.triggers#BuildTrigger |


**Examples:**
```bash
To create a push trigger with a 2nd-gen repository for all branches:

    $ gcloud builds triggers create gitlab --name="my-trigger" \
        --service-account="projects/my-project/serviceAccounts/my-byosa@\
    my-project.iam.gserviceaccount.com" \
        --repository="projects/1234/locations/us-central1/connections/my\
    conn/repositories/myrepo" --branch-pattern=".*" \
        --build-config="cloudbuild.yaml" --region=us-central1

To create a pull request trigger with a 2nd-gen repository for main:

    $ gcloud builds triggers create gitlab --name="my-trigger" \
        --service-account="projects/my-project/serviceAccounts/my-byosa@\
    my-project.iam.gserviceaccount.com" \
        --repository="projects/1234/locations/us-central1/connections/my\
    conn/repositories/myrepo" --build-config="cloudbuild.yaml" \
        --pull-request-pattern="^main$" --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/triggers/create/gitlab)

---
### `gcloud builds triggers create manual`

Create a build trigger with a manual trigger event

Create a build trigger with a manual trigger event.

**Synopsis:**
```
gcloud builds triggers create manual
    (--trigger-config=PATH | [(--build-config=PATH | --inline-config=PATH
      | [--dockerfile=DOCKERFILE : --dockerfile-dir=DOCKERFILE_DIR;
      default="/" --dockerfile-image=DOCKERFILE_IMAGE])
      : --description=DESCRIPTION --name=NAME --region=REGION
      --[no-]require-approval --service-account=SERVICE_ACCOUNT
      --substitutions=[KEY=VALUE,...] --branch=BRANCH
      | --tag=TAG --repository=REPOSITORY
      | [--repo=REPO --repo-type=REPO_TYPE
      : --github-enterprise-config=GITHUB_ENTERPRISE_CONFIG]])
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--trigger-config` | PATH |  | _[Exactly one of these must be specified:]_ Path to Build Trigger config file (JSON or YAML format). For more details, see https://cloud.google.com/cloud-build/docs/api/reference/rest/v1/projects.triggers#BuildTrigger |


**Examples:**
```bash
To create a manual trigger that builds off branch my-branch in a GitHub
repository named my-repo:

    $ gcloud builds triggers create manual --name=my-manual-trigger \
        --build-config=cloudbuild.yaml \
        --repo=https://www.github.com/owner/repo --repo-type=GITHUB \
        --branch=my-branch

To create a manual trigger that builds off branch my-branch in a 2nd-gen
GitHub repository resource:

    $ gcloud builds triggers create manual --name=my-manual-trigger \
        --build-config=cloudbuild.yaml \
        --repository=projects/my-proj/locations/us-west1/connections/\
    my-conn/repositories/my-repo --branch=my-branch
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/triggers/create/manual)

---
### `gcloud builds triggers create pubsub`

Create a build trigger with a Pub/Sub trigger event

Create a build trigger with a Pub/Sub trigger event.

**Synopsis:**
```
gcloud builds triggers create pubsub
    (--trigger-config=PATH | [--topic=TOPIC (--build-config=PATH
      | --inline-config=PATH | [--dockerfile=DOCKERFILE
      : --dockerfile-dir=DOCKERFILE_DIR;
      default="/" --dockerfile-image=DOCKERFILE_IMAGE])
      : --description=DESCRIPTION --name=NAME --region=REGION
      --[no-]require-approval --service-account=SERVICE_ACCOUNT
      --subscription-filter=SUBSCRIPTION_FILTER
      --substitutions=[KEY=VALUE,...] --branch=BRANCH
      | --tag=TAG --repository=REPOSITORY
      | [--repo=REPO --repo-type=REPO_TYPE
      : --github-enterprise-config=GITHUB_ENTERPRISE_CONFIG]])
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--trigger-config` | PATH |  | _[Exactly one of these must be specified:]_ Path to Build Trigger config file (JSON or YAML format). For more details, see https://cloud.google.com/cloud-build/docs/api/reference/rest/v1/projects.triggers#BuildTrigger |


**Examples:**
```bash
To create a Pub/Sub trigger that listens to topic my-topic and builds off
branch my-branch in a GitHub repository named my-repo:

    $ gcloud builds triggers create pubsub --name=my-pubsub-trigger \
        --service-account="projects/my-project/serviceAccounts/my-byosa@\
    my-project.iam.gserviceaccount.com" \
        --topic=projects/my-project/topics/my-topic \
        --repo=https://www.github.com/owner/repo --repo-type=GITHUB \
        --branch=my-branch

To create a Pub/Sub trigger that listens to topic my-topic and builds off
branch my-branch in a 2nd-gen GitHub repository resource:

    $ gcloud builds triggers create pubsub --name=my-pubsub-trigger \
        --service-account="projects/my-project/serviceAccounts/my-byosa@\
    my-project.iam.gserviceaccount.com" \
        --repository=projects/my-proj/locations/us-west1/connections/\
    my-conn/repositories/my-repo --branch=my-branch
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/triggers/create/pubsub)

---
### `gcloud builds triggers create webhook`

Create a build trigger with a Webhook trigger event

Create a build trigger with a Webhook trigger event.

**Synopsis:**
```
gcloud builds triggers create webhook
    (--trigger-config=PATH | [--secret=SECRET (--build-config=PATH
      | --inline-config=PATH | [--dockerfile=DOCKERFILE
      : --dockerfile-dir=DOCKERFILE_DIR;
      default="/" --dockerfile-image=DOCKERFILE_IMAGE])
      : --description=DESCRIPTION --name=NAME --region=REGION
      --[no-]require-approval --service-account=SERVICE_ACCOUNT
      --subscription-filter=SUBSCRIPTION_FILTER
      --substitutions=[KEY=VALUE,...] --branch=BRANCH
      | --tag=TAG --repository=REPOSITORY
      | [--repo=REPO --repo-type=REPO_TYPE
      : --github-enterprise-config=GITHUB_ENTERPRISE_CONFIG]])
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--trigger-config` | PATH |  | _[Exactly one of these must be specified:]_ Path to Build Trigger config file (JSON or YAML format). For more details, see https://cloud.google.com/cloud-build/docs/api/reference/rest/v1/projects.triggers#BuildTrigger |


**Examples:**
```bash
To create a Webhook trigger that requires secret
projects/my-project/secrets/my-secret/versions/2 and builds off branch
my-branch in a GitHub repository named my-repo:

    $ gcloud builds triggers create webhook --name=my-webhook-trigger \
        --service-account="projects/my-project/serviceAccounts/my-byosa@\
    my-project.iam.gserviceaccount.com" \
        --secret=projects/my-project/secrets/my-secret/versions/2 \
        --repo=https://www.github.com/owner/repo --repo-type=GITHUB \
        --branch=my-branch

To create a Webhook trigger that requires secret
projects/my-project/secrets/my-secret/versions/2 and builds off branch
my-branch in a 2nd-gen GitHub repository:

    $ gcloud builds triggers create webhook --name=my-webhook-trigger \
        --service-account="projects/my-project/serviceAccounts/my-byosa@\
    my-project.iam.gserviceaccount.com" \
        --secret=projects/my-project/secrets/my-secret/versions/2 \
        --branch=my-branch \
        --repository=projects/my-proj/locations/us-west1/connections/\
    my-conn/repositories/my-repo
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/triggers/create/webhook)

---

## `gcloud builds triggers update` — update Triggers in Google Cloud Build
### `gcloud builds triggers update bitbucket-cloud`

Updates Bitbucket Cloud trigger used by Cloud Build

Updates Bitbucket Cloud trigger used by Cloud Build.

**Synopsis:**
```
gcloud builds triggers update bitbucket-cloud (TRIGGER : --region=REGION)
    (--trigger-config=PATH | --description=DESCRIPTION
      --ignored-files=[GLOB,...] --included-files=[GLOB,...]
      --repository=REPOSITORY --[no-]require-approval
      --service-account=SERVICE_ACCOUNT --branch-pattern=REGEX
      | --tag-pattern=REGEX | --comment-control=COMMENT_CONTROL
      --pull-request-pattern=REGEX --build-config=PATH
      | --inline-config=PATH
      | [--dockerfile=DOCKERFILE --dockerfile-image=DOCKERFILE_IMAGE
      : --dockerfile-dir=DOCKERFILE_DIR] --clear-substitutions
      | --remove-substitutions=[KEY,...]
      | --update-substitutions=[KEY=VALUE,...]) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Trigger resource - Build Trigger. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument TRIGGER on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TRIGGER
     ID of the trigger or fully qualified identifier for the trigger.

     To set the trigger attribute:
     + provide the argument TRIGGER on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud location for the trigger.

     To set the region attribute:
     + provide the argument TRIGGER on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property builds/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--trigger-config` | PATH |  | _[Exactly one of these must be specified:]_ Path to Build Trigger config file (JSON or YAML format). For more details, see https://cloud.google.com/cloud-build/docs/api/reference/rest/v1/projects.triggers#BuildTrigger |


**Examples:**
```bash
To update the branch pattern of the trigger:

    $ gcloud builds triggers update bitbucket-cloud my-trigger \
        --branch-pattern=".*"

To update the build config of the trigger:

    $ gcloud builds triggers update bitbucket-cloud my-trigger \
        --build-config="cloudbuild.yaml"

To update the substitutions of the trigger:

    $ gcloud builds triggers update bitbucket-cloud my-trigger \
        --update-substitutions=_REPO_NAME=my-repo,_BRANCH_NAME=master

To update the 2nd-gen repository resource of the trigger:

    $ gcloud builds triggers update bitbucket-cloud my-trigger \
        --repository=projects/my-project/locations/us-west1/\
    connections/my-conn/repositories/my-repo
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/triggers/update/bitbucket-cloud)

---
### `gcloud builds triggers update bitbucket-data-center`

Updates Bitbucket Data Center trigger used by Cloud Build

Updates Bitbucket Data Center trigger used by Cloud Build.

**Synopsis:**
```
gcloud builds triggers update bitbucket-data-center
    (TRIGGER : --region=REGION)
    (--trigger-config=PATH | --description=DESCRIPTION
      --ignored-files=[GLOB,...] --included-files=[GLOB,...]
      --repository=REPOSITORY --[no-]require-approval
      --service-account=SERVICE_ACCOUNT --branch-pattern=REGEX
      | --tag-pattern=REGEX | --comment-control=COMMENT_CONTROL
      --pull-request-pattern=REGEX --build-config=PATH
      | --inline-config=PATH
      | [--dockerfile=DOCKERFILE --dockerfile-image=DOCKERFILE_IMAGE
      : --dockerfile-dir=DOCKERFILE_DIR] --clear-substitutions
      | --remove-substitutions=[KEY,...]
      | --update-substitutions=[KEY=VALUE,...]) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Trigger resource - Build Trigger. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument TRIGGER on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TRIGGER
     ID of the trigger or fully qualified identifier for the trigger.

     To set the trigger attribute:
     + provide the argument TRIGGER on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud location for the trigger.

     To set the region attribute:
     + provide the argument TRIGGER on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property builds/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--trigger-config` | PATH |  | _[Exactly one of these must be specified:]_ Path to Build Trigger config file (JSON or YAML format). For more details, see https://cloud.google.com/cloud-build/docs/api/reference/rest/v1/projects.triggers#BuildTrigger |


**Examples:**
```bash
To update the branch pattern of the trigger:

    $ gcloud builds triggers update bitbucket-data-center my-trigger \
        --branch-pattern=".*"

To update the build config of the trigger:

    $ gcloud builds triggers update bitbucket-data-center my-trigger \
        --build-config="cloudbuild.yaml"

To update the substitutions of the trigger:

    $ gcloud builds triggers update bitbucket-data-center my-trigger \
        --update-substitutions=_REPO_NAME=my-repo,_BRANCH_NAME=master

To update the 2nd-gen repository resource of the trigger:

    $ gcloud builds triggers update bitbucket-data-center my-trigger \
        --repository=projects/my-project/locations/us-west1/\
    connections/my-conn/repositories/my-repo
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/triggers/update/bitbucket-data-center)

---
### `gcloud builds triggers update bitbucketserver`

Updates Bitbucket Server trigger used by Cloud Build

Updates Bitbucket Server trigger used by Cloud Build.

**Synopsis:**
```
gcloud builds triggers update bitbucketserver (TRIGGER : --region=REGION)
    (--trigger-config=PATH
      | --bitbucket-server-config-resource=BITBUCKET_SERVER_CONFIG_RESOURCE
      --description=DESCRIPTION --ignored-files=[GLOB,...]
      --included-files=[GLOB,...] --project-key=PROJECT_KEY
      --repo-slug=REPO_SLUG --[no-]require-approval
      --service-account=SERVICE_ACCOUNT --branch-pattern=REGEX
      | --tag-pattern=REGEX | --comment-control=COMMENT_CONTROL;
      default="COMMENTS_ENABLED"
      --pull-request-pattern=REGEX --build-config=PATH
      | --inline-config=PATH
      | [--dockerfile=DOCKERFILE --dockerfile-image=DOCKERFILE_IMAGE
      : --dockerfile-dir=DOCKERFILE_DIR] --clear-substitutions
      | --remove-substitutions=[KEY,...]
      | --update-substitutions=[KEY=VALUE,...]) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Trigger resource - Build Trigger. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument TRIGGER on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TRIGGER
     ID of the trigger or fully qualified identifier for the trigger.

     To set the trigger attribute:
     + provide the argument TRIGGER on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud location for the trigger.

     To set the region attribute:
     + provide the argument TRIGGER on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property builds/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--trigger-config` | PATH |  | _[Exactly one of these must be specified:]_ Path to Build Trigger config file (JSON or YAML format). For more details, see https://cloud.google.com/cloud-build/docs/api/reference/rest/v1/projects.triggers#BuildTrigger |


**Examples:**
```bash
To update the branch pattern of the trigger:

    $ gcloud builds triggers update bitbucketserver my-trigger \
        --branch-pattern=".*"

To update the build config of the trigger:

    $ gcloud builds triggers update bitbucketserver my-trigger \
        --build-config="cloudbuild.yaml"

To update the substitutions of the trigger:        $ gcloud builds triggers update bitbucketserver my-trigger \
        --update-substitutions=_REPO_NAME=my-repo,_BRANCH_NAME=master
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/triggers/update/bitbucketserver)

---
### `gcloud builds triggers update cloud-source-repositories`

Updates Cloud Source Repositories trigger used by Cloud Build

Updates Cloud Source Repositories trigger used by Cloud Build.

**Synopsis:**
```
gcloud builds triggers update cloud-source-repositories
    (TRIGGER : --region=REGION)
    (--trigger-config=PATH | --description=DESCRIPTION
      --ignored-files=[GLOB,...] --included-files=[GLOB,...] --repo=REPO
      --[no-]require-approval
      --service-account=SERVICE_ACCOUNT --branch-pattern=REGEX
      | --tag-pattern=REGEX --build-config=PATH | --inline-config=PATH
      | [--dockerfile=DOCKERFILE --dockerfile-image=DOCKERFILE_IMAGE
      : --dockerfile-dir=DOCKERFILE_DIR] --clear-substitutions
      | --remove-substitutions=[KEY,...]
      | --update-substitutions=[KEY=VALUE,...]) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Trigger resource - Build Trigger. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument TRIGGER on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TRIGGER
     ID of the trigger or fully qualified identifier for the trigger.

     To set the trigger attribute:
     + provide the argument TRIGGER on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud location for the trigger.

     To set the region attribute:
     + provide the argument TRIGGER on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property builds/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--trigger-config` | PATH |  | _[Exactly one of these must be specified:]_ Path to Build Trigger config file (JSON or YAML format). For more details, see https://cloud.google.com/cloud-build/docs/api/reference/rest/v1/projects.triggers#BuildTrigger |


**Examples:**
```bash
To update the branch pattern of the trigger:

    $ gcloud builds triggers update cloud-source-repositories \
        my-trigger --branch-pattern=".*"

To update the build config of the trigger:

    $ gcloud builds triggers update cloud-source-repositories \
        my-trigger --build-config="cloudbuild.yaml"

To update the substitutions of the trigger:

    $ gcloud builds triggers update cloud-source-repositories \
        my-trigger \
        --update-substitutions=_REPO_NAME=my-repo,_BRANCH_NAME=master
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/triggers/update/cloud-source-repositories)

---
### `gcloud builds triggers update github`

Update GitHub trigger used by Cloud Build

Update GitHub trigger used by Cloud Build.

**Synopsis:**
```
gcloud builds triggers update github (TRIGGER : --region=REGION)
    (--trigger-config=PATH | --description=DESCRIPTION
      --ignored-files=[GLOB,...] --include-logs-with-status
      --included-files=[GLOB,...] --[no-]require-approval
      --service-account=SERVICE_ACCOUNT --branch-pattern=REGEX
      | --tag-pattern=REGEX | --comment-control=COMMENT_CONTROL;
      default="COMMENTS_ENABLED"
      --pull-request-pattern=REGEX --build-config=PATH
      | --inline-config=PATH
      | [--dockerfile=DOCKERFILE --dockerfile-image=DOCKERFILE_IMAGE
      : --dockerfile-dir=DOCKERFILE_DIR] --clear-substitutions
      | --remove-substitutions=[KEY,...]
      | --update-substitutions=[KEY=VALUE,...] --repository=REPOSITORY
      | --enterprise-config=ENTERPRISE_CONFIG
      --repo-name=REPO_NAME --repo-owner=REPO_OWNER) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Trigger resource - Build Trigger. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument TRIGGER on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TRIGGER
     ID of the trigger or fully qualified identifier for the trigger.

     To set the trigger attribute:
     + provide the argument TRIGGER on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud location for the trigger.

     To set the region attribute:
     + provide the argument TRIGGER on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property builds/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--trigger-config` | PATH |  | _[Exactly one of these must be specified:]_ Path to Build Trigger config file (JSON or YAML format). For more details, see https://cloud.google.com/cloud-build/docs/api/reference/rest/v1/projects.triggers#BuildTrigger |


**Examples:**
```bash
To update the branch pattern of the trigger:

    $ gcloud builds triggers update github my-trigger \
        --branch-pattern=".*"

To update the build config of the trigger:

    $ gcloud builds triggers update github my-trigger \
        --build-config="cloudbuild.yaml"

To update the substitutions of the trigger:

    $ gcloud builds triggers update github my-trigger \
        --update-substitutions=_REPO_NAME=my-repo,_BRANCH_NAME=master
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/triggers/update/github)

---
### `gcloud builds triggers update gitlab`

Updates GitLab trigger used by Cloud Build

Updates GitLab trigger used by Cloud Build.

**Synopsis:**
```
gcloud builds triggers update gitlab (TRIGGER : --region=REGION)
    (--trigger-config=PATH | --description=DESCRIPTION
      --ignored-files=[GLOB,...] --included-files=[GLOB,...]
      --repository=REPOSITORY --[no-]require-approval
      --service-account=SERVICE_ACCOUNT --branch-pattern=REGEX
      | --tag-pattern=REGEX | --comment-control=COMMENT_CONTROL
      --pull-request-pattern=REGEX --build-config=PATH
      | --inline-config=PATH
      | [--dockerfile=DOCKERFILE --dockerfile-image=DOCKERFILE_IMAGE
      : --dockerfile-dir=DOCKERFILE_DIR] --clear-substitutions
      | --remove-substitutions=[KEY,...]
      | --update-substitutions=[KEY=VALUE,...]) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Trigger resource - Build Trigger. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument TRIGGER on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TRIGGER
     ID of the trigger or fully qualified identifier for the trigger.

     To set the trigger attribute:
     + provide the argument TRIGGER on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud location for the trigger.

     To set the region attribute:
     + provide the argument TRIGGER on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property builds/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--trigger-config` | PATH |  | _[Exactly one of these must be specified:]_ Path to Build Trigger config file (JSON or YAML format). For more details, see https://cloud.google.com/cloud-build/docs/api/reference/rest/v1/projects.triggers#BuildTrigger |


**Examples:**
```bash
To update the branch pattern of the trigger:

    $ gcloud builds triggers update gitlab my-trigger \
        --branch-pattern=".*"

To update the build config of the trigger:

    $ gcloud builds triggers update gitlab my-trigger \
        --build-config="cloudbuild.yaml"

To update the substitutions of the trigger:

    $ gcloud builds triggers update gitlab my-trigger \
        --update-substitutions=_REPO_NAME=my-repo,_BRANCH_NAME=master

To update the 2nd-gen repository resource of the trigger:

    $ gcloud builds triggers update gitlab my-trigger \
        --repository=projects/my-project/locations/us-west1/\
    connections/my-conn/repositories/my-repo
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/triggers/update/gitlab)

---
### `gcloud builds triggers update manual`

Updates a manual trigger used by Cloud Build

Updates a manual trigger used by Cloud Build.

**Synopsis:**
```
gcloud builds triggers update manual (TRIGGER : --region=REGION)
    (--trigger-config=PATH | --description=DESCRIPTION
      --[no-]require-approval
      --service-account=SERVICE_ACCOUNT --clear-substitutions
      | --remove-substitutions=[KEY,...]
      | --update-substitutions=[KEY=VALUE,...] --inline-config=PATH
      | [--dockerfile=DOCKERFILE : --dockerfile-dir=DOCKERFILE_DIR
      --dockerfile-image=DOCKERFILE_IMAGE]
      | --git-file-source-branch=GIT_FILE_SOURCE_BRANCH
      | --git-file-source-tag=GIT_FILE_SOURCE_TAG
      --git-file-source-github-enterprise-config=GIT_FILE_SOURCE_GITHUB_ENTERPRISE_CONFIG --git-file-source-path=PATH --git-file-source-repo-type=GIT_FILE_SOURCE_REPO_TYPE --git-file-source-uri=URL --source-to-build-branch=SOURCE_TO_BUILD_BRANCH | --source-to-build-tag=SOURCE_TO_BUILD_TAG --source-to-build-github-enterprise-config=SOURCE_TO_BUILD_GITHUB_ENTERPRISE_CONFIG --source-to-build-repo-type=SOURCE_TO_BUILD_REPO_TYPE --source-to-build-uri=SOURCE_TO_BUILD_URI)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Trigger resource - Build Trigger. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument TRIGGER on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TRIGGER
     ID of the trigger or fully qualified identifier for the trigger.

     To set the trigger attribute:
     + provide the argument TRIGGER on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud location for the trigger.

     To set the region attribute:
     + provide the argument TRIGGER on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property builds/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--trigger-config` | PATH |  | _[Exactly one of these must be specified:]_ Path to Build Trigger config file (JSON or YAML format). For more details, see https://cloud.google.com/cloud-build/docs/api/reference/rest/v1/projects.triggers#BuildTrigger |


**Examples:**
```bash
To update the branch from which the trigger clones:

    $ gcloud builds triggers update manual my-trigger \
        --source-to-build-branch=my-branch
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/triggers/update/manual)

---
### `gcloud builds triggers update pubsub`

Update a Pub/Sub trigger used by Cloud Build

Update a Pub/Sub trigger used by Cloud Build.

**Synopsis:**
```
gcloud builds triggers update pubsub (TRIGGER : --region=REGION)
    (--trigger-config=PATH | --description=DESCRIPTION
      --[no-]require-approval --service-account=SERVICE_ACCOUNT
      --topic=TOPIC --clear-subscription-filter
      | --subscription-filter=SUBSCRIPTION_FILTER --clear-substitutions
      | --remove-substitutions=[KEY,...]
      | --update-substitutions=[KEY=VALUE,...] --inline-config=PATH
      | [--dockerfile=DOCKERFILE : --dockerfile-dir=DOCKERFILE_DIR
      --dockerfile-image=DOCKERFILE_IMAGE]
      | --git-file-source-branch=GIT_FILE_SOURCE_BRANCH
      | --git-file-source-tag=GIT_FILE_SOURCE_TAG
      --git-file-source-github-enterprise-config=GIT_FILE_SOURCE_GITHUB_ENTERPRISE_CONFIG --git-file-source-path=PATH --git-file-source-repo-type=GIT_FILE_SOURCE_REPO_TYPE --git-file-source-uri=URL --source-to-build-branch=SOURCE_TO_BUILD_BRANCH | --source-to-build-tag=SOURCE_TO_BUILD_TAG --source-to-build-github-enterprise-config=SOURCE_TO_BUILD_GITHUB_ENTERPRISE_CONFIG --source-to-build-repo-type=SOURCE_TO_BUILD_REPO_TYPE --source-to-build-uri=SOURCE_TO_BUILD_URI)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Trigger resource - Build Trigger. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument TRIGGER on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TRIGGER
     ID of the trigger or fully qualified identifier for the trigger.

     To set the trigger attribute:
     + provide the argument TRIGGER on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud location for the trigger.

     To set the region attribute:
     + provide the argument TRIGGER on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property builds/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--trigger-config` | PATH |  | _[Exactly one of these must be specified:]_ Path to Build Trigger config file (JSON or YAML format). For more details, see https://cloud.google.com/cloud-build/docs/api/reference/rest/v1/projects.triggers#BuildTrigger |


**Examples:**
```bash
To update the branch from which the trigger clones:

    $ gcloud builds triggers update pubsub my-trigger \
        --source-to-build-branch=my-branch

To update the topic:

    $ gcloud builds triggers update pubsub my-trigger \
        --topic=projects/my-project/topics/my-topic

To update the substitutions of the trigger:        $ gcloud builds triggers update pubsub my-trigger \
        --update-substitutions=_REPO_NAME=my-repo,_BRANCH_NAME=master
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/triggers/update/pubsub)

---
### `gcloud builds triggers update webhook`

Update a Webhook trigger used by Cloud Build

Update a Webhook trigger used by Cloud Build.

**Synopsis:**
```
gcloud builds triggers update webhook (TRIGGER : --region=REGION)
    (--trigger-config=PATH | --description=DESCRIPTION
      --[no-]require-approval --secret=SECRET
      --service-account=SERVICE_ACCOUNT
      --subscription-filter=SUBSCRIPTION_FILTER --clear-substitutions
      | --remove-substitutions=[KEY,...]
      | --update-substitutions=[KEY=VALUE,...] --inline-config=PATH
      | [--dockerfile=DOCKERFILE : --dockerfile-dir=DOCKERFILE_DIR
      --dockerfile-image=DOCKERFILE_IMAGE]
      | --git-file-source-branch=GIT_FILE_SOURCE_BRANCH
      | --git-file-source-tag=GIT_FILE_SOURCE_TAG
      --git-file-source-github-enterprise-config=GIT_FILE_SOURCE_GITHUB_ENTERPRISE_CONFIG --git-file-source-path=PATH --git-file-source-repo-type=GIT_FILE_SOURCE_REPO_TYPE --git-file-source-uri=URL --source-to-build-branch=SOURCE_TO_BUILD_BRANCH | --source-to-build-tag=SOURCE_TO_BUILD_TAG --source-to-build-github-enterprise-config=SOURCE_TO_BUILD_GITHUB_ENTERPRISE_CONFIG --source-to-build-repo-type=SOURCE_TO_BUILD_REPO_TYPE --source-to-build-uri=SOURCE_TO_BUILD_URI)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Trigger resource - Build Trigger. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument TRIGGER on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TRIGGER
     ID of the trigger or fully qualified identifier for the trigger.

     To set the trigger attribute:
     + provide the argument TRIGGER on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud location for the trigger.

     To set the region attribute:
     + provide the argument TRIGGER on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property builds/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--trigger-config` | PATH |  | _[Exactly one of these must be specified:]_ Path to Build Trigger config file (JSON or YAML format). For more details, see https://cloud.google.com/cloud-build/docs/api/reference/rest/v1/projects.triggers#BuildTrigger |


**Examples:**
```bash
To update the branch from which the trigger clones:

    $ gcloud builds triggers update webhook my-webhook-trigger \
        --source-to-build-branch=my-branch

To update the webhook secret:

    $ gcloud builds triggers update webhook my-webhook-trigger \
        --secret=projects/my-project/secrets/my-secret/versions/2

To update the substitutions of the trigger:        $ gcloud builds triggers update webhook my-trigger \
        --update-substitutions=_REPO_NAME=my-repo,_BRANCH_NAME=master
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/triggers/update/webhook)

---
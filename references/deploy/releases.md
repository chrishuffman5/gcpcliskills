# gcloud deploy releases

create and manage Release resources for Cloud Deploy

### `gcloud deploy releases abandon`

Abandons a release

After a release is abandoned, no new rollouts can be created from it.

Rollouts of abandoned releases can't be rolled back to.

Existing rollouts of abandoned releases will be unaffected.

**Synopsis:**
```
gcloud deploy releases abandon
    (RELEASE : --delivery-pipeline=DELIVERY_PIPELINE --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Release resource - The name of the Release. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument release on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RELEASE
     ID of the release or fully qualified identifier for the release.

     To set the release attribute:
     + provide the argument release on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --delivery-pipeline=DELIVERY_PIPELINE
     The delivery pipeline associated with the release. Alternatively, set
     the property [deploy/delivery-pipeline].

     To set the delivery-pipeline attribute:
     + provide the argument release on the command line with a fully
       specified name;
     + provide the argument --delivery-pipeline on the command line;
     + set the property deploy/delivery_pipeline.

  --region=REGION
     The Cloud region for the release. Alternatively, set the property
     [deploy/region].

     To set the region attribute:
     + provide the argument release on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property deploy/region.
```

**Examples:**
```bash
To abandon a release called test-release for delivery pipeline
test-pipeline in region us-central1, run:

    $ gcloud deploy releases abandon test-release \
        --delivery-pipeline=test-pipeline --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/releases/abandon)

---
### `gcloud deploy releases create`

Creates a new release, delivery pipeline qualified

Creates a new release, delivery pipeline qualified.

**Synopsis:**
```
gcloud deploy releases create
    (RELEASE : --delivery-pipeline=DELIVERY_PIPELINE --region=REGION)
    [--annotations=[KEY=VALUE,...]] [--deploy-parameters=[KEY=VALUE,...]]
    [--description=DESCRIPTION] [--docker-version=DOCKER_VERSION]
    [--gcs-source-staging-dir=GCS_SOURCE_STAGING_DIR]
    [--helm-version=HELM_VERSION] [--ignore-file=IGNORE_FILE]
    [--kpt-version=KPT_VERSION] [--kubectl-version=KUBECTL_VERSION]
    [--kustomize-version=KUSTOMIZE_VERSION] [--labels=[KEY=VALUE,...]]
    [--override-deploy-policies=[POLICY,...]]
    [--skaffold-version=SKAFFOLD_VERSION] [--to-target=TO_TARGET]
    [--build-artifacts=BUILD_ARTIFACTS | --images=[NAME=TAG,...]]
    [--disable-initial-rollout | --enable-initial-rollout
      --initial-rollout-annotations=[KEY=VALUE,...]
      --initial-rollout-labels=[KEY=VALUE,...]
      --initial-rollout-phase-id=INITIAL_ROLLOUT_PHASE_ID]
    [--from-k8s-manifest=FROM_K8S_MANIFEST
      | --from-run-manifest=FROM_RUN_MANIFEST
      | --skaffold-file=SKAFFOLD_FILE --source=SOURCE; default="."]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Release resource - The name of the Release. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument release on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RELEASE
     ID of the release or fully qualified identifier for the release.

     To set the release attribute:
     + provide the argument release on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --delivery-pipeline=DELIVERY_PIPELINE
     The delivery pipeline associated with the release. Alternatively, set
     the property [deploy/delivery-pipeline].

     To set the delivery-pipeline attribute:
     + provide the argument release on the command line with a fully
       specified name;
     + provide the argument --delivery-pipeline on the command line;
     + set the property deploy/delivery_pipeline.

  --region=REGION
     The Cloud region for the release. Alternatively, set the property
     [deploy/region].

     To set the region attribute:
     + provide the argument release on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property deploy/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--annotations` | [KEY=VALUE,...] |  | Annotations to apply to the release. Annotations take the form of key/value string pairs. Examples: Add annotations: $ gcloud deploy releases create \ --annotations="from_target=test,status=stable" |
| `--deploy-parameters` | [KEY=VALUE,...] |  | Deployment parameters to apply to the release. Deployment parameters take the form of key/value string pairs. Examples: Add deployment parameters: $ gcloud deploy releases create \ --deploy-parameters="key1=value1,key2=value2" |
| `--description` | DESCRIPTION |  | Description of the release. |
| `--docker-version` | DOCKER_VERSION |  | Version of the Docker binary. |
| `--gcs-source-staging-dir` | GCS_SOURCE_STAGING_DIR |  | A directory in Google Cloud Storage to copy the source used for staging the build. If the specified bucket does not exist, Cloud Deploy will create one. If you don't set this field, gs://[DELIVERY_PIPELINE_ID]_clouddeploy/source is used. |
| `--helm-version` | HELM_VERSION |  | Version of the Helm binary. |
| `--ignore-file` | IGNORE_FILE |  | Override the .gcloudignore file and use the specified file instead. |
| `--kpt-version` | KPT_VERSION |  | Version of the Kpt binary. |
| `--kubectl-version` | KUBECTL_VERSION |  | Version of the Kubectl binary. |
| `--kustomize-version` | KUSTOMIZE_VERSION |  | Version of the Kustomize binary. |
| `--labels` | [KEY=VALUE,...] |  | Labels to apply to the release. Labels take the form of key/value string pairs. Examples: Add labels: $ gcloud deploy releases create --labels="commit=abc123,author=foo" |
| `--override-deploy-policies` | [POLICY,...] |  | Deploy policies to override |
| `--skaffold-version` | SKAFFOLD_VERSION |  | Version of the Skaffold binary. |
| `--to-target` | TO_TARGET |  | Specifies a target to deliver into upon release creation |


**Examples:**
```bash
To create a release with source located at storage URL
gs://bucket/object.zip and the first rollout in the first target of the
promotion sequence:

    $ gcloud deploy releases create my-release \
       --source=`gs://bucket/object.zip` \
       --delivery-pipeline=my-pipeline --region=us-central1

To create a release with source located at current directory and deploy a
rollout to target prod :

    $ gcloud deploy releases create my-release \
        --delivery-pipeline=my-pipeline --region=us-central1 \
        --to-target=prod

The following command creates a release without a skaffold.yaml as input,
and generates one for you:

    $ gcloud deploy releases create my-release \
        --delivery-pipeline=my-pipeline --region=us-central1 \
        --from-k8s-manifest=path/to/kubernetes/k8.yaml

The current UTC date and time on the machine running the gcloud command can
also be included in the release name by adding $DATE and $TIME parameters:

    $ gcloud deploy releases create 'my-release-$DATE-$TIME' \
        --delivery-pipeline=my-pipeline --region=us-central1

If the current UTC date and time is set to 2021-12-21 12:02, then the
created release will have its name set as my-release-20211221-1202.

When using these parameters, please be sure to wrap the release name in
single quotes or else the template parameters will be overridden by
environment variables.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/releases/create)

---
### `gcloud deploy releases describe`

Show details about a release

Show details a specified release.

**Synopsis:**
```
gcloud deploy releases describe
    (RELEASE : --delivery-pipeline=DELIVERY_PIPELINE --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Release resource - The release you want to describe. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument release on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RELEASE
     ID of the release or fully qualified identifier for the release.

     To set the release attribute:
     + provide the argument release on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --delivery-pipeline=DELIVERY_PIPELINE
     The name of the Cloud Deploy delivery pipeline.

     To set the delivery-pipeline attribute:
     + provide the argument release on the command line with a fully
       specified name;
     + provide the argument --delivery-pipeline on the command line;
     + set the property deploy/delivery_pipeline.

  --region=REGION
     Location of the release.

     To set the region attribute:
     + provide the argument release on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property deploy/region.
```

**Examples:**
```bash
To show details about the release 'test-release', for delivery pipeline
'test-pipeline', in region 'us-central1', run:

    $ gcloud deploy releases describe test-release \
        --delivery-pipeline=test-pipeline --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/releases/describe)

---
### `gcloud deploy releases list`

List releases

List the releases for a specified delivery pipeline.

**Synopsis:**
```
gcloud deploy releases list
    [--delivery-pipeline=DELIVERY_PIPELINE --region=REGION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--delivery-pipeline` | DELIVERY_PIPELINE |  | _[* set the property core/project.]_ ID of the delivery_pipeline or fully qualified identifier for the delivery_pipeline. To set the delivery-pipeline attribute: + provide the argument --delivery-pipeline on the command line; + set the property deploy/delivery_pipeline. |
| `--region` | REGION |  | _[* set the property core/project.]_ Location of the delivery_pipeline. To set the region attribute: + provide the argument --delivery-pipeline on the command line with a fully specified name; + set the property deploy/delivery_pipeline with a fully specified name; + provide the argument --region on the command line; + set the property deploy/region. |


**Examples:**
```bash
To list the releases for delivery pipeline 'test-pipeline', in region
'us-central1', run:

    $ gcloud deploy releases list --delivery-pipeline=test-pipeline \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/releases/list)

---
### `gcloud deploy releases promote`

Promotes a release from one target (source), to another (destination)

If to-target is not specified the command promotes the release from the
target that is farthest along in the promotion sequence to its next stage
in the promotion sequence.

**Synopsis:**
```
gcloud deploy releases promote
    (--release=RELEASE
      : --delivery-pipeline=DELIVERY_PIPELINE --region=REGION)
    [--annotations=[KEY=VALUE,...]] [--labels=[KEY=VALUE,...]]
    [--override-deploy-policies=[POLICY,...]] [--rollout-id=ROLLOUT_ID]
    [--starting-phase-id=STARTING_PHASE_ID] [--to-target=TO_TARGET]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--release` | RELEASE |  | _[This must be specified.]_ ID of the release or fully qualified identifier for the release. To set the release attribute: + provide the argument --release on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--delivery-pipeline` | DELIVERY_PIPELINE |  | _[This must be specified.]_ The delivery pipeline associated with the release. Alternatively, set the property [deploy/delivery-pipeline]. To set the delivery-pipeline attribute: + provide the argument --release on the command line with a fully specified name; + provide the argument --delivery-pipeline on the command line; + set the property deploy/delivery_pipeline. |
| `--region` | REGION |  | _[This must be specified.]_ The Cloud region for the release. Alternatively, set the property [deploy/region]. To set the region attribute: + provide the argument --release on the command line with a fully specified name; + provide the argument --region on the command line; + set the property deploy/region. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--annotations` | [KEY=VALUE,...] |  | Annotations to apply to the rollout. Annotations take the form of key/value string pairs. Examples: Add annotations: $ gcloud deploy releases promote \ --annotations="from_target=test,status=stable" |
| `--labels` | [KEY=VALUE,...] |  | Labels to apply to the rollout. Labels take the form of key/value string pairs. Examples: Add labels: $ gcloud deploy releases promote --labels="commit=abc123,author=foo" |
| `--override-deploy-policies` | [POLICY,...] |  | Deploy policies to override |
| `--rollout-id` | ROLLOUT_ID |  | ID to assign to the generated rollout for promotion. |
| `--starting-phase-id` | STARTING_PHASE_ID |  | If set, starts the created rollout at the specified phase. Start rollout at stable phase: $ gcloud deploy releases promote --starting-phase-id=stable |
| `--to-target` | TO_TARGET |  | Destination target to promote into. |


**Examples:**
```bash
To promote a release called 'test-release' for delivery pipeline
'test-pipeline' in region 'us-central1' to target 'prod', run:

    $ gcloud deploy releases promote --release=test-release \
        --delivery-pipeline=test-pipeline --region=us-central1 \
        --to-target=prod
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/releases/promote)

---
# gcloud deploy rollouts

create and manage Rollout resources for Cloud Deploy

### `gcloud deploy rollouts advance`

Advances a rollout

Advances a rollout.

**Synopsis:**
```
gcloud deploy rollouts advance
    (ROLLOUT : --delivery-pipeline=DELIVERY_PIPELINE
      --region=REGION --release=RELEASE)
    [--override-deploy-policies=[POLICY,...]] [--phase-id=PHASE_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Rollout resource - The name of the Rollout. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument rollout on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ROLLOUT
     ID of the rollout or fully qualified identifier for the rollout.

     To set the rollout attribute:
     + provide the argument rollout on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --delivery-pipeline=DELIVERY_PIPELINE
     The delivery pipeline associated with the rollout. Alternatively, set
     the property [deploy/delivery-pipeline].

     To set the delivery-pipeline attribute:
     + provide the argument rollout on the command line with a fully
       specified name;
     + provide the argument --delivery-pipeline on the command line;
     + set the property deploy/delivery_pipeline.

  --region=REGION
     The Cloud region for the rollout. Alternatively, set the property
     [deploy/region].

     To set the region attribute:
     + provide the argument rollout on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property deploy/region.

  --release=RELEASE
     The release associated with the rollout.

     To set the release attribute:
     + provide the argument rollout on the command line with a fully
       specified name;
     + provide the argument --release on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--override-deploy-policies` | [POLICY,...] |  | Deploy policies to override |
| `--phase-id` | PHASE_ID |  | Phase ID on a rollout resource |


**Examples:**
```bash
To advance a rollout test-rollout to phase test-phase for delivery pipeline
test-pipeline, release test-release in region us-central1, run:

    $ gcloud deploy rollouts advance test-rollout \
         --phase-id=test-phase --delivery-pipeline=test-pipeline \
         --release=test-release --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/rollouts/advance)

---
### `gcloud deploy rollouts approve`

Approves a rollout having an Approval state of "Required"

Approves a rollout having an Approval state of "Required".

**Synopsis:**
```
gcloud deploy rollouts approve
    (ROLLOUT : --delivery-pipeline=DELIVERY_PIPELINE
      --region=REGION --release=RELEASE)
    [--override-deploy-policies=[POLICY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Rollout resource - The name of the Rollout. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument rollout on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ROLLOUT
     ID of the rollout or fully qualified identifier for the rollout.

     To set the rollout attribute:
     + provide the argument rollout on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --delivery-pipeline=DELIVERY_PIPELINE
     The delivery pipeline associated with the rollout. Alternatively, set
     the property [deploy/delivery-pipeline].

     To set the delivery-pipeline attribute:
     + provide the argument rollout on the command line with a fully
       specified name;
     + provide the argument --delivery-pipeline on the command line;
     + set the property deploy/delivery_pipeline.

  --region=REGION
     The Cloud region for the rollout. Alternatively, set the property
     [deploy/region].

     To set the region attribute:
     + provide the argument rollout on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property deploy/region.

  --release=RELEASE
     The release associated with the rollout.

     To set the release attribute:
     + provide the argument rollout on the command line with a fully
       specified name;
     + provide the argument --release on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--override-deploy-policies` | [POLICY,...] |  | Deploy policies to override |


**Examples:**
```bash
To approve a rollout 'test-rollout' for delivery pipeline 'test-pipeline',
release 'test-release' in region 'us-central1', run:

    $ gcloud deploy rollouts approve test-rollout \
        --delivery-pipeline=test-pipeline --release=test-release \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/rollouts/approve)

---
### `gcloud deploy rollouts cancel`

Cancel a Rollout

Cancel a Rollout.

**Synopsis:**
```
gcloud deploy rollouts cancel
    (ROLLOUT : --delivery-pipeline=DELIVERY_PIPELINE
      --region=REGION --release=RELEASE)
    [--override-deploy-policies=[POLICY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Rollout resource - The name of the Rollout. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument rollout on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ROLLOUT
     ID of the rollout or fully qualified identifier for the rollout.

     To set the rollout attribute:
     + provide the argument rollout on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --delivery-pipeline=DELIVERY_PIPELINE
     The delivery pipeline associated with the rollout. Alternatively, set
     the property [deploy/delivery-pipeline].

     To set the delivery-pipeline attribute:
     + provide the argument rollout on the command line with a fully
       specified name;
     + provide the argument --delivery-pipeline on the command line;
     + set the property deploy/delivery_pipeline.

  --region=REGION
     The Cloud region for the rollout. Alternatively, set the property
     [deploy/region].

     To set the region attribute:
     + provide the argument rollout on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property deploy/region.

  --release=RELEASE
     The release associated with the rollout.

     To set the release attribute:
     + provide the argument rollout on the command line with a fully
       specified name;
     + provide the argument --release on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--override-deploy-policies` | [POLICY,...] |  | Deploy policies to override |


**Examples:**
```bash
To cancel a rollout test-rollout for delivery pipeline test-pipeline,
release test-release in region us-central1, run:

    $ gcloud deploy rollouts cancel test-rollout \
         --delivery-pipeline=test-pipeline --release=test-release \
         --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/rollouts/cancel)

---
### `gcloud deploy rollouts describe`

Show details for a rollout

Show details for a specified rollout.

**Synopsis:**
```
gcloud deploy rollouts describe
    (ROLLOUT : --delivery-pipeline=DELIVERY_PIPELINE
      --region=REGION --release=RELEASE) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Rollout resource - The name of the rollout you want to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument rollout on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ROLLOUT
     ID of the rollout or fully qualified identifier for the rollout.

     To set the rollout attribute:
     + provide the argument rollout on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --delivery-pipeline=DELIVERY_PIPELINE
     The name of the Cloud Deploy delivery pipeline.

     To set the delivery-pipeline attribute:
     + provide the argument rollout on the command line with a fully
       specified name;
     + provide the argument --delivery-pipeline on the command line;
     + set the property deploy/delivery_pipeline.

  --region=REGION
     Location of the rollout.

     To set the region attribute:
     + provide the argument rollout on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property deploy/region.

  --release=RELEASE
     The name of the Cloud Deploy release.

     To set the release attribute:
     + provide the argument rollout on the command line with a fully
       specified name;
     + provide the argument --release on the command line.
```

**Examples:**
```bash
To show details about a rollout 'test-rollout', for delivery pipeline
'test-pipeline', and release 'test-release' in region 'us-central1', run:

    $ gcloud deploy rollouts describe test-rollout \
        --delivery-pipeline=test-pipeline --release=test-release \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/rollouts/describe)

---
### `gcloud deploy rollouts ignore-job`

Ignores a specified job and phase combination on a rollout

Ignores a specified job and phase combination on a rollout.

**Synopsis:**
```
gcloud deploy rollouts ignore-job
    (ROLLOUT : --delivery-pipeline=DELIVERY_PIPELINE
      --region=REGION --release=RELEASE) --job-id=JOB_ID
    --phase-id=PHASE_ID [--override-deploy-policies=[POLICY,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Rollout resource - The name of the Rollout. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument rollout on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ROLLOUT
     ID of the rollout or fully qualified identifier for the rollout.

     To set the rollout attribute:
     + provide the argument rollout on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --delivery-pipeline=DELIVERY_PIPELINE
     The delivery pipeline associated with the rollout. Alternatively, set
     the property [deploy/delivery-pipeline].

     To set the delivery-pipeline attribute:
     + provide the argument rollout on the command line with a fully
       specified name;
     + provide the argument --delivery-pipeline on the command line;
     + set the property deploy/delivery_pipeline.

  --region=REGION
     The Cloud region for the rollout. Alternatively, set the property
     [deploy/region].

     To set the region attribute:
     + provide the argument rollout on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property deploy/region.

  --release=RELEASE
     The release associated with the rollout.

     To set the release attribute:
     + provide the argument rollout on the command line with a fully
       specified name;
     + provide the argument --release on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--job-id` | JOB_ID |  | Job ID on a rollout resource |
| `--phase-id` | PHASE_ID |  | Phase ID on a rollout resource |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--override-deploy-policies` | [POLICY,...] |  | Deploy policies to override |


**Examples:**
```bash
To ignore a job test-job in phase test-phase on a rollout test-rollout for
delivery pipeline test-pipeline, release test-release in region
us-central1, run:

    $ gcloud deploy rollouts ignore-job test-rollout --job-id=test-job \
         --phase-id=test-phase --delivery-pipeline=test-pipeline \
         --release=test-release --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/rollouts/ignore-job)

---
### `gcloud deploy rollouts list`

List the rollouts

List the rollouts for a specified delivery pipeline.

**Synopsis:**
```
gcloud deploy rollouts list
    (--release=RELEASE
      : --delivery-pipeline=DELIVERY_PIPELINE --region=REGION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--release` | RELEASE |  | _[This must be specified.]_ ID of the release or fully qualified identifier for the release. To set the release attribute: + provide the argument --release on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--delivery-pipeline` | DELIVERY_PIPELINE |  | _[This must be specified.]_ The name of the Cloud Deploy delivery pipeline. To set the delivery-pipeline attribute: + provide the argument --release on the command line with a fully specified name; + provide the argument --delivery-pipeline on the command line; + set the property deploy/delivery_pipeline. |
| `--region` | REGION |  | _[This must be specified.]_ Location of the release. To set the region attribute: + provide the argument --release on the command line with a fully specified name; + provide the argument --region on the command line; + set the property deploy/region. |


**Examples:**
```bash
To list the rollouts for delivery pipeline 'test-pipeline' and release
'test-release' in region 'us-central1', run:

    $ gcloud deploy rollouts list --delivery-pipeline=test-pipeline \
        --release=test-release --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/rollouts/list)

---
### `gcloud deploy rollouts reject`

Rejects a rollout having an Approval state of "Required"

Rejects a rollout having an Approval state of "Required".

**Synopsis:**
```
gcloud deploy rollouts reject
    (ROLLOUT : --delivery-pipeline=DELIVERY_PIPELINE
      --region=REGION --release=RELEASE)
    [--override-deploy-policies=[POLICY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Rollout resource - The name of the Rollout. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument rollout on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ROLLOUT
     ID of the rollout or fully qualified identifier for the rollout.

     To set the rollout attribute:
     + provide the argument rollout on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --delivery-pipeline=DELIVERY_PIPELINE
     The delivery pipeline associated with the rollout. Alternatively, set
     the property [deploy/delivery-pipeline].

     To set the delivery-pipeline attribute:
     + provide the argument rollout on the command line with a fully
       specified name;
     + provide the argument --delivery-pipeline on the command line;
     + set the property deploy/delivery_pipeline.

  --region=REGION
     The Cloud region for the rollout. Alternatively, set the property
     [deploy/region].

     To set the region attribute:
     + provide the argument rollout on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property deploy/region.

  --release=RELEASE
     The release associated with the rollout.

     To set the release attribute:
     + provide the argument rollout on the command line with a fully
       specified name;
     + provide the argument --release on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--override-deploy-policies` | [POLICY,...] |  | Deploy policies to override |


**Examples:**
```bash
To reject a rollout 'test-rollout' for delivery pipeline 'test-pipeline',
release 'test-release' in region 'us-central1', run:

    $ gcloud deploy rollouts reject test-rollout \
         --delivery-pipeline=test-pipeline --release=test-release \
         --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/rollouts/reject)

---
### `gcloud deploy rollouts retry-job`

Retries a specified job, phase combination on a rollout

Retries a specified job, phase combination on a rollout.

**Synopsis:**
```
gcloud deploy rollouts retry-job
    (ROLLOUT : --delivery-pipeline=DELIVERY_PIPELINE
      --region=REGION --release=RELEASE) --job-id=JOB_ID
    --phase-id=PHASE_ID [--override-deploy-policies=[POLICY,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Rollout resource - The name of the Rollout. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument rollout on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ROLLOUT
     ID of the rollout or fully qualified identifier for the rollout.

     To set the rollout attribute:
     + provide the argument rollout on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --delivery-pipeline=DELIVERY_PIPELINE
     The delivery pipeline associated with the rollout. Alternatively, set
     the property [deploy/delivery-pipeline].

     To set the delivery-pipeline attribute:
     + provide the argument rollout on the command line with a fully
       specified name;
     + provide the argument --delivery-pipeline on the command line;
     + set the property deploy/delivery_pipeline.

  --region=REGION
     The Cloud region for the rollout. Alternatively, set the property
     [deploy/region].

     To set the region attribute:
     + provide the argument rollout on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property deploy/region.

  --release=RELEASE
     The release associated with the rollout.

     To set the release attribute:
     + provide the argument rollout on the command line with a fully
       specified name;
     + provide the argument --release on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--job-id` | JOB_ID |  | Job ID on a rollout resource |
| `--phase-id` | PHASE_ID |  | Phase ID on a rollout resource |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--override-deploy-policies` | [POLICY,...] |  | Deploy policies to override |


**Examples:**
```bash
To retry a job 'test-job' in phase 'test-phase' on a rollout 'test-rollout'
for delivery pipeline 'test-pipeline', release 'test-release' in region
'us-central1', run:

    $ gcloud deploy rollouts retry-job test-rollout --job-id=test-job \
         --phase-id=test-phase --delivery-pipeline=test-pipeline \
         --release=test-release --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/rollouts/retry-job)

---
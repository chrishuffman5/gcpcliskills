# gcloud deploy job-runs

manages job runs resources for Cloud Deploy

### `gcloud deploy job-runs describe`

Show details for a job run

Show details for a specified job run.

**Synopsis:**
```
gcloud deploy job-runs describe
    (JOB_RUN : --delivery-pipeline=DELIVERY_PIPELINE
      --region=REGION --release=RELEASE --rollout=ROLLOUT)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job run resource - The name of the job run you want to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument job_run on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  JOB_RUN
     ID of the job run or fully qualified identifier for the job run.

     To set the job_run attribute:
     + provide the argument job_run on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --delivery-pipeline=DELIVERY_PIPELINE
     The name of the Cloud Deploy delivery pipeline.

     To set the delivery-pipeline attribute:
     + provide the argument job_run on the command line with a fully
       specified name;
     + provide the argument --delivery-pipeline on the command line;
     + set the property deploy/delivery_pipeline.

  --region=REGION
     Location of the job run.

     To set the region attribute:
     + provide the argument job_run on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property deploy/region.

  --release=RELEASE
     The name of the Cloud Deploy release.

     To set the release attribute:
     + provide the argument job_run on the command line with a fully
       specified name;
     + provide the argument --release on the command line.

  --rollout=ROLLOUT
     The name of the Cloud Deploy rollout.

     To set the rollout attribute:
     + provide the argument job_run on the command line with a fully
       specified name;
     + provide the argument --rollout on the command line.
```

**Examples:**
```bash
To show details about a job run 'test-jobrun', for delivery pipeline
'test-pipeline', release 'test-release', rollout 'test-rollout', in region
'us-central1', run:

    $ gcloud deploy job-runs describe test-jobrun \
        --delivery-pipeline=test-pipeline --release=test-release \
        --rollout=test-rollout --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/job-runs/describe)

---
### `gcloud deploy job-runs list`

List the job runs

List the job runs for a specified delivery pipeline.

**Synopsis:**
```
gcloud deploy job-runs list
    (--rollout=ROLLOUT : --delivery-pipeline=DELIVERY_PIPELINE
      --region=REGION --release=RELEASE) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--rollout` | ROLLOUT |  | _[This must be specified.]_ ID of the rollout or fully qualified identifier for the rollout. To set the rollout attribute: + provide the argument --rollout on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--delivery-pipeline` | DELIVERY_PIPELINE |  | _[This must be specified.]_ The name of the Cloud Deploy delivery pipeline. To set the delivery-pipeline attribute: + provide the argument --rollout on the command line with a fully specified name; + provide the argument --delivery-pipeline on the command line; + set the property deploy/delivery_pipeline. |
| `--region` | REGION |  | _[This must be specified.]_ Location of the rollout. To set the region attribute: + provide the argument --rollout on the command line with a fully specified name; + provide the argument --region on the command line; + set the property deploy/region. |
| `--release` | RELEASE |  | _[This must be specified.]_ The name of the Cloud Deploy release. To set the release attribute: + provide the argument --rollout on the command line with a fully specified name; + provide the argument --release on the command line. |


**Examples:**
```bash
To list the job runs for delivery pipeline 'test-pipeline', release
'test-release', and rollout 'test-rollout' in region 'us-central1', run:

    $ gcloud deploy job-runs list --delivery-pipeline=test-pipeline \
        --release=test-release --rollout=test-rollout \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/job-runs/list)

---
### `gcloud deploy job-runs terminate`

Terminates a Cloud Deploy job run

Terminates a Cloud Deploy job run.

**Synopsis:**
```
gcloud deploy job-runs terminate
    (JOB_RUN : --delivery-pipeline=DELIVERY_PIPELINE
      --region=REGION --release=RELEASE --rollout=ROLLOUT)
    [--override-deploy-policies=[POLICY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job run resource - The name of the Job Run. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument job_run on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  JOB_RUN
     ID of the job_run or fully qualified identifier for the job_run.

     To set the name attribute:
     + provide the argument job_run on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --delivery-pipeline=DELIVERY_PIPELINE
     The delivery pipeline associated with the job_run. Alternatively, set
     the property [deploy/delivery-pipeline].

     To set the delivery-pipeline attribute:
     + provide the argument job_run on the command line with a fully
       specified name;
     + provide the argument --delivery-pipeline on the command line;
     + set the property deploy/delivery_pipeline.

  --region=REGION
     The Cloud region for the job_run. Alternatively, set the property
     [deploy/region].

     To set the region attribute:
     + provide the argument job_run on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property deploy/region.

  --release=RELEASE
     The release associated with the job_run.

     To set the release attribute:
     + provide the argument job_run on the command line with a fully
       specified name;
     + provide the argument --release on the command line.

  --rollout=ROLLOUT
     The rollout associated with the job_run.

     To set the rollout attribute:
     + provide the argument job_run on the command line with a fully
       specified name;
     + provide the argument --rollout on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--override-deploy-policies` | [POLICY,...] |  | Deploy policies to override |


**Examples:**
```bash
To terminate a job run test-jobrun, for delivery pipeline 'test-pipeline',
release 'test-release', rollout 'test-rollout', in region 'us-central1',
run:

    $ gcloud deploy job-runs terminate test-jobrun \
         --delivery-pipeline=test-pipeline --release=test-release \
         --rollout=test-rollout --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/job-runs/terminate)

---
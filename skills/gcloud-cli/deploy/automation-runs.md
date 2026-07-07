# gcloud deploy automation-runs

manages AutomationRuns resources for Cloud Deploy

### `gcloud deploy automation-runs cancel`

Cancels a Cloud Deploy Automation Run

Cancels a Cloud Deploy Automation Run.

**Synopsis:**
```
gcloud deploy automation-runs cancel
    (AUTOMATION_RUN
      : --delivery-pipeline=DELIVERY_PIPELINE --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Automation run resource - The name of the AutomationRun. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument automation_run on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  AUTOMATION_RUN
     ID of the automation_run or fully qualified identifier for the
     automation_run.

     To set the name attribute:
     + provide the argument automation_run on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --delivery-pipeline=DELIVERY_PIPELINE
     The delivery pipeline associated with the automation_run.
     Alternatively, set the property [deploy/delivery-pipeline].

     To set the delivery-pipeline attribute:
     + provide the argument automation_run on the command line with a
       fully specified name;
     + provide the argument --delivery-pipeline on the command line;
     + set the property deploy/delivery_pipeline.

  --region=REGION
     The Cloud region for the automation_run. Alternatively, set the
     property [deploy/region].

     To set the region attribute:
     + provide the argument automation_run on the command line with a
       fully specified name;
     + provide the argument --region on the command line;
     + set the property deploy/region.
```

**Examples:**
```bash
To cancel an AutomationRun test-run for delivery pipeline test-pipeline in
region us-central1, run:

    $ gcloud deploy automation-runs cancel test-run \
         --delivery-pipeline=test-pipeline --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/automation-runs/cancel)

---
### `gcloud deploy automation-runs describe`

Show details for an Automation Run

Show details for a specified automation run.

**Synopsis:**
```
gcloud deploy automation-runs describe
    (AUTOMATION_RUN
      : --delivery-pipeline=DELIVERY_PIPELINE --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Automation run resource - The name of the automation run you want to
describe. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument automation_run on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  AUTOMATION_RUN
     ID of the automation run or fully qualified identifier for the
     automation run.

     To set the automation_run attribute:
     + provide the argument automation_run on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --delivery-pipeline=DELIVERY_PIPELINE
     The name of the Cloud Deploy delivery pipeline.

     To set the delivery-pipeline attribute:
     + provide the argument automation_run on the command line with a
       fully specified name;
     + provide the argument --delivery-pipeline on the command line;
     + set the property deploy/delivery_pipeline.

  --region=REGION
     Location of the automation run.

     To set the region attribute:
     + provide the argument automation_run on the command line with a
       fully specified name;
     + provide the argument --region on the command line;
     + set the property deploy/region.
```

**Examples:**
```bash
To show details about a automation run 'test-automationrun', for delivery
pipeline 'test-pipeline', in region 'us-central1', run:

    $ gcloud deploy automation-runs describe test-automationrun \
        --delivery-pipeline=test-pipeline --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/automation-runs/describe)

---
### `gcloud deploy automation-runs list`

List the Automation Runs

List the automation runs for a specified delivery pipeline.

**Synopsis:**
```
gcloud deploy automation-runs list
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
To list the automation runs for delivery pipeline 'test-pipeline' in region
'us-central1', run:

    $ gcloud deploy automation-runs list \
        --delivery-pipeline=test-pipeline --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/automation-runs/list)

---
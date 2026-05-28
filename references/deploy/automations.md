# gcloud deploy automations

manages Automations resources for Cloud Deploy

### `gcloud deploy automations delete`

Deletes a Cloud Deploy Automation

Deletes a Cloud Deploy Automation.

**Synopsis:**
```
gcloud deploy automations delete
    (AUTOMATION : --delivery-pipeline=DELIVERY_PIPELINE --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Automation resource - The name of the Automation. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument automation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  AUTOMATION
     ID of the automation or fully qualified identifier for the
     automation.

     To set the name attribute:
     + provide the argument automation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --delivery-pipeline=DELIVERY_PIPELINE
     The delivery pipeline associated with the automation. Alternatively,
     set the property [deploy/delivery-pipeline].

     To set the delivery-pipeline attribute:
     + provide the argument automation on the command line with a fully
       specified name;
     + provide the argument --delivery-pipeline on the command line;
     + set the property deploy/delivery_pipeline.

  --region=REGION
     The Cloud region for the automation. Alternatively, set the property
     [deploy/region].

     To set the region attribute:
     + provide the argument automation on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property deploy/region.
```

**Examples:**
```bash
To delete an automation test-automation for delivery pipeline
test-pipeline, in region us-central1, run:

    $ gcloud deploy automations delete test-automation \
        --delivery-pipeline=test-pipeline --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/automations/delete)

---
### `gcloud deploy automations describe`

Show details for an Automation

Show details for a specified automation.

**Synopsis:**
```
gcloud deploy automations describe
    (AUTOMATION : --delivery-pipeline=DELIVERY_PIPELINE --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Automation resource - The name of the automation you want to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument automation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  AUTOMATION
     ID of the automation or fully qualified identifier for the
     automation.

     To set the automation attribute:
     + provide the argument automation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --delivery-pipeline=DELIVERY_PIPELINE
     The name of the Cloud Deploy delivery pipeline.

     To set the delivery-pipeline attribute:
     + provide the argument automation on the command line with a fully
       specified name;
     + provide the argument --delivery-pipeline on the command line;
     + set the property deploy/delivery_pipeline.

  --region=REGION
     Location of the automation.

     To set the region attribute:
     + provide the argument automation on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property deploy/region.
```

**Examples:**
```bash
To show details about an automation 'test-automation', for delivery
pipeline 'test-pipeline', in region 'us-central1', run:

    $ gcloud deploy automations describe test-automation \
        --delivery-pipeline=test-pipeline --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/automations/describe)

---
### `gcloud deploy automations export`

Returns the YAML definition of the specified Automation

The exported yaml definition can be applied by using the deploy apply
command.

**Synopsis:**
```
gcloud deploy automations export
    (AUTOMATION : --delivery-pipeline=DELIVERY_PIPELINE --region=REGION)
    [--destination=DESTINATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Automation resource - The name of the Automation. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument automation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  AUTOMATION
     ID of the automation or fully qualified identifier for the
     automation.

     To set the name attribute:
     + provide the argument automation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --delivery-pipeline=DELIVERY_PIPELINE
     The delivery pipeline associated with the automation. Alternatively,
     set the property [deploy/delivery-pipeline].

     To set the delivery-pipeline attribute:
     + provide the argument automation on the command line with a fully
       specified name;
     + provide the argument --delivery-pipeline on the command line;
     + set the property deploy/delivery_pipeline.

  --region=REGION
     The Cloud region for the automation. Alternatively, set the property
     [deploy/region].

     To set the region attribute:
     + provide the argument automation on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property deploy/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | Path to a YAML file where the configuration will be exported. Alternatively, you may omit this flag to write to standard output. |


**Examples:**
```bash
To return the YAML definition of the automation test-automation of delivery
pipeline test-pipeline, in region us-central1, run:

    $ gcloud deploy automations export test-automation \
        --delivery-pipeline=test-pipeline --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/automations/export)

---
### `gcloud deploy automations list`

List the Automations

List the automations for a specified delivery pipeline.

**Synopsis:**
```
gcloud deploy automations list
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
To list the automations for delivery pipeline 'test-pipeline' in region
'us-central1', run:

    $ gcloud deploy automations list --delivery-pipeline=test-pipeline \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/automations/list)

---
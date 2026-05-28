# gcloud assured workloads

read and manipulate Assured Workloads resources

### `gcloud assured workloads create`

Create a new Assured Workloads environment

**Synopsis:**
```
gcloud assured workloads create --billing-account=BILLING_ACCOUNT
    --compliance-regime=COMPLIANCE_REGIME --display-name=DISPLAY_NAME
    --location=LOCATION --organization=ORGANIZATION
    [--enable-sovereign-controls=ENABLE_SOVEREIGN_CONTROLS]
    [--external-identifier=EXTERNAL_IDENTIFIER] [--labels=[KEY=VALUE,...]]
    [--next-rotation-time=NEXT_ROTATION_TIME] [--partner=PARTNER]
    [--partner-permissions=[KEY=VALUE,...]]
    [--partner-services-billing-account=PARTNER_SERVICES_BILLING_ACCOUNT]
    [--provisioned-resources-parent=PROVISIONED_RESOURCES_PARENT]
    [--resource-settings=[KEY=VALUE,...]]
    [--rotation-period=ROTATION_PERIOD] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--billing-account` | BILLING_ACCOUNT |  | The billing account of the new Assured Workloads environment, for example, billingAccounts/0000AA-AAA00A-A0A0A0 |
| `--compliance-regime` | one of: assured-workloads-for-partners, au-regions-and-us-support, australia-data-boundary-and-support, ca-protected-b, ca-regions-and-support, canada-controlled-goods, canada-data-boundary-and-support, cjis, data-boundary-for-canada-controlled-goods, data-boundary-for-canada-protected-b, data-boundary-for-cjis, data-boundary-for-fedramp-high, data-boundary-for-fedramp-moderate, data-boundary-for-il2, data-boundary-for-il4, data-boundary-for-il5, data-boundary-for-irs-publication-1075, data-boundary-for-itar, eu-data-boundary-and-support, eu-regions-and-support, fedramp-high, fedramp-moderate, healthcare-and-life-sciences-controls, healthcare-and-life-sciences-controls-us-support, hipaa, hitrust, il2, il4, il5, irs-1075, isr-regions, isr-regions-and-support, israel-data-boundary-and-support, itar, japan-data-boundary, jp-regions-and-support, ksa-data-boundary-with-access-justifications, ksa-regions-and-support-with-sovereignty-controls, regional-controls, regional-data-boundary, us-data-boundary-and-support, us-data-boundary-for-healthcare-and-life-sciences, us-data-boundary-for-healthcare-and-life-sciences-with-support, us-regional-access |  | The compliance regime of the new Assured Workloads environment. COMPLIANCE_REGIME must be one of: assured-workloads-for-partners, au-regions-and-us-support, australia-data-boundary-and-support, ca-protected-b, ca-regions-and-support, canada-controlled-goods, canada-data-boundary-and-support, cjis, data-boundary-for-canada-controlled-goods, data-boundary-for-canada-protected-b, data-boundary-for-cjis, data-boundary-for-fedramp-high, data-boundary-for-fedramp-moderate, data-boundary-for-il2, data-boundary-for-il4, data-boundary-for-il5, data-boundary-for-irs-publication-1075, data-boundary-for-itar, eu-data-boundary-and-support, eu-regions-and-support, fedramp-high, fedramp-moderate, healthcare-and-life-sciences-controls, healthcare-and-life-sciences-controls-us-support, hipaa, hitrust, il2, il4, il5, irs-1075, isr-regions, isr-regions-and-support, israel-data-boundary-and-support, itar, japan-data-boundary, jp-regions-and-support, ksa-data-boundary-with-access-justifications, ksa-regions-and-support-with-sovereignty-controls, regional-controls, regional-data-boundary, us-data-boundary-and-support, us-data-boundary-for-healthcare-and-life-sciences, us-data-boundary-for-healthcare-and-life-sciences-with-support, us-regional-access. |
| `--display-name` | DISPLAY_NAME |  | The display name of the new Assured Workloads environment |
| `--location` | LOCATION |  | The location of the new Assured Workloads environment. For a current list of supported LOCATION values, see Assured Workloads locations (https://cloud.google.com/assured-workloads/docs/locations). |
| `--organization` | ORGANIZATION |  | The parent organization of the new Assured Workloads environment, provided as an organization ID |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--enable-sovereign-controls` | ENABLE_SOVEREIGN_CONTROLS |  | If true, enable sovereign controls for the new Assured Workloads environment, currently only supported by EU_REGIONS_AND_SUPPORT |
| `--external-identifier` | EXTERNAL_IDENTIFIER |  | The external identifier of the new Assured Workloads environment |
| `--labels` | [KEY=VALUE,...] |  | The labels of the new Assured Workloads environment, for example, LabelKey1=LabelValue1,LabelKey2=LabelValue2 |
| `--next-rotation-time` | NEXT_ROTATION_TIME |  | The next rotation time of the KMS settings of new Assured Workloads environment, for example, 2020-12-30T10:15:30.00Z |
| `--partner` | one of: local-controls-by-s3ns, sovereign-controls-by-cntxt, sovereign-controls-by-cntxt-no-ekm, sovereign-controls-by-psn, sovereign-controls-by-sia-minsait, sovereign-controls-by-t-systems |  | The partner choice when creating a workload managed by local trusted partners. PARTNER must be one of: local-controls-by-s3ns, sovereign-controls-by-cntxt, sovereign-controls-by-cntxt-no-ekm, sovereign-controls-by-psn, sovereign-controls-by-sia-minsait, sovereign-controls-by-t-systems. |
| `--partner-permissions` | [KEY=VALUE,...] |  | The partner permissions for the partner regime, for example, data-logs-viewer=true/false |
| `--partner-services-billing-account` | PARTNER_SERVICES_BILLING_ACCOUNT |  | Billing account necessary for purchasing services from Sovereign Partners. This field is required for creating SIA/PSN/CNTXT partner workloads. The caller should have 'billing.resourceAssociations.create' IAM permission on this billing-account. The format of this string is billingAccounts/AAAAAA-BBBBBB-CCCCCC |
| `--provisioned-resources-parent` | PROVISIONED_RESOURCES_PARENT |  | The parent of the provisioned projects, for example, folders/{FOLDER_ID} |
| `--resource-settings` | [KEY=VALUE,...] |  | A comma-separated, key=value map of custom resource settings such as custom project ids, for example: consumer-project-id={CONSUMER_PROJECT_ID} Note: Currently only consumer-project-id, consumer-project-name, encryption-keys-project-id, encryption-keys-project-name and keyring-id are supported. The encryption-keys-project-id, encryption-keys-project-name and keyring-id settings can be specified only if KMS settings are provided |
| `--rotation-period` | ROTATION_PERIOD |  | The rotation period of the KMS settings of the new Assured Workloads environment, for example, 172800s |


**Examples:**
```bash
The following example command creates a new Assured Workloads environment
with these properties:

  o belonging to an organization with ID 123
  o located in the us-central1 region
  o display name Test-Workload
  o compliance regime FEDRAMP_MODERATE
  o billing account billingAccounts/456
  o first key rotation set for 10:15am on the December 30, 2020
  o key rotation interval set for every 48 hours
  o with the label: key = 'LabelKey1', value = 'LabelValue1'
  o with the label: key = 'LabelKey2', value = 'LabelValue2'
  o provisioned resources parent 'folders/789'
  o with custom project id 'my-custom-id' for consumer project
  o with external identifier for the workload of 'external-id'

    $ gcloud assured workloads create --organization=123 \
        --location=us-central1 --display-name=Test-Workload \
        --compliance-regime=FEDRAMP_MODERATE \
        --billing-account=billingAccounts/456 \
        --next-rotation-time=2020-12-30T10:15:00.00Z \
        --rotation-period=172800s \
        --labels=LabelKey1=LabelValue1,LabelKey2=LabelValue2 \
        --provisioned-resources-parent=folders/789 \
        --resource-settings=consumer-project-id=my-custom-id \
        --external-identifier=external-id

The following example command creates a new Partner Assured Workloads, with
the following properties:

  o belonging to an organization with ID 123
  o located in the me-central2 region
  o display name Test-Workload
  o partner CNTXT
  o partner services billing account billingAccounts/789
  o billing account billingAccounts/456
  o data logs viewer partner permission enabled
  o first key rotation set for 10:15am on the December 30, 2020
  o key rotation interval set for every 48 hours
  o with the label: key = 'LabelKey1', value = 'LabelValue1'
  o with the label: key = 'LabelKey2', value = 'LabelValue2'
  o provisioned resources parent 'folders/789'
  o with custom project id 'my-custom-id' for consumer project
  o with external identifier for the workload of 'external-id'

    $ gcloud assured workloads create --organization=123 \
        --location=me-central2 --display-name=Test-Workload \
        --compliance-regime=ASSURED_WORKLOADS_FOR_PARTNERS \
        --partner=SOVEREIGN_CONTROLS_BY_CNTXT \
        --partner-services-billing-account=billingAccounts/\
    01BF3F-2C6DE5-30C607 --partner-permissions=data-logs-viewer=true \
        --billing-account=billingAccounts/456 \
        --next-rotation-time=2020-12-30T10:15:00.00Z \
        --rotation-period=172800s \
        --labels=LabelKey1=LabelValue1,LabelKey2=LabelValue2 \
        --provisioned-resources-parent=folders/789 \
        --resource-settings=consumer-project-id=my-custom-id \
        --external-identifier=external-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/assured/workloads/create)

---
### `gcloud assured workloads delete`

Delete Assured Workloads environment

Delete a given Assured Workloads environment.

**Synopsis:**
```
gcloud assured workloads delete
    (WORKLOAD : --location=LOCATION --organization=ORGANIZATION)
    [--etag=ETAG] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload resource - The Assured Workloads environment resource to delete.
The arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  WORKLOAD
     ID of the workload or fully qualified identifier for the workload.

     To set the workload attribute:
     + provide the argument workload on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the workload.

     To set the location attribute:
     + provide the argument workload on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The parent organization for the workload.

     To set the organization attribute:
     + provide the argument workload on the command line with a fully
       specified name;
     + provide the argument --organization on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--etag` | ETAG |  | The etag acquired by reading the Assured Workloads environment or AW "resource". |


**Examples:**
```bash
To delete an Assured Workload environment in the us-central1 region,
belonging to an organization with ID 123, with workload ID 456 and an etag
of 789, run:

    $ gcloud assured workloads delete \
        organizations/123/locations/us-central1/workloads/456 --etag=789
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/assured/workloads/delete)

---
### `gcloud assured workloads describe`

Describe Assured Workloads environment

Obtain details about a given Assured Workloads environment.

**Synopsis:**
```
gcloud assured workloads describe
    (WORKLOAD : --location=LOCATION --organization=ORGANIZATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload resource - The Assured Workloads environment resource to
describe. The arguments in this group can be used to specify the
attributes of this resource.

This must be specified.

  WORKLOAD
     ID of the workload or fully qualified identifier for the workload.

     To set the workload attribute:
     + provide the argument workload on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the workload.

     To set the location attribute:
     + provide the argument workload on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The parent organization for the workload.

     To set the organization attribute:
     + provide the argument workload on the command line with a fully
       specified name;
     + provide the argument --organization on the command line.
```

**Examples:**
```bash
To describe an Assured Workloads environment in the us-central1 region,
belonging to an organization with ID 123, with workload ID 456 and an etag
of 789, run:

    $ gcloud assured workloads describe \
        organizations/123/locations/us-central1/workloads/456
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/assured/workloads/describe)

---
### `gcloud assured workloads enable-resource-monitoring`

Enables Resource Monitoring for an Assured Workloads environment

Enable resource violation monitoring for a workload.

**Synopsis:**
```
gcloud assured workloads enable-resource-monitoring
    (WORKLOAD : --location=LOCATION --organization=ORGANIZATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload resource - The Assured Workloads environment resource to
enable-resource-monitoring. The arguments in this group can be used to
specify the attributes of this resource.

This must be specified.

  WORKLOAD
     ID of the workload or fully qualified identifier for the workload.

     To set the workload attribute:
     + provide the argument workload on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the workload.

     To set the location attribute:
     + provide the argument workload on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The parent organization for the workload.

     To set the organization attribute:
     + provide the argument workload on the command line with a fully
       specified name;
     + provide the argument --organization on the command line.
```

**Examples:**
```bash
To enable resource violation monitoring for a workload in the us-central1
region, belonging to an organization with ID 123, with workload ID 456,
run:

    $ gcloud assured workloads enable-resource-monitoring \
        organizations/123/locations/us-central1/workloads/456
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/assured/workloads/enable-resource-monitoring)

---
### `gcloud assured workloads list`

List all Assured Workloads environments that belong to a given parent organization

List all Assured Workloads environments that belong to a given parent
organization.

**Synopsis:**
```
gcloud assured workloads list --location=LOCATION
    --organization=ORGANIZATION [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | The location of the Assured Workloads environments. For a current list of supported LOCATION values, see Assured Workloads locations (https://cloud.google.com/assured-workloads/docs/locations). |
| `--organization` | ORGANIZATION |  | The parent organization of the Assured Workloads environments, provided as an organization ID. |


**Examples:**
```bash
The following example command lists all Assured Workloads environments with
these properties:

  o belonging to an organization with ID 123
  o located in the us-central1 region
  o returning no more than 30 results
  o requesting 10 results at a time from the backend

    $ gcloud assured workloads list --organization=123 \
        --location=us-central1 --limit=30 --page-size=10
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/assured/workloads/list)

---
### `gcloud assured workloads update`

Update Assured Workloads environments

Update a given Assured Workloads environment.

**Synopsis:**
```
gcloud assured workloads update
    (WORKLOAD : --location=LOCATION --organization=ORGANIZATION)
    (--display-name=DISPLAY_NAME --labels=[KEY=VALUE,...]
      --violation-notifications-enabled=VIOLATION_NOTIFICATIONS_ENABLED)
    [--etag=ETAG] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload resource - The Assured Workloads environment resource to update.
The arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  WORKLOAD
     ID of the workload or fully qualified identifier for the workload.

     To set the workload attribute:
     + provide the argument workload on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the workload.

     To set the location attribute:
     + provide the argument workload on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The parent organization for the workload.

     To set the organization attribute:
     + provide the argument workload on the command line with a fully
       specified name;
     + provide the argument --organization on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | _[At least one of these must be specified:]_ The new display name of the Assured Workloads environment. |
| `--labels` | [KEY=VALUE,...] |  | _[At least one of these must be specified:]_ The new labels of the Assured Workloads environment, for example, LabelKey1=LabelValue1,LabelKey2=LabelValue2 |
| `--violation-notifications-enabled` | VIOLATION_NOTIFICATIONS_ENABLED |  | _[At least one of these must be specified:]_ The notification setting of the Assured Workloads environment. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--etag` | ETAG |  | The etag acquired by reading the Assured Workloads environment before updating. |


**Examples:**
```bash
To update a given Assured Workloads environment in the us-central1 region,
belonging to an organization with ID 123, with workload ID 456 and an etag
of 789 with a new display name of 'Test-Workload-2' and a new set of labels
(including any required existing labels) of (key = 'ExistingLabelKey1',
value = 'ExistingLabelValue1') and (key = 'NewLabelKey2', value =
'NewLabelValue2'), run:

    $ gcloud assured workloads update \
        organizations/123/locations/us-central1/workloads/456 \
        --display-name=Test-Workload-2 \
        --labels=ExistingLabelKey1=ExistingLabelValue1,\
    NewLabelKey2=NewLabelValue2 --etag=789
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/assured/workloads/update)

---

## `gcloud assured workloads violations` — read and list Assured Workloads Violations
### `gcloud assured workloads violations acknowledge`

Acknowledge an existing Assured Workloads compliance violation

Acknowledge an existing Assured Workloads compliance violation.

**Synopsis:**
```
gcloud assured workloads violations acknowledge
    (VIOLATION : --location=LOCATION
      --organization=ORGANIZATION --workload=WORKLOAD) --comment=COMMENT
    [--acknowledge-type=ACKNOWLEDGE_TYPE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Violation resource - The Assured Workloads violation resource to
acknowledge. The arguments in this group can be used to specify the
attributes of this resource.

This must be specified.

  VIOLATION
     ID of the violation or fully qualified identifier for the violation.

     To set the violation attribute:
     + provide the argument violation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the violation.

     To set the location attribute:
     + provide the argument violation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The parent organization for the violation.

     To set the organization attribute:
     + provide the argument violation on the command line with a fully
       specified name;
     + provide the argument --organization on the command line.

  --workload=WORKLOAD
     The workload for the violation.

     To set the workload attribute:
     + provide the argument violation on the command line with a fully
       specified name;
     + provide the argument --workload on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--comment` | COMMENT |  | Business justification used added to acknowledge a violation. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--acknowledge-type` | ACKNOWLEDGE_TYPE |  | the acknowledge type for specified violation, which is one of: SINGLE_VIOLATION - to acknowledge specified violation, EXISTING_CHILD_RESOURCE_VIOLATIONS - to acknowledge specified org policy violation and all associated child resource violations. |


**Examples:**
```bash
To acknowledge an Assured Workloads Violation in the us-central1 region,
belonging to an organization with ID 123, with workload ID 456, with
violation ID 789 and comment as test ack, run:

    $ gcloud assured workloads violations acknowledge \
         organizations/123/locations/us-central1/workloads/456/\
     violations/789 --comment="test ack"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/assured/workloads/violations/acknowledge)

---
### `gcloud assured workloads violations describe`

Describe an Assured Workloads compliance violation

Obtain details about a given compliance violation.

**Synopsis:**
```
gcloud assured workloads violations describe
    (VIOLATION : --location=LOCATION
      --organization=ORGANIZATION --workload=WORKLOAD)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Violation resource - The Assured Workloads violation resource to describe.
The arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  VIOLATION
     ID of the violation or fully qualified identifier for the violation.

     To set the violation attribute:
     + provide the argument violation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the violation.

     To set the location attribute:
     + provide the argument violation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The parent organization for the violation.

     To set the organization attribute:
     + provide the argument violation on the command line with a fully
       specified name;
     + provide the argument --organization on the command line.

  --workload=WORKLOAD
     The workload for the violation.

     To set the workload attribute:
     + provide the argument violation on the command line with a fully
       specified name;
     + provide the argument --workload on the command line.
```

**Examples:**
```bash
To describe an Assured Workloads Violation in the us-central1 region,
belonging to an organization with ID 123, with workload ID 456, with
violation ID 789, run:

    $ gcloud assured workloads violations describe \
        organizations/123/locations/us-central1/workloads/456/\
    violations/789
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/assured/workloads/violations/describe)

---
### `gcloud assured workloads violations list`

List all Assured Workloads violations that belong to a assured workloads environment

List all Violations that belong to the given Assured Workloads environment.

**Synopsis:**
```
gcloud assured workloads violations list --location=LOCATION
    --organization=ORGANIZATION --workload=WORKLOAD [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | The location of the Assured Workloads environments. For a current list of supported LOCATION values, see Assured Workloads locations (https://cloud.google.com/assured-workloads/docs/locations). |
| `--organization` | ORGANIZATION |  | The parent organization of the Assured Workloads environments, provided as an organization ID. |
| `--workload` | WORKLOAD |  | The parent workload of the Assured Workloads violations, provided as workload ID. |


**Examples:**
```bash
The following example command lists all violations with these properties:

  o belonging to an organization with ID 123
  o belonging to the assured workload with ID w123
  o located in the us-central1 region
  o returning no more than 30 results
  o requesting 10 results at a time from the backend

    $ gcloud assured workloads violations list --organization=123 \
        --location=us-central1 --workload=w123 --limit=30 --page-size=10
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/assured/workloads/violations/list)

---
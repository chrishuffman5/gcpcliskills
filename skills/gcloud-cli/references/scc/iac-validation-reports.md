# gcloud scc iac-validation-reports

manage Cloud SCC (Security Command Center) iac-validation-reports

### `gcloud scc iac-validation-reports create`

Create a Cloud Security Command Center IaC Validation Report

Create a Cloud Security Command Center (SCC) IaC Validation Report. First
argument is the parent of the IaC defined in the plan file. It is followed
by path of the terraform plan file in JSON format.

LRO operation ID is returned as the response of the command.

**Synopsis:**
```
gcloud scc iac-validation-reports create PARENT --tf-plan-file=PATH_TO_FILE
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PARENT
   Name of the organization where IaC Validation Report is to be created.
   Format: organizations/<organizationID>/locations/<location>
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--tf-plan-file` | PATH_TO_FILE |  | Path to a JSON file containing the IaC plan to be validated. Use a full or relative path to a local file containing the value of tf_plan_file. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
Create an Iac Validation report on parent
organizations/123/locations/global:

    $ gcloud scc iac-validation-reports create \
       organizations/123/locations/global --tf-plan-file=planFile.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/iac-validation-reports/create)

---
### `gcloud scc iac-validation-reports describe`

Describe a Cloud Security Command Center IaC Validation Report

Describe a Cloud Security Command Center (SCC) IaC Validation Report. Takes
the name of the report as an argument.

Returns IAC Validation Report as response.

**Synopsis:**
```
gcloud scc iac-validation-reports describe
    (REPORT : --location=LOCATION --organization=ORGANIZATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Report resource - IAC Validation report to be described. For example
organizations/123/locations/global/reports/abcef-gh. The arguments in this
group can be used to specify the attributes of this resource.

This must be specified.

  REPORT
     ID of the report or fully qualified identifier for the report.

     To set the report attribute:
     + provide the argument report on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     ID of the location where the resource exists (for example, global).

     To set the location attribute:
     + provide the argument report on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     ID of the organization which is the parent of the resource.

     To set the organization attribute:
     + provide the argument report on the command line with a fully
       specified name;
     + provide the argument --organization on the command line.
```

**Examples:**
```bash
Describe an IAC Validation report named
organizations/123/locations/global/reports/abcef-gh :

    $ gcloud scc iac-validation-reports describe \
        organizations/123/locations/global/reports/abcef-gh

    or, run:

    $ gcloud scc iac-validation-reports describe abcef-gh \
        --organization=123 --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/iac-validation-reports/describe)

---
### `gcloud scc iac-validation-reports list`

Lists all the Cloud Security Command Center IaC validation reports for an organization

Lists all the Cloud Security Command Center (SCC) IaC validation reports
for an organization.

**Synopsis:**
```
gcloud scc iac-validation-reports list
    ([PARENT] --location=LOCATION --organization=ORGANIZATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Exactly one of these must be specified:

  [PARENT]
     Parent of the IaC validation reports or fully qualified identifier
     for the IaC validation reports.

  Specify organization and location using flags.

    --location=LOCATION
       When data residency controls are enabled, this attribute specifies
       the location in which the resource is located and applicable.

       This flag argument must be specified if any of the other arguments
       in this group are specified.

    --organization=ORGANIZATION
       The organization ID (e.g., 123) that contains the resource.

       This flag argument must be specified if any of the other arguments
       in this group are specified.
```

**Examples:**
```bash
To list Cloud Security Command Center IaC validation reports for
organization 123 in the global location, run:

    $ gcloud scc iac-validation-reports list \
        organizations/123/locations/global/reports

Or using flags:

    $ gcloud scc iac-validation-reports list --organization=123 \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/iac-validation-reports/list)

---